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
		
		stage ('ssh tomcat')
		{
			
			steps {
				sshPublisher(publishers: [sshPublisherDesc(configName: 'tomcat', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: 'var/lib/tomcat/webapps', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
				}
		}
		
	}
}
