#!/usr/bin/env groovy

// Continuous Integration script to build Jupyter-Book
// Author: mauricio.diaz@inria.fr

pipeline {
  agent none
    stages {
      stage('Clone Conda env') {
        agent { label 'linux && cpu' }
        environment {
           PATH = "$HOME/miniconda/bin:$PATH"
           }
        //when { changeset "requirements.txt" }   
        steps {
          echo 'Install clinicadl in a clean environment...'
          echo 'My branch name is ${BRANCH_NAME}'
          sh 'echo "My branch name is ${BRANCH_NAME}"'
          sh 'echo "Agent name: ${NODE_NAME}"'
          sh '''#!/usr/bin/env bash
             set +x
             eval "$(conda shell.bash hook)"
             conda create -y -n clinicadl_course python=3.7
             conda activate clinicadl_course
             pip install clinicadl==0.1.2
             conda install jupyter
             pip install sphinx nbsphinx sphinx-click sphinx_tabs  myst-parser==0.9.1 jupytext[myst]
             pip install jupyter-book==0.7.1
             conda deactivate
             '''
        }
      }
      stage('Build') {
        checkout([
            $class: 'GitSCM',
            branches: scm.branches,
            doGenerateSubmoduleConfigurations: true,
            extensions: scm.extensions + [[$class: 'SubmoduleOption', parentCredentials: true]],
            userRemoteConfigs: scm.userRemoteConfigs
        ])
        agent { label 'linux && cpu' }
        environment {
          PATH = "$HOME/miniconda/bin:$PATH"
          GIT_SSH_COMMAND = 'ssh -i /builds/.ssh/github_idrsa'
          }
        steps {
          echo 'Building Jupyter-book...'
          sh 'echo "Agent name: ${NODE_NAME}"'
          sh '''#!/usr/bin/env bash
             set +x
             git submodule update --init --recursive
             git pull --recurse-submodules
             eval "$(conda shell.bash hook)" 
             conda activate clinicadl_course
             jupyter-book build .
             cp -r Notebooks-AD-DL/images _build/html/Notebooks-AD-DL/
             cd _build/html/Notebooks-AD-DL
             sed -i 's+github/aramis-lab/MICCAI-educational-challenge-2020/blob/master/Notebooks-AD-DL+github/aramis-lab/Notebooks-AD-DL/blob/master+g' *.html
             conda deactivate
             '''
          stash(name: 'doc_html', includes: '_build/html/**')
        }
      }
      stage('Deploy') {
        agent { label 'linux && cpu' }
        environment {
          PATH = "$HOME/miniconda/bin:$PATH"
          }
        steps {
          echo 'Deploying in webserver...'
          sh 'echo "Agent name: ${NODE_NAME}"'
          unstash(name: 'doc_html')
          sh '''#!/usr/bin/env bash
             set +x
             ls ./
             scp -r _build/html aramislab.paris.inria.fr:~/jupyterbook/ 
             '''
          echo 'Finish uploading artifacts'   
        }
      }
    }
    post {
      success {
        mattermostSend(
          color: "##A837C4",
          message: "The tutorial has been updated, <https://aramislab.paris.inria.fr/clinicadl/tuto/intro.html|see here>"
        )
      }
      failure {
        mail to: 'clinicadl-ci@inria.fr',
          subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
          body: "Something is wrong with ${env.BUILD_URL}"
      }
    }
  }
