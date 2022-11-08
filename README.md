# alura-tracker

https://bulma.io

# #1 __Iniciando Alura Tracker__

- __Iniciar um projeto novo, utilizando TypeScript e Vue3__;

    - Aprendemos como instalar e utilizar o vue cli para construir um novo projeto, customizando inclusive as dependências que teremos.

- __Importar o Bulma__;
    
    - Fazendo uma única importação, no index.html, passamos a ter disponível todos as facilidades desse framework CSS.

- __Criar componentes__;

    - Para cada novo componente, criamos um arquivo Vue com as seguintes sessões: template, para o html. script, para o comportamento e style para o visual.

- __Escutar eventos de clique;__

    - O Vue nos ajuda a trabalhar com eventos, basta utilizarmos a sintaxe @NOMEDOEVENTO direto no elemento que queremos ouvir.

- __Trabalhar com intervalos.__

    - O setInterval é perfeito para nosso cenário, de incrementar o tempo decorrido a cada segundo.


# #2 __Compondo Componentes__


## Sobre o object Date():

https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global_Objects/Date

```javascript
new Date().toLocaleTimeString() //Esse método já retorna o horário, localizado de acordo com o idioma do navegador. Saiba mais sobre ele
```


## Propriedade do componente pai

É possivel passar propriedades entre os componentes ( Componente Pai --> Componente Filho )


__ChildComponent.vue__
```ts
 import { defineComponent } from 'vue';

    export default defineComponent({
        name: 'CronometroComponent',
        props:{ // Aqui são as propriedades do componente
            tempoEmSegundos:{ //Declararação da propriedade que queremos receber
                type: Number, // tipo de prop
                default: 0,   // valor padrão da pro
            }
        },
        computed:{
            tempoDecorrido(): string {
                return new Date(this.tempoEmSegundos * 1000).toISOString().substring(19,11);
            }
        }
    })

```
__FatherComponent.vue__
```html
<!-- <tamplate>  ...-->
 <section>
    <strong>
        <Cronometro :tempoEmSegundos="tempoEmSegundos"  />
                <!--:propriedadedoComponenteFilho="DadoComponentepai"  -->
    </strong>
</section>
```

```ts

// <script lan='ts'>  ...-->

export default defineComponent({
    name: 'TemporizadorComponent',
    components:{
        Cronometro,
    },
    data(){
        return{
            tempoEmSegundos: 0, // dado do componente que queremos passar
            cronometro: 0,
            cronometroRodando: false
        }
    },

    //.
    //.
    //.
    

```


- __Refatorar componentes em componentes menores;__

    - Vimos que é muito fácil atribuir funcionalidades demais a um componente existente. Quando isso aconteceu, aprendemos a refatorar o componente em componentes menores e mais coesos.

- __Formatar a exibição de X segundos em HH:mm:ss;__

    - Aprendemos que podemos construir um objeto Date passando em seu construtor a quantidade de microsegundos decorridos. Depois, fatiamos a string para pegarmos somente as horas, minutos e segundos.

- __Emitir eventos customizados;__

    - Aprendemos a utilizar o $emit para criar eventos utilizados na comunicação entre componentes.

- __Ouvir eventos customizados.__
    - Aprendemos que ouvir eventos customizados é tão simples quanto ouvir eventos HTML, como o click por exemplo.



# __Desafio Alura__

Repare esse trecho de código do nosso template do componente Temporizador:

```html
<button class="button" @click="iniciar" :disabled="cronometroRodando">
    <span class="icon">
        <i class="fas fa-play"></i>
    </span>
    <span>play</span>
</button>
<button class="button" @click="finalizar" :disabled="!cronometroRodando">
    <span class="icon">
        <i class="fas fa-stop"></i>
    </span>
    <span>stop</span>
</button>

```

> Eles são muito parecidos! Que tal criar um componente que representa um botão e reaproveitá-lo?

> Dica: repare que ele emite um evento de clique e que possui uma prop que indica se ele está desabilitado. Além disso, O texto e o ícone também são bons candidatos a props.


# #3 __Trabalhando com Listas__


- __#Renderizar listas com o v-for;__

    - Utilizamos um mecanismo de repetição para renderizar N vezes uma tarefa, onde N é o tamanho da lista. Isso faz com que nossa lista seja dinâmica.

- __#Condicionais com v-if / v-else;__

    - Aprendemos como esconder ou exibir um componente, dado um estado específico utilizando a diretiva v-if.

- __#Fallback de conteúdo com o operador || (OU);__

    - Utilizamos o operador OU para exibir um texto padrão, caso a tarefa não possua uma descrição.

- __#Slots.__

    - Aprendemos a lidar com o slot quando criamos um componente para representar o Box. Assim, conseguimos exibir os elementos filhos dentro do nosso Box.



# #3 __Estilos Estilosos__

- Variáveis css

Ex.

```css

main{
  --bg-primario: #ffffff;
  --texto-primario: #000;
}

main.modo-escuro{
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo{
  background-color: var(--bg-primario);
  
}

```


- __Uso de variáveis CSS para temas (claro/escuro);__

    - Utilizando essas variáveis, nós podemos facilmente controlar o tema do nosso Alura Tracker, alterando a cor de fundo e a cor do texto de acordo com o tema aplicado.

- __Adicionar e remover classes baseado num estado do componente;__

    - Aprendemos a adicionar ou remover classes, condicionalmente utilizando a diretiva :class.


- __Estilos via objetos.__

    - Aprendemos uma nova forma de aplicar estilos a um elemento, utilizando um objeto que representa as propriedades e seus valores.