O **GitHub Profile 3D Contrib** é uma ação do GitHub que gera uma representação tridimensional do seu gráfico de contribuições, criando uma imagem 3D para ser exibida no seu perfil. Essa ferramenta permite visualizar suas contribuições de forma mais dinâmica e personalizada.

Para utilizar essa ação, siga os passos abaixo:

1. **Crie um repositório especial**: Crie um repositório no GitHub com o mesmo nome do seu nome de usuário. Por exemplo, se seu nome de usuário é `octocat`, o repositório deve ser `octocat/octocat`.

2. **Adicione um arquivo de workflow**: No repositório criado, adicione um arquivo de workflow do GitHub Actions com o seguinte conteúdo:

    ```yaml
    name: GitHub-Profile-3D-Contrib

    on:
      schedule:
        - cron: "0 18 * * *"  # Executa diariamente às 18:00 UTC
      workflow_dispatch:

    jobs:
      build:
        runs-on: ubuntu-latest
        name: generate-github-profile-3d-contrib
        steps:
          - uses: actions/checkout@v4
          - uses: yoshi389111/github-profile-3d-contrib@latest
            env:
              GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
              USERNAME: ${{ github.repository_owner }}
          - name: Commit & Push
            run: |
              git config user.name github-actions
              git config user.email github-actions@github.com
              git add -A .
              if git commit -m "generated"; then
                git push
              fi
    ```

    Este workflow está configurado para ser executado diariamente às 18:00 UTC. Você pode ajustar o horário conforme sua preferência, lembrando que deve ser especificado em UTC. citeturn0search0

3. **Execute o workflow manualmente**: Após adicionar o workflow, você pode iniciá-lo manualmente navegando até a aba "Actions" no seu repositório, selecionando "GitHub-Profile-3D-Contrib" e clicando em "Run workflow".

4. **Adicione a imagem ao README.md**: Após a execução bem-sucedida do workflow, uma imagem 3D das suas contribuições será gerada no diretório `profile-3d-contrib`. Para exibi-la no seu perfil, adicione a seguinte linha ao seu `README.md`:

    ```markdown
    ![](./profile-3d-contrib/profile-green-animate.svg)
    ```

Além disso, existe uma extensão para o Chrome chamada **GitHub Isometric Contributions** que permite visualizar seu gráfico de contribuições do GitHub em 3D diretamente no navegador. Essa extensão adiciona uma opção para alternar entre a visualização 2D e 3D do gráfico de contribuições no seu perfil do GitHub. citeturn0search5

Para uma demonstração visual de como visualizar um modelo 3D do seu gráfico de contribuições do GitHub, você pode assistir ao seguinte vídeo:

videoVisualize um modelo 3D do seu gráfico de contribuições do GitHubturn0search2 