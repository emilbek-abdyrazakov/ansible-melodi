properties([
    parameters([
        string(description: 'Enter IP Address', name: 'IPADDRESS', trim: true)
        ])
    ])

node{
    stage("Pull Repo"){
        git 'https://github.com/emilbek-abdyrazakov/ansible-melodi.git'
    }
        stage("Install Melodi") {
            sh """
                ansiblePlaybook become: true, credentialsId: 'jenkins-master-ssh-key', disableHostKeyChecking: true, inventory: '"${params.IPADDRESS},"', playbook: 'main.yml'
            """
        }   
}
