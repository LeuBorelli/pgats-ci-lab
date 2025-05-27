pipeline {
    agent any // No Jenkins, 'agent any' diz "rode onde puder". Similar ao 'runs-on'.

    tools {
        // !!! IMPORTANTE !!!
        // 'NodeJS_22' é um NOME DE EXEMPLO. Você precisa configurar isso no Jenkins.
        // Vá em 'Gerenciar Jenkins' > 'Global Tool Configuration',
        // ache 'NodeJS', clique 'Add NodeJS', dê o nome 'NodeJS_22' (ou outro)
        // e escolha a versão 22.x para ser instalada automaticamente.
        nodejs 'NodeJS_22' // <- Equivalente ao 'setup-node'
    }

    stages {
        // Etapa 1: Pega o Código
        stage('Checkout') {
            steps {
                echo 'Pegando o código do Git...'
                checkout scm // <- Equivalente ao 'actions/checkout'
            }
        }

        // Etapa 2: Instala o Yarn
        stage('Install Yarn') {
            steps {
                echo 'Instalando Yarn...'
                powershell 'npm install -g yarn' // <- Mesmo comando do 'run:'
            }
        }

        // Etapa 3: Instala Dependências
        stage('Install Dependencies') {
            steps {
                echo 'Instalando dependências...'
                powershell 'yarn install' // <- Mesmo comando 'yarn', mas 'yarn install' é mais explícito
            }
        }

        // Etapa 4: Instala Playwright
        stage('Install Playwright') {
            steps {
                echo 'Instalando Playwright...'
                powershell 'yarn playwright install' // <- Mesmo comando do 'run:'
            }
        }

        // Etapa 5: Roda os Testes
        stage('Run E2E Tests') {
            steps {
                echo 'Executando os testes E2E...'
                powershell 'yarn run e2e' // <- Mesmo comando do 'run:'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finalizado.'
        }
    }
}
