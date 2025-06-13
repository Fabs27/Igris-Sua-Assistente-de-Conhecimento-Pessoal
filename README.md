Igris: Sua Assistente de Conhecimento Pessoal
A Igris é uma assistente de conhecimento pessoal, desenvolvida para ser uma ferramenta útil para estudantes, pesquisadores e entusiastas em diversas áreas do saber. Ela pode pesquisar em sua base de dados interna, buscar informações na web, ajudar no download de arquivos e até mesmo aprender novos conhecimentos com sua permissão. A Igris interage via uma interface gráfica intuitiva e comandos de voz, respondendo ao seu nome para ativar a escuta.
Índice
 * Visão Geral
 * Funcionalidades
 * Como Usar
 * Instalação e Configuração Inicial
 * Estrutura do Código em Blocos
 * Copyright e Licença
 * Contato
Visão Geral
A Igris é projetada para ser um repositório de conhecimento dinâmico. Ela utiliza um banco de dados SQLite para armazenar informações categorizadas e tem a capacidade de expandir seu próprio conhecimento buscando na internet e solicitando sua aprovação para integrar novos dados. A interação pode ser totalmente por voz, com a Igris esperando ser chamada ("Igris") antes de processar um comando, ou por texto, através da interface gráfica.
Funcionalidades
 * Busca de Conhecimento Interno: Pesquisa em uma base de dados organizada por categorias, áreas e tópicos.
 * Reconhecimento e Síntese de Voz: Interação por voz para comandos e respostas.
 * Ativação por Voz: A Igris só responde quando ouve a palavra "Igris", mesmo no meio de uma frase.
 * Relógio Offline: Mantém e informa a hora, mesmo sem conexão constante com a internet, sincronizando quando possível.
 * Pesquisa Web: Abre o navegador para pesquisar termos na internet.
 * Download de Arquivos: Baixa arquivos de URLs fornecidas.
 * Modo Administrador: Permite ações sensíveis, como o aprendizado de novos conhecimentos, mediante senha.
 * Aprendizado Adaptativo: A Igris pode sugerir adicionar novos conhecimentos encontrados na web à sua base de dados, com sua permissão.
 * Configurações Personalizáveis: Nome do usuário, idioma da Igris e voz podem ser configurados e salvos.
Como Usar
Interação por Voz (Recomendado)
 * Chame a Igris: A Igris estará sempre "ouvindo" pela palavra "Igris". Diga algo como: "Olá Igris, pode me ajudar?" ou "Que horas são, Igris?".
 * Dê seu Comando: Após ouvir "Igris", ela responderá "Sim?" e você poderá dizer seu comando.
 * Comandos de Voz:
   * "Igris, pesquisar web [termo]": Abre uma pesquisa no Google.
   * "Igris, que horas são?": Informa a hora atual.
   * "Igris, listar categorias": Mostra as categorias de conhecimento.
   * "Igris, ver [tópico]": Exibe o conteúdo de um tópico específico.
   * "Igris, baixar [URL]": Baixa um arquivo da internet.
   * "Igris, sair": Fecha a aplicação.
Interação por Texto (GUI)
 * Digite seu Comando: Use a caixa de texto na parte inferior da janela da Igris.
 * Pressione Enter ou Clique em "Enviar": O comando será processado.
 * Comandos de Texto:
   * sair: Fecha a aplicação.
   * admin: Ativa o modo administrador (requer senha).
   * voz [on/off]: Liga ou desliga a voz da Igris.
   * idioma [código]: Altera o idioma da Igris (ex: idioma en-US).
   * listar categorias: Mostra todas as categorias de conhecimento.
   * listar areas [categoria]: Lista as áreas dentro de uma categoria.
   * listar topicos [area]: Lista os tópicos dentro de uma área.
   * ver [topico]: Exibe o conteúdo detalhado de um tópico.
   * [palavra_chave]: Realiza uma busca interna por palavras-chave.
   * pesquisar web [termo]: Abre o navegador com uma pesquisa no Google.
   * baixar [URL]: Baixa um arquivo de uma URL.
   * que horas são? ou horas: Informa a hora atual.
   * sincronizar hora: Força a sincronização do relógio com a internet.
   * selecionar voz: Abre a janela para mudar a voz da Igris.
Instalação e Configuração Inicial
 * Clonar o Repositório:
   git clone [URL_DO_SEU_REPOSITORIO]
cd igris-assistant

 * Executar o Script de Inicialização:
   A Igris possui um script de inicialização (start.bat no Windows) que verifica e instala as dependências necessárias automaticamente, incluindo o Python (se não estiver presente) e as bibliotecas Python (pyttsx3, SpeechRecognition, requests, beautifulsoup4, colorama, pyaudio).
   * No Windows:
     É altamente recomendado executar o start.bat como administrador (clique com o botão direito -> "Executar como administrador") para garantir que todas as instalações, especialmente a do Python e PyAudio, ocorram sem problemas de permissão.
   * Em Linux/macOS (Adaptação Manual - Exemplo):
     Você precisará instalar o Python 3 (se não tiver) e as bibliotecas manualmente:
     sudo apt update # Para Debian/Ubuntu
sudo apt install python3 python3-pip # Para Debian/Ubuntu
# Ou brew install python3 para macOS

pip install pyttsx3 SpeechRecognition requests beautifulsoup4 colorama
pip install pyaudio # Pode precisar de dependências de sistema, veja documentação do PyAudio

     Em seguida, execute o script principal Python:
     python main.py

 * Primeiro Uso:
   * Na primeira execução, a Igris guiará você para selecionar sua voz e perguntará como você gostaria de ser chamado.
   * Um banco de dados conhecimento.db será criado na pasta database/ para armazenar o conhecimento da Igris.
Estrutura do Código em Blocos
O projeto Igris é organizado em blocos lógicos para facilitar a compreensão e manutenção.
Bloco 1: Importações e Configurações Iniciais
 * Conteúdo: Importa todas as bibliotecas necessárias (sqlite3, os, subprocess, tkinter, webbrowser, json, re, datetime, requests, beautifulsoup4, colorama, pyttsx3, speech_recognition, pyaudio).
 * Funcionalidade: Define variáveis globais como o nome do banco de dados, caminhos de configuração, senha do administrador, e flags de estado (voz habilitada, modo admin, etc.). Inclui lógica para tentar instalar bibliotecas Python que faltam.
Bloco 2: Funções de Utilitários e Setup
 * Conteúdo: Funções auxiliares como igris_speak (para a Igris falar), print_and_speak (imprime e fala), is_admin (verifica privilégios de administrador), check_and_create_dirs (cria pastas necessárias).
 * Funcionalidade: Lida com a inicialização do ambiente, incluindo a importante função install_python_if_needed, que tenta instalar o Python e suas dependências. Também contém as funções para conectar, criar tabelas e inserir dados iniciais no banco de dados (connect_db, create_tables, insert_initial_data).
Bloco 3: Funções de Configuração e Entrada/Saída de Voz
 * Conteúdo: Funções para gerenciar as configurações do usuário (load_user_config, save_user_config).
 * Funcionalidade: Contém a lógica principal de reconhecimento de voz (listen_for_command) que agora inclui a detecção da palavra de ativação "Igris". Também inclui funções para alternar o modo admin (toggle_admin_mode_gui) e a saída de voz (toggle_voice_output).
Bloco 4: Funções de Pesquisa, Download e Aprendizado
 * Conteúdo: Funções para interagir com a base de conhecimento (search_knowledge, show_all_categories, show_areas_by_category, show_topics_by_area, show_content_by_topic).
 * Funcionalidade: Inclui funcionalidades de rede como search_web (abrir navegador) e download_file_from_url. O destaque é o sistema de aprendizado, com get_web_content (extrai texto de URLs), suggest_category_area_topic (sugere categorização) e confirm_and_add_knowledge (guia o usuário para adicionar novo conhecimento à base).
Bloco 5: Relógio Offline e Funções da GUI
 * Conteúdo: Funções relacionadas ao relógio (get_current_time_online, get_current_time_igris) que permite à Igris informar a hora aproximada mesmo sem conexão constante.
 * Funcionalidade: Inclui as funções de interface gráfica Tkinter (print_to_gui para exibir texto colorido na janela) e a função central de processamento de comandos (process_command_internal), que é chamada tanto pela entrada de texto quanto pela voz.
Bloco 6: Funções da Janela de Seleção de Voz e Saudação
 * Conteúdo: open_voice_selection_window (cria a interface para o usuário escolher a voz da Igris) e greet_user (cumprimenta o usuário com base na hora do dia).
 * Funcionalidade: Gerencia a personalização da voz da Igris e a saudação inicial ao usuário.
Bloco 7: Início da Escuta (Thread) e Função Principal
 * Conteúdo: start_listening_for_activation (roda em um thread separado para ouvir a palavra de ativação Igris continuamente) e run_igris_gui (a função principal que inicializa toda a aplicação, GUI, banco de dados e loops de escuta).
 * Funcionalidade: Orquestra o funcionamento geral da Igris, garantindo que o reconhecimento de voz esteja sempre ativo em segundo plano sem bloquear a interface gráfica.
Copyright e Licença
CÓDIGO ASSINADO POR: @fabs_txt
AUTOR: Fabrício Faustino
CIDADE: Marília, SP, Brasil
DATA DE CRIAÇÃO: 13/06/2025
HORA DE CRIAÇÃO: 03:22 AM -03

COPYRIGHT (C) 2025 Fabrício Faustino. Todos os direitos reservados.
Qualquer cópia, reprodução ou distribuição deste código, no todo ou em parte,
sem a devida atribuição e permissão do autor, é estritamente proibida e ilegal.

Este código é uma propriedade intelectual de Fabrício Faustino.

Este projeto está licenciado sob a Licença MIT. Sinta-se à vontade para inspecionar, aprender e adaptar o código para fins não comerciais, desde que a atribuição original e o aviso de copyright sejam mantidos.
Contato
Para dúvidas, sugestões ou colaborações, entre em contato com:
 * Fabrício Faustino
 * Email: moosebethor@gmail.com
 * Instagram/X/Outro: @fabs_txt
