# Exercício – Módulo 15: Conversão de CSS para SASS

## Descrição

Este exercício faz parte do módulo 15 do curso de Front-end da EBAC. O objetivo foi transformar um arquivo CSS tradicional em uma estrutura organizada utilizando **SASS**, aplicando boas práticas como reutilização de código, uso de variáveis e modularização.

---

## O que foi feito

- ✅ O arquivo `style.css` foi convertido para o padrão **SASS**, separando as responsabilidades em arquivos como `main.scss`, `reset.scss` e `variaveis.scss`.
- ✅ Foram criadas variáveis de cores e fontes para facilitar a manutenção e garantir consistência visual no projeto.
- ✅ Breakpoints para dispositivos móveis e tablets foram definidos como variáveis para facilitar a responsividade.
- ✅ O sistema de **módulos do SASS** foi utilizado com `@use` para importar `reset` e `variaveis` no `main.scss`.
- ✅ O layout foi mantido fiel ao original, porém agora com uma estrutura mais escalável e organizada.

---

## Organização dos arquivos

```bash
.
├── config/
│   ├── reset.scss
│   └── variaveis.scss
├── main.scss
└── index.html
