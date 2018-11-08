node {
    stage 'Get git repository from github'
        sh 'cd /var/lib/jenkins/workspace/test_3/'
        sh 'rm -Rf *'
        sh 'git clone https://github.com/Masol87/TestJenkins.git'
        
    stage 'Create WAR file for the Progect'
        sh 'cd /var/lib/jenkins/workspace/test_3/TestJenkins/src/main/webapp'
        sh 'jar -cvf MyWebApp.war *'
        
    stage 'Clear folders on TomCat server'
        sh 'sudo ssh root@10.30.0.170 rm -Rf /opt/tomcat/webapps/MyWebApp MyWebApp.war | echo "8tme6gf5PKV"'

    stage 'Deploy war to TomCat'
        sh 'cd /var/lib/jenkins/workspace/test_3'
        sh 'sudo -s scp -rv *.war root@10.30.0.170:/opt/tomcat/webapps/ | echo "8tme6gf5PKV"'
    
    stage 'Restart TomCat service'
        sh 'sudo ssh root@10.30.0.170 service tomcat stop | echo "8tme6gf5PKV"'
        sh 'sudo ssh root@10.30.0.170 /opt/tomcat/bin/shutdown.sh | echo "8tme6gf5PKV"'
        sh 'sudo ssh root@10.30.0.170 /opt/tomcat/bin/configtest.sh | echo "8tme6gf5PKV"'
        sh 'sudo ssh root@10.30.0.170 /opt/tomcat/bin/startup.sh | echo "8tme6gf5PKV"'
        sh 'sudo ssh root@10.30.0.170 service tomcat start | echo "8tme6gf5PKV"'
    
}
