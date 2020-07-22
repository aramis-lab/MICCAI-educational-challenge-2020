#!/usr/bin/env groovy

// Continuous Integration script to build Jupyter-Book
// Author: mauricio.diaz@inria.fr

pipeline {
  agent none
    stages {
      stage('Install') {
        parallel {
          stage('Clone Conda env') {
            agent { label 'linux' }
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
                 source $WORKSPACE/../../miniconda/etc/profile.d/conda.sh
                 conda create -y -n clinicadl_course python=3.7
                 conda activate clinicadl_course
                 pip install clinicadl==0.0.2b4
                 conda install jupyter
                 pip install -U jupyter-book==0.7.0b2
                 conda deactivate
                 '''
            }
          }
        }
      }
      stage('Build') {
        parallel {
          stage('CLI test Linux') {
            agent { label 'linux' }
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
                 source $WORKSPACE/../../miniconda/etc/profile.d/conda.sh
                 conda activate clinicadl_course
                 jupyter-book build .
                 cp -r Notebooks-AD-DL/images _build/html/Notebooks-AD-DL/
                 conda deactivate
                 '''
              stash(name: 'doc_html', includes: '_build/html/**')
            }
          }
        }
      }
      stage('Deploy') {
        parallel {
          stage('Deploy in webserver') {
            agent { label 'linux' }
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
      }
    }
    post {
      failure {
        mail to: 'clinicadl-ci@inria.fr',
          subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
          body: "Something is wrong with ${env.BUILD_URL}"
      }
    }
  }
