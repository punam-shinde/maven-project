pipeline
{

agent any
	stages
	{
		stage ('scm checkout')
		{
			steps{
			git 'https://github.com/punam-shinde/maven-project.git'}
		}



		stage ('code test')
		{
			
			steps {
				withMaven(maven: '/usr/share/apache-maven') 
					{
						sh 'mvn test'
					}
				}
		}
		
		stage ('Package')
		{
			
			steps {
				withMaven(maven: '/usr/share/apache-maven') 
					{
						sh 'mvn package'
					}
				}
		}
		
		stage ('Install')
		{
			
			steps {
				withMaven(maven: '/usr/share/apache-maven') 
					{
						sh 'mvn install'
					}
				}
		}
		
		stage ('deploy to tomcat')
		{
			
			steps {
  				sshagent (credentials: ['172.31.35.229']) {
    				sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.35.229 /var/lib/tomcat/webapps'
  				}
				}
		}
		
	}
}
