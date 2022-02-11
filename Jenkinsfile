  node{
      stage('Clone') {
          checkout scm
      }
      stage('Génération de la clé ssh et copie vers la machine cible'){
          'apk add ansible  sshpass'

          'rm -rf /root/.ssh'

          'ssh-keygen -q -t rsa -N '' -f /root/.ssh/id_rsa'

          'sshpass -p 'root' ssh-copy-id -o stricthostkeychecking=no root@app-salaire.issaga.form'

      }
      stage('Ansible') {
        ansiblePlaybook (
            colorized: true,          
            playbook: 'playbook.yml',
            inventory: 'hosts.yml'
        )
      }
  }
