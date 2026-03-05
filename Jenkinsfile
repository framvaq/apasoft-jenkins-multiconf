pipeline {
  agent none
  stages {
    stage('Run everywhere') {
      steps {
        echo "This always runs"
      }
    }

    stage('Run on Multiple Configurations') {
      matrix {
        axes {
          axis {
            name 'OS'
            values 'linux', 'windows'
          }

          axis {
            name 'BROWSER'
            values 'chrome', 'edge', 'firefox'
          }
        }

        agent {
          label "${OS}"
        }
  
        stages {
          stage('Prepare') {
            steps {
              echo "Preparing browser ${BROWSER} on ${OS}"
            }
          }
  
          stage('Run') {
            steps {
              echo "Running ${BROWSER} on ${OS}"
            }
          }
        } // stages
      } // matrix
    } // stage
  } // stages
}
