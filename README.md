
# Hi! I'm Marina Santana 👋

🎓 I'm an Analysis and Systems Development (ADS) student at FIAP.

💻 I'm passionate about technology and software development.
I'm currently learning programming, building projects and developing
my skills as a developer.

## 📚 Currently Learning

- ☕ Java
- 🗄️ SQL
- 🌐 HTML & CSS
- ⚡ JavaScript
- 🐙 Git & GitHub

## 📊 GitHub Stats

<div align="center">

<img height="180em" src="./profile/stats.svg"/>

<img height="180em" src="./profile/top-langs.svg"/>

</div>


## 🛠️ Technologies & Tools

<div align="left">

<img src="https://skillicons.dev/icons?i=html,css,js,java,git,github,vscode" />

</div>

## 🚀 Goals

I'm currently focused on improving my programming skills,
building real projects and preparing myself for opportunities
in the technology industry.

## 📫 Connect with me

<div>
  <a href="https://github.com/marinasantanaq">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white">
  </a>
</div>
name: Update README cards

on:
  schedule:
    - cron: "0 0 * * *" # Runs once daily at midnight
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    permissions:
      contents: write

    steps:
      - uses: actions/checkout@v6

      - name: Generate stats card
        uses: stats-organization/github-readme-stats-action@v2
        with:
          card: stats
          options: username=${{ github.repository_owner }}&show_icons=true
          path: profile/stats.svg
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Generate top languages card
        uses: stats-organization/github-readme-stats-action@v2
        with:
          card: top-langs
          options: username=${{ github.repository_owner }}&layout=compact&langs_count=6
          path: profile/top-langs.svg
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Generate pin card
        uses: stats-organization/github-readme-stats-action@v2
        with:
          card: pin
          options: username=stats-organization&repo=github-readme-stats
          path: profile/pin-stats-organization-github-readme-stats.svg
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Commit cards
        run: |
          git config user.name "github-actions[bot]"
          git config user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git add profile/*.svg
          git commit -m "Update README cards" || exit 0
          git push
