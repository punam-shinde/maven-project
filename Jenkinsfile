pipeline
{

agent any{
		stage "scm checkout"
		{
			git 'https://github.com/punam-shinde/maven-project.git'
		}

	
		stage "code test"{
			
			steps {
				withMaven(maven: '/usr/share/apache-maven') 
				{
					sh 'mvn test'
				}
				}
		}
	}
}
