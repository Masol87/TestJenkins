node {
    stage 'Get git repository from github'
        sh 'cd /var/lib/jenkins/workspace/test_3/'
        sh 'rm -Rf TestJenkins MyWebApp.war'
        sh 'git clone https://github.com/Masol87/TestJenkins.git'
        
    stage 'Create WAR file for the Progect'
        sh 'cd /var/lib/jenkins/workspace/test_3/TestJenkins/src/main/webapp'
        sh 'jar -cvf MyWebApp.war *'

    stage 'Deploy war to TomCat'
        sh 'sudo -s scp -rv MyWebApp.war root@10.30.1.151:/opt/tomcat/webapps/ | echo "8tme6gf5PKV"'
    
    stage 'Restart TomCat service'
        sh 'sudo ssh root@10.30.1.151 service tomcat restart | echo "8tme6gf5PKV"'
    
}
