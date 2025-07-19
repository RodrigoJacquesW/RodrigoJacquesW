# 👩🏻‍💻 Rodrigo Jacques Wolff

**Engenheiro Civil - Estudante de dados**

Me chamo Rodrigo Jacques Wolff, tenho 25 anos e sou natural de Santa Catarina. Sou formado em Engenharia Civil pelo IFSC (Instituto Federal de Santa Catarina) e atuei na construção civil durante cinco anos, atualmente trabalho como analista de dados. Aproveito meu tempo livre para estudar engenharia de dados: Extrações, Automatizações, Pipeline, Versionamento, Banco de Dados e afins.

<a href="https://www.linkedin.com/in/Rodrigo-Jacques-Wolff" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 

### 📊 Estatísticas

<p>
  <img 
    align="left" 
    alt="GitHub Stats" 
    height="150" 
    style="padding-right: 10px;" 
    src="https://github-readme-stats.vercel.app/api?username=RodrigoJacquesW&show_icons=true&theme=tokyonight&include_all_commits=true" 
  />

<img 
      align="left" 
      alt="GitHub Stats" 
      height="150" 
      src="https://github-readme-stats.vercel.app/api/top-langs/?username=RodrigoJacquesW&theme=tokyonight&layout=compact&custom_title=Tecnologias" 
  />

name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
