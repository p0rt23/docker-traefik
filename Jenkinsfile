node {
    stage('Build') {
        checkout scm
    }

    stage('Deploy') {
        try {
            sh "docker stop traefik"
            sh "docker rm traefik"
        }
        catch (Exception e) { 
            
        }
        
        sh '''
            docker run \
                -d \
                --restart always \
                --name traefik \
                -p 80:80 \
                -p 8080:8080 \
                -v $PWD/traefik.toml:/etc/traefik/traefik.toml \
                -v /var/run/docker.sock:/var/run/docker.sock \
                traefik:latest 
        '''
    }
}
