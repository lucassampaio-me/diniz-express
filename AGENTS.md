# Repository Guidelines

## Estrutura do Projeto e Organização dos Módulos
Este repositório é um site estático de marketing da Diniz Express. Mantenha a estrutura da página em `index.html`, o comportamento interativo em `js/main.js` e os estilos-fonte do Tailwind em `css/input.css`. O CSS compilado fica em `css/output.css` e deve ser gerado a partir do arquivo-fonte, então edite `input.css` e rode o build em vez de alterar `output.css` manualmente. Materiais de referência ficam em `DESIGN.md`, `copy_diniz_express.md` e `CLAUDE.md`. Não edite `node_modules/`; é saída instalada e deve permanecer fora de versão.

## Comandos de Build, Teste e Desenvolvimento
Execute `npm install` para instalar as dependências do Tailwind CLI.

Use `npm run watch` durante o desenvolvimento para recompilar `css/output.css` sempre que `css/input.css` mudar.

Use `npm run build` antes de entregar alterações para gerar a folha de estilos minificada usada por `index.html`.

Não há servidor local configurado em `package.json`; abra `index.html` diretamente no navegador para revisão manual.

## Estilo de Código e Convenções de Nomenclatura
Use indentação de 2 espaços em HTML, CSS e JavaScript, seguindo os arquivos atuais. Prefira seções semânticas em `index.html`, nomes de classe em kebab-case como `.container-main` e `.sticky-whatsapp`, e funções JavaScript curtas com nomes baseados em verbos, como `initAccordion()`. Mantenha os textos em português do Brasil, salvo quando a alteração exigir outro idioma. Considere `DESIGN.md` como a fonte principal para cores, tipografia, espaçamento e intenção dos componentes.

## Diretrizes de Testes
Ainda não existe uma suíte de testes automatizados. Valide alterações executando `npm run build` e revisando `index.html` manualmente no navegador, com atenção especial ao layout responsivo, links de WhatsApp, comportamento do accordion e animações de scroll. Se testes automatizados forem adicionados depois, coloque-os em uma pasta `tests/` e use nomes no padrão `*.test.js`.

## Diretrizes de Commit e Pull Request
O histórico Git não está disponível neste workspace, então não foi possível inferir uma convenção específica do repositório. Use mensagens de commit curtas e no imperativo, como `Ajusta espacamento do CTA da hero` ou `Melhora suporte de teclado no accordion`. Pull requests devem resumir a mudança visível para o usuário, listar os arquivos afetados, registrar a validação manual realizada e incluir capturas de tela em alterações visuais ou de layout.

## Segurança e Conteúdo
Evite versionar segredos, arquivos temporários ou exports locais. Links externos, números de telefone, horários de atendimento e promessas de serviço em `index.html` são conteúdos críticos para o negócio e devem ser verificados antes da publicação.
