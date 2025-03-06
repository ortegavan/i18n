# I18n

Esta é uma prova de conceito para internacionalização de aplicações em Angular.

1. Adicione o módulo de internacionalização ao seu projeto:

```bash
ng add @angular/localize
```

Se o pacote não for adicionado, ocorrerá um erro ao tentar usar o atributo `i18n` em um template.

2. Adicione o atributo `i18n` ao(s) elemento(s) que deseja internacionalizar:

```html
<h1 i18n>Hello i18n!</h1>
```

3. Extraia o arquivo de tradução:

```bash
ng extract-i18n --output-path src/locale --out-file messages.en.xlf
```

4. Copie o arquivo extraído e, com base nele, crie outro arquivo, um para cada idioma. Por exemplo, `messages.pt.xlf`:

```bash
cp src/locale/messages.en.xlf src/locale/messages.pt.xlf
```

5. Traduza o conteúdo de cada novo arquivo para o idioma desejado. Existem ferramentas como https://poeditor.com que podem ajudar nessa etapa.

6. Configure o angular.json para trabalhar com os arquivos de tradução:

```json
"projects": {
    "i18n": {
        "i18n": {
            "sourceLocale": "en-US",
            "locales": {
                "pt": "src/locale/messages.pt.xlf"
            }
        },
        ...
    }
}
```

e

```json
"architect": {
    "build": {
        "options": {
            "localize": true,
        }
    }
}
```

7. Compile o projeto para que os arquivos de tradução sejam incluídos no build:

```bash
ng build --localize
```

8. Execute o projeto com o idioma desejado (altere o "localize" no arquivo angular.json para o idioma desejado, deixe true para o idioma padrão):

```bash
ng serve --configuration=pt-BR
```
