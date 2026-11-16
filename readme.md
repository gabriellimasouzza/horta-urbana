# 🌱 Horta Urbana

> **⚠️ AVISO IMPORTANTE SOBRE USO E PRIVACIDADE DE DADOS**
> Este é um **aplicativo pessoal**, feito originalmente para uso do próprio criador. Por isso, se você abrir a versão hospedada/pública:
> * **Seus dados não vão para a nuvem do criador.** O Firebase configurado no código pertence só à conta do autor, e o login do Google dele é o único que grava lá. O que você cadastrar (locais, plantios, registros de adubo) fica **apenas no navegador** do aparelho que você usa (via `localStorage`) e pode ser perdido se você limpar os dados do navegador. Use **Baixar arquivo de backup** (aba Guia) de vez em quando.
> * **Use o código como quiser.** O projeto é público para que qualquer pessoa possa clonar, fazer um *fork*, modificar e hospedar a própria versão, ligando o próprio Firebase ou um repositório privado do GitHub para guardar os dados.

---

## 📖 Sobre o projeto

O **Horta Urbana** é um aplicativo web leve, responsivo e de arquivo único (`index.html`) para planejar e acompanhar hortas domésticas em **canteiros, vasos ou torres verticais de PVC**, em qualquer cidade do Brasil.

Ele cruza a previsão do tempo, o histórico de clima de 10 anos da cidade escolhida e recomendações técnicas de cultivo (principalmente da **Embrapa**, além de IAPAR, MAPA, FAO, NOAA e Simepar) para dizer o que plantar, quando adiar e como cuidar. Todos os textos e cálculos usam a cidade escolhida, não uma cidade fixa.

---

## ✨ Funcionalidades

### 1. 📅 Aba "Hoje"
* **Previsão do tempo ao vivo** (Open-Meteo): temperatura atual, máxima e mínima, chuva e probabilidade, umidade e vento, com busca por qualquer cidade do Brasil (cidade inicial: Porto Barreiro, PR). Sem internet, o app mostra a última previsão salva no mesmo dia, com a idade dela.
* **Calendário de plantio de 14 dias**, com a lua de cada dia e o que fazer em cada um:
  * **Escolha do local:** a lista pode ser filtrada por um local cadastrado. O app mostra "Não cabe" e o motivo (profundidade, torre de PVC, planta grande, poucas horas de sol).
  * **Plantar ou adiar:** adia o plantio de plantas sensíveis se a mínima prevista nos próximos 3 dias for de 3 °C ou menos, e adia qualquer plantio com chuva de 30 mm ou mais ou máxima de 35 °C ou mais.
  * **Adubar ou esperar:** adia o adubo se a chuva prevista passar de 20 mm em 3 dias (ou 10 mm em um dia), porque o adubo seria lavado, e se houver geada. Depois de registrar um adubo ("Adubei hoje"), espera cerca de 15 dias.
  * **Regar:** estima a água que o sol e o vento devem secar (evapotranspiração) e avisa quando a chuva já rega.
  * **Plantas já plantadas** aparecem como "Plantado" e saem da lista de sugestões.
  * **Ervas e chás de vários anos** (melissa, poejo, lúcia-lima, lavanda, boldo, hortelã, hortelã-pimenta, camomila e louro) entram no calendário pela época indicada pela Embrapa.
* **Fenômeno do Pacífico agora (El Niño, La Niña ou neutro):** o app consulta o índice ONI do NOAA e mostra a fase atual e o que ela costuma causar na **região da cidade escolhida**, com dicas para a horta. Se a consulta for bloqueada pelo navegador, usa o último valor guardado (com aviso de idade) e você pode escolher a fase à mão.
* **Situações pela previsão da cidade:** seca de curto prazo, terra encharcada, onda de calor, risco de geada e chuva forte.
* **Lua do dia** e das próximas fases (com a orientação do Hemisfério Sul) e, se você ligar, dicas da tradição popular.
* **O que plantar no mês:** lista as espécies em *Boa época*, *No limite*, *Evite agora* e *Sem dado*, mais as de vários anos.

### 2. 🪴 Aba "Locais"
* Cadastro de **canteiro, torre de PVC ou vaso**, com profundidade, horas de sol, período do sol e superfície. Dá para **editar** cada local.
* **Rega estimada** em litros para hoje e amanhã.
* **Terra e adubo do local:** calcula o volume de terra e a mistura (terra, esterco, calcário dolomítico e NPK 4-14-8) pela receita da Embrapa para recipientes, mais doses de reforço reduzidas para a área do local.
* **Avisos de adequação** (profundidade, sol).

### 3. 🌱 Aba "Plantios"
* Registro do plantio com **espécie, local, data, anotação e forma de plantio**. A forma depende da planta (semente, muda, planta formada, estaca, divisão de touceira, bulbilho, rizoma, rama ou maniva).
* **Prazo de colheita por forma de plantio**, somando o berçário só quando há dado confiável. Quando não achei o prazo, o app diz "sem prazo confiável".
* **Marcar como colhido, morreu ou removido**, com histórico e opção de reativar. Também dá para editar e anotar cada plantio.
* **Rodízio:** avisa quando o local já teve a mesma família botânica (ex.: solanáceas) nos últimos 12 meses.
* **Avisos:** espécie que não serve para torre, vaso raso demais e plantas que não toleram transplante.
* **Histórico de adubo** com os últimos registros.

### 4. 🌿 Aba "Espécies"
* **58 espécies** em 5 grupos: *Folhas; Temperos e ervas aromáticas; Plantas para chás; Legumes e hortaliças de frutos; Raízes, tubérculos e bulbos*.
* Cada uma tem ícone SVG, ciclo, tamanho de vaso, compatibilidade com torre, tolerância à geada e dicas em linguagem simples.

### 5. 🌤️ Aba "Clima"
* Histórico dos **últimos 10 anos** da cidade (Open-Meteo Archive): dias de geada por ano, meses sem geada, temperaturas e chuva por mês.
* **Calendário anual de plantio** calculado para a cidade, cruzando o clima com a faixa de temperatura de cada planta.

### 6. 🐛 Aba "Problemas"
* 18 fichas de **pragas, doenças e falta de nutrientes**, com sinais e o que fazer (soluções naturais da Embrapa). Procura fotos na pasta `imagens/` (`pulgao.jpg`, `lagarta.jpg`, `mosca_branca.jpg`, `cochonilha.jpg`, `acaro.jpg`, `tripes.jpg`, `lesma.jpg`, `vaquinha.jpg`, `nematoide.jpg`, `oidio.jpg`, `ferrugem.jpg`, `manchas.jpg`, `podridao.jpg`, `virus.jpg`, `def_n.jpg`, `def_p.jpg`, `def_k.jpg`, `def_ca.jpg`). Sem a foto, mostra "foto em breve".

### 7. 📚 Aba "Guia" e dados
* Guia rápido sobre luz, rega, terra, acidez, adubo, mudas, poda, pragas, consórcio, rodízio, colheita, torre, vasos e clima da sua cidade.
* **Salvar na nuvem com login do Google (Firebase).** Veja `LEIA-ME-FIREBASE.md`.
* **Alternativa:** salvar em um repositório privado do GitHub com um *Fine-grained token*.
* **Backup em arquivo:** baixar e enviar um arquivo `.json`, além de copiar e colar o texto.

### 8. 💬 Assistente
* Chat que responde **só por palavras-chave**, com o conteúdo do próprio app (não é uma IA). Cruza perguntas gerais (rega, pragas, geada, clima, El Niño) com a espécie citada e com a sua cidade.

---

## 🛠️ Tecnologias

* **HTML, CSS e JavaScript puro**, em um único `index.html`, com tema claro e escuro automático. Os ícones das plantas estão embutidos; a pasta `icones/` guarda as versões em SVG.
* **Open-Meteo:** previsão, busca de cidades e histórico climático (sem chave).
* **NOAA CPC:** índice ONI do El Niño.
* **Firebase (Authentication e Firestore):** sincronização opcional.
* **API do GitHub:** sincronização alternativa.

---

## 🚀 Como usar ou adaptar

1. **Baixe ou clone o repositório:**
   ```bash
   git clone https://github.com/SEU-USUARIO/SEU-REPOSITORIO.git
   ```
2. **Rode localmente:** abra o `index.html` no navegador (ou use o *Live Server* do VS Code).
3. **Para salvar na nuvem (opcional):**
   * **Opção A (sem mexer no código):** na aba **Guia**, em **Alternativa: salvar no GitHub**, crie um repositório privado e use um *Fine-grained token* com permissão de ler e escrever *Contents*.
   * **Opção B (seu próprio Firebase):** crie um projeto gratuito no [Firebase Console](https://console.firebase.google.com/), ligue o *Authentication (Google)* e o *Firestore*, publique as regras do `LEIA-ME-FIREBASE.md` e troque `window.FIREBASE_CONFIG` no `index.html` pelas suas chaves.

---

## ⚠️ Limites conhecidos

* Vários limites do app são **estimativas** e estão marcados na tela: a temperatura de 3 °C como alerta de geada, os 15 dias entre adubos, os 14 dias de colheita leve de uma planta já formada e as faixas de temperatura de parte das espécies.
* Calendário de plantio da Embrapa por região só está embutido para o **Sul** (usado apenas como reserva em cidades do Sul). Nas outras regiões, vale o cálculo pelo clima da cidade.
* A consulta automática do El Niño pode ser bloqueada pelo navegador; nesse caso o app usa o último valor guardado ou a fase que você escolher.
* Não há doses de adubo **por espécie** nem de micronutrientes, porque não achei fonte confiável.
* Não é um aplicativo instalável (PWA) e não envia avisos ao celular.

---

## 📚 Fontes de referência

Publicações da **Embrapa** (*Documentos 161* e *157*, *Catálogo Brasileiro de Hortaliças*, *Horta em Pequenos Espaços*, *Produção de mudas de hortícolas*), **IAPAR**, **MAPA**, **FAO**, **INMET**, **CPTEC/INPE**, **NOAA** e **Simepar**. Os dados de tempo vêm do **Open-Meteo**.
