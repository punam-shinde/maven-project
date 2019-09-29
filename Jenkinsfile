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
	}
}
