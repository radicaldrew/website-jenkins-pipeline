def remote = [:]
remote.name = 'website'
remote.host = "$params.ip"
remote.allowAnyHosts = true

node {
        withCredentials([sshUserPrivateKey(credentialsId: 'ec2', keyFileVariable: 'identity', passphraseVariable: '', usernameVariable: 'userName')]) {
                remote.user = userName
                remote.identityFile = identity

                stage('Checkout') {
                        git branch: 'main', credentialsId: 'github',   url: "$params.repository"
                }
                stage('Upload') {
                        sshCommand sudo: true, remote: remote, command: 'rm -rf /var/www/html/*'
                        sshPut remote: remote, from: './index.html', into: '/var/www/html/'
                        sshPut remote: remote, from: './css/', into: '/var/www/html'
                        sshPut remote: remote, from: './images/', into: '/var/www/html'
                        sshCommand sudo: true, remote: remote, command: 'chown -R www-data: /var/www/html'
                }
        }
}
