# NAC10CICD
Laboratório com teste de aplicação node utilizando a integração Git + Travis + Heroku

![alt tag](https://github.com/fiapsecdevops/NAC10CICD/raw/master/images/logo-lab.png)


> Neste laboratório executaremos a construção do exercício anterior: Uma aplicação node utilizando repositório Git utilizará o Travis como CI para execução de um teste funcional, este teste será utilizado como "triger" para o delivery da aplicação utilizando a plataforma PAAS Heroku.

---

## Pré-requisitos

Para a execução deste laboratório os seguinte requisitos devem ser verificados;

1. Acesso na plataforma [github](https://github.com);
2. Acesso na plataforma [heroku](https://www.heroku.com/);
3. Acesso na plataforma [travis](http://travis-ci.org);*
4. Instalação do [Heroku Cli](https://devcenter.heroku.com/articles/heroku-cli);**
5. Instalação do [Travis Cli](https://github.com/travis-ci/travis.rb);**

*  Para este acesso é possível executar login utlizando a conta no Github;
** Os clientes de linha de comando do Heroku e Travis serão disponibilizados em um host para execução do exercício;

---

## Etapa 1 - Entrega da aplicação utilizando o Heroku Cli

![alt tag](https://github.com/fiapsecdevops/NAC10CICD/raw/master/images/etapa1-lab.png)

**Objetivo:** Testar a aplicação usando o Heroku (será necessário criar a app antes na plataforma).

1. Faça login no github e execute um fork [deste repositório](https://github.com/fiapsecdevops/NAC10CICD-APP) ele possui a base de código necessária para testar o funcionamento da aplicação e sua entrega de forma direta ou utilizando encapsulamento em containers (repositórios utilizados em aulas anteriores podem ser removidos);

2. Após o Fork clone o repositório localmente no mesmo host onde o Heroku Cli está instalado;

3. A partir do diretório do projeto que acabou de clonar, faça login no Heroku e utilize a sequência abaixo para criar uma app:

```sh
heroku login -i
heroku create
```

![alt tag](https://github.com/fiapsecdevops/NAC10CICD/raw/master/images/lab-step-01.png)

> Após o login o segundo comando criará uma aplicação com um nome randomico, isso é necessário pois o nome de um projeto no Heroku app é sempre único;

4. Entregando uma versão preliminar da aplicação de forma direta (sem utilizar o CI):

```sh
git push heroku master
```

Neste processo o Heroku receberá um push com o código base da aplicação, como não houve uma declaração direta da linguagem de programação a plataforma tentará inferir a linguagem com base nos commits executados no repositório master e o processo de deploy deverá ocorrer como esperado:

![alt tag](https://github.com/fiapsecdevops/NAC10CICD/raw/master/images/lab-step-02.png)

> No caso do node por exemplo, essa inferência da linguagem de programação em uso ocorre devido a estrutura do package.json com pacotes NPM, se você enviasse um aplicativo escrito em PHP com um composer.json essa app seria provavelmente identificada como uma app escrita em PHP. Segundo na documentação oficial da plataforma disponível no endereço https://devcenter.heroku.com/articles/buildpacks essa identificação ocorre no primeiro envio devido a ordem na qual os buildpacks são chamados para detecção.

Após o deploy teste a aplicação acessando a URL da aplicação;

---