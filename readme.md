# 🌱 Horta Urbana

> **⚠️ AVISO IMPORTANTE SOBRE USO E PRIVACIDADE DE DADOS:**
> Este é um **aplicativo pessoal**, desenvolvido originalmente para o uso próprio do seu criador. Por esse motivo, se você acessar a versão hospedada/pública diretamente:
> * **Seus dados não ficam salvos na nuvem do criador:** O banco de dados na nuvem (Firebase) está vinculado apenas à conta pessoal do autor. As informações que você cadastrar (seus locais, plantios e registros) ficarão salvas **apenas localmente no navegador** do dispositivo que você estiver usando (via `localStorage`) e podem ser perdidas se você limpar os dados do navegador.
> * **Sinta-se livre para usar o código:** O projeto está público justamente para que qualquer pessoa possa utilizá-lo como quiser! Você pode clonar, fazer um *fork*, modificar e hospedar a sua própria versão (conectando seu próprio Firebase ou repositório privado do GitHub para salvar seus dados na nuvem).

---

## 📖 Sobre o Projeto

O **Horta Urbana** é uma aplicação web leve, responsiva e de arquivo único (`index.html`), criada para auxiliar no planejamento, acompanhamento e manejo de hortas domésticas — seja em **canteiros, vasos ou torres verticais de PVC**. 

O sistema cruza dados meteorológicos em tempo real e históricos climáticos de 10 anos da cidade escolhida com recomendações técnicas de cultivo (baseadas principalmente em materiais da **Embrapa**, **IAPAR**, **MAPA** e **FAO**).

---

## ✨ Funcionalidades Principais

### 1. 📅 Aba "Hoje" (Painel Diário e Calendário Inteligente)
* **Previsão do Tempo e Clima Atual:** Integração com a API gratuita **Open-Meteo**, exibindo temperatura atual, máxima/mínima, umidade, vento, volume e probabilidade de chuva, além de busca para qualquer cidade do Brasil (padrão inicial: Porto Barreiro, PR).
* **Calendário Dinâmico de 14 Dias:** Avalia diariamente se é um bom momento para plantar ou adubar com base na previsão dos próximos dias:
  * *Alerta de Geada:* Adia o plantio de espécies sensíveis e a adubação se houver previsão de mínima $\le 3\text{ }^\circ\text{C}$ nos próximos 3 dias.
  * *Alerta de Chuva Forte e Calor Extremo:* Recomenda adiar plantios em dias com chuva $\ge 30\text{ mm}$ ou temperatura $\ge 35\text{ }^\circ\text{C}$, e evita adubação antes de chuvas fortes ($\ge 10\text{ mm}$ no dia ou $\ge 20\text{ mm}$ em 3 dias) para não lavar os nutrientes.
  * *Controle de Rega e Adubação:* Calcula a evapotranspiração ($ET_0$) para sugerir regas e permite registrar a data e o tipo de adubação (*composto, húmus, NPK*) com intervalo automático de 15 dias.
* **Fases da Lua e Monitoramento El Niño:** Exibe a fase lunar atual (com opção de ativar/desativar dicas da tradição popular) e boletins sobre fenômenos climáticos (El Niño / La Niña) e seus impactos na horta.
* **O que plantar no mês:** Classifica automaticamente mais de 55 espécies entre *Boa época*, *No limite*, *Evite agora*, *Sem dado* e *Perenes (o ano todo)*.

### 2. 🪴 Aba "Locais"
* Cadastro personalizado dos espaços de cultivo (**Canteiro**, **Torre de PVC** ou **Vaso**), informando profundidade (cm), horas de sol, período de incidência solar (manhã, tarde, dia todo) e área ($m^2$).
* **Cálculo de Rega Estimada:** Calcula automaticamente quantos litros de água cada local precisa hoje e amanhã com base na evapotranspiração da cidade, no tamanho do recipiente e na exposição ao sol.
* **Alertas de Adequação:** Avisa sobre limitações de profundidade (ex.: locais com menos de 30 cm para raízes e frutos), excesso de sol da tarde ou falta de luminosidade.

### 3. 🌱 Aba "Plantios"
* Registro detalhado do que foi plantado, vinculando a espécie ao local cadastrado e à **forma de plantio** (*semente, muda, planta formada, estaca, touceira, bulbilho, rizoma, rama ou maniva*).
* **Contagem Regressiva para Colheita:** Ajusta o prazo estimado até a primeira colheita de acordo com o método escolhido (ex.: somando dias de berçário quando plantado por semente).
* **Validações Automáticas:** Alerta caso a espécie seja incompatível com torre de PVC, se o vaso for raso demais ou se a planta não tolerar transplante.
* **Histórico de Adubação:** Lista os últimos registros de adubos aplicados.

### 4. 🌿 Aba "Espécies"
* Catálogo completo com **mais de 55 espécies** organizadas por categorias (*Folhas, Temperos e ervas aromáticas, Plantas para chás, Legumes e hortaliças de frutos, Raízes, tubérculos e bulbos*).
* Inclui ícones vetoriais exclusivos em SVG para cada planta, ciclo em dias, profundidade ideal de vaso, compatibilidade com torre de PVC, resistência à geada e dicas práticas de cultivo.

### 5. 🌤️ Aba "Clima"
* Busca o histórico climático dos **últimos 10 anos** (2015–2024) da cidade selecionada via Open-Meteo Archive.
* Calcula a média anual de dias com risco de geada, meses livres de geada, médias térmicas/pluviométricas mensais e gera uma **matriz anual de plantio** personalizada para a região.

### 6. 🐛 Aba "Problemas"
* Guia visual de diagnóstico dividido em **Pragas**, **Doenças** e **Falta de nutrientes** (Nitrogênio, Fósforo, Potássio e Cálcio).
* Apresenta os sintomas e soluções naturais/orgânicas (calda de sabão neutro, óleo de neem, leite cru, manejo cultural).

### 7. 📚 Aba "Guia" e Configurações
* Enciclopédia rápida sobre luz, rega, preparo de substrato, pH, podas, consórcio, rotação de culturas e conservação pós-colheita.
* **Exportação e Importação:** Permite copiar e colar os dados em formato JSON para backup manual.
* **Sincronização Alternativa via GitHub:** Conta com suporte nativo para salvar os dados em um arquivo `dados.json` dentro de um repositório privado do próprio usuário usando um *Fine-grained Personal Access Token*.

### 8. 💬 Assistente Virtual Integrado
* Chat flutuante que funciona 100% offline/localmente por busca de palavras-chave, cruzando dúvidas gerais (rega, pragas, geada, substrato) com as características específicas de cada espécie cadastrada no aplicativo.

---

## 🛠️ Tecnologias Utilizadas

* **HTML5, CSS3 e JavaScript (Vanilla ES6+):** Toda a interface, lógica, estilização (com suporte automático a tema claro e escuro) e ícones SVG estão contidos em um único arquivo `index.html`, sem necessidade de *build* ou dependências externas pesadas.
* **Open-Meteo API:** Previsão do tempo, geocodificação de cidades e histórico climático (sem necessidade de chave de API).
* **Firebase (Authentication & Firestore):** Estrutura pronta para sincronização em nuvem (configurada para o criador, mas facilmente substituível).
* **GitHub REST API:** Opção alternativa integrada para persistência de dados em repositório privado.

---

## 🚀 Como Usar ou Adaptar o Projeto

Como este projeto não depende de servidores complexos ou ferramentas de compilação, rodá-lo é muito simples:

1. **Baixe ou clone este repositório:**
   ```bash
   git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
   ```
2. **Execute localmente:**
   Basta abrir o arquivo `index.html` diretamente no seu navegador (ou usar uma extensão como o *Live Server* no VS Code).
3. **Para salvar seus dados na nuvem (Opcional):**
   * **Opção A (Sem alterar código):** Abra o app no navegador, vá até a aba **Guia**, role até **"Alternativa: salvar no GitHub"**, crie um repositório privado na sua conta e insira um *Fine-grained Token* com permissão de leitura e escrita em *Contents*.
   * **Opção B (Seu próprio Firebase):** Crie um projeto gratuito no [Firebase Console](https://console.firebase.google.com/), ative o *Authentication (Google)* e o *Firestore Database*, e substitua o objeto `window.FIREBASE_CONFIG` no código do `index.html` pelas suas próprias chaves.

---

## 📚 Fontes de Referência Agronômica

As informações técnicas de cultivo presentes neste aplicativo foram compiladas a partir de publicações da **Embrapa** (*Documentos 161*, *Catálogo de Hortaliças*, *Horta em Pequenos Espaços*), **IAPAR**, **MAPA**, **FAO** e boletins meteorológicos do **NOAA** e **Simepar**.