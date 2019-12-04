pipeline {
	agent any
	parameters {
	    choice(name: 'BUILD_ENV', choices: ['dev', 'pre', 'prod'], description: '构建环境')
        text(name: 'BUILD_SUBMIT', defaultValue: '', description: '修改信息')
        text(name: 'NOTICE', defaultValue: '', description: '注意事项')
        text(name: 'PROBLEMS', defaultValue: '', description: '已知问题')
        text(name: 'CONFIG', defaultValue: '', description: '配置文件')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    }
	environment {
                DEBUG_FLAGS = '-g'
                CC = """${sh(
                returnStdout: true,
                script: 'echo "clang"'
            )}"""
    }
	stages{
		stage ('编译'){
		    
			steps{
			    dir('/home/xxqin/project/git/kxjl-build-v2/'){
			        sh 'python -u build_images_ms.py'
			    }
				
				echo env.DEBUG_FLAGS
			} 
		}
		stage ('测试'){
			steps{
				sh '''echo Deploy'''
			} 
		}
		stage ('部署'){
			steps{
				echo env.CC
			}
		}
	}
}