[![Typing SVG](https://readme-typing-svg.herokuapp.com?font=Fira+Code&pause=1000&color=691AF7&background=64646400&width=435&lines=Bem+vindo++!!!+%3A)+)](https://git.io/typing-svg)
<h2 align="left">Oii!😎<br>Aqui é a Brunna Souza Martins (●'◡'●)<br>Aprendendo e vivendo ^_^</h2>

###

<div align="right">
  <img src="https://github-readme-stats.vercel.app/api?username=Brunna-0909&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=rose_pine&locale=en&hide_border=false&order=1" height="159" alt="stats graph"  />
</div>

###

<img align="right" height="158" src="https://i.pinimg.com/originals/a4/a5/21/a4a5213d12274e96ae25f2468aad27bc.gif"  />

###

<div align="left">
  <a href="https://www.instagram.com/brunnasouzamartins/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Instagram&logo=instagram&label=&color=E4405F&logoColor=white&labelColor=&style=for-the-badge" height="36" alt="instagram logo"  />
  </a>
</div>

###

<br clear="both">
name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

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

###
