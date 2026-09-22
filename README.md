# Conferidor de escrita manual de ideias

Aplicativo web para acompanhar, durante a escrita, quanto cada ideia planejada aparece no texto do estudante.

**Acesse:** [conferidor-de-ideias.vercel.app](https://conferidor-de-ideias.vercel.app/)

## Como usar

1. Em **Suas ideias**, escreva uma ideia por linha. Cada quebra de linha cria uma nova ideia.
2. Em **Seu texto**, desenvolva as ideias com suas próprias palavras.
3. Acompanhe **Ideias no texto**. Cada cartão mostra o número da ideia e uma estimativa percentual de quanto ela foi contemplada.

A análise começa após duas palavras completas e é atualizada a cada duas novas palavras completas. O botão **Inserir texto de exemplo** permite experimentar sem escrever um texto do zero.

O percentual é uma estimativa de desenvolvimento do significado da ideia. **Não representa a proporção de palavras iguais** entre a ideia e o texto, nem uma nota escolar automática. Leia o texto e use o resultado como apoio à revisão.

## Limites e privacidade

- Até **20 ideias** por análise, com no máximo **600 caracteres por ideia**.
- Texto de até **12.000 caracteres**.
- Cada atualização consulta a API da [TypeSafe](https://docs.typesafe.ai/introduction) e pode consumir créditos.
- O texto e as ideias enviados para análise passam pelo servidor da aplicação e pela API da TypeSafe. Evite inserir dados pessoais ou sigilosos.

## Executar no computador

É necessário ter **Node.js** instalado e uma chave de API da TypeSafe.

No PowerShell, dentro desta pasta:

```powershell
.\iniciar.ps1
```

Quando solicitado, cole a chave no terminal. Ela não é exibida nem gravada em arquivo pelo servidor local. Depois, abra `http://127.0.0.1:4173/`. Para encerrar, pressione `Ctrl+C` no terminal.

Também é possível fornecer `TYPESAFE_API_KEY` como variável de ambiente antes de executar o script. Nunca coloque a chave em `public/`, no README ou em um repositório Git.

## Publicação na Vercel

O projeto usa arquivos estáticos em `public/` e uma função de servidor em `api/check.mjs`. Na Vercel, cadastre `TYPESAFE_API_KEY` em **Project → Environment Variables** como variável do tipo **Secret**, no ambiente **Production**, usando uma chave que não tenha sido compartilhada publicamente. Faça uma nova implantação depois de salvar a variável.

A chave é lida somente pela função de servidor. O navegador chama `/api/check` e não recebe a chave. Para reduzir uso indevido da API, o projeto publicado tem uma regra no firewall da Vercel que limita essa rota a **30 requisições por minuto por IP**.

## Estrutura do projeto

| Caminho | Finalidade |
| --- | --- |
| `public/index.html` | Estrutura da interface. |
| `public/app.css` | Layout, cores e tipografia. |
| `public/app.js` | Interação em tempo real e exibição dos resultados. |
| `public/assets/background.jpg` | Imagem de fundo. |
| `api/check.mjs` | Função da Vercel que recebe o texto e consulta a TypeSafe. |
| `lib/coverage.mjs` | Validação e cálculo dos percentuais. |
| `server.mjs` e `iniciar.ps1` | Servidor para teste local. |

## Créditos

Desenvolvido pelo **professor Dr. Glauber Santiago** — DAC/UFSCar.

Apoio: [**Grupo de Pesquisa Horizonte ↗**](https://grupohorizonte.ufscar.br/) • [**🌐 Website do Docente ↗**](https://servidores.ufscar.br/glauber/)
