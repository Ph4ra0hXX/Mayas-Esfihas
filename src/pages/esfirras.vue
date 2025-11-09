<script>
import { ref } from "vue";
import router from "../router/index";
import { carrinhoStore } from "../store/produtos";
import { useToast } from "vue-toastification";

export default {
  setup() {
    const toast = useToast();

    const carrinho = carrinhoStore();

    const Esfirras = ref({
      salgados: [
        {
          nome: "Esfirra - Calabresa com Queijo",
          descricao: "Sabor marcante e irresistível",
          preco: 6.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Queijo com Salsinha",
          descricao: "Simples, leve e cheio de aroma",
          preco: 6.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Carne Moída com Tomate e Cebola",
          descricao: "O tradicional que nunca sai de moda",
          preco: 6.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Carne de Sol com Queijo Coalho",
          descricao: "Sabor nordestino que derrete na boca",
          preco: 6.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Frango com Catupiry",
          descricao: "Cremoso, suculento e apaixonante",
          preco: 6.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Frango, Bacon e Queijo",
          descricao: "Crocante e cheio de sabor",
          preco: 5.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Marguerita (Queijo, Manjericão e Tomate)",
          descricao: "Um toque italiano na sua mesa",
          preco: 5.5,
          quantidade: 0,
        },
      ],
      tradicionais: [
        {
          nome: "Esfirra - 4 Queijos",
          descricao: "Mussarela, parmesão, provolone e catupiry derretendo",
          preco: 6.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Camarão com Queijo",
          descricao: "Recheio cremoso e sabor do mar",
          preco: 7.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Carne de Sol com Nata e Queijo",
          descricao: "A junção perfeita de tradição e cremosidade",
          preco: 7.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Carne com Requeijão",
          descricao: "Sabor intenso e textura irresistível",
          preco: 7.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Peperoni com Requeijão",
          descricao: "Um toque picante e cremoso",
          preco: 7.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Frango com Requeijão",
          descricao: "Suave e saboroso, impossível resistir",
          preco: 6.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Calabresa com Doritos e Cheddar",
          descricao: "Crocante, ousada e deliciosa",
          preco: 7.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Havaí (Lombinho, Abacaxi e Mussarela)",
          descricao: "Doce, salgado e surpreendente",
          preco: 7.5,
          quantidade: 0,
        },
      ],
      especiais: [],
      doces: [
        {
          nome: "Esfirra - Chocolate com M&M’s",
          descricao: "Divertida e deliciosa",
          preco: 6.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Doce de Leite com Coco",
          descricao: "Sabor caseiro com toque cremoso",
          preco: 6.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Doce de Leite com Banana",
          descricao: "Combinação perfeita de doçura e carinho",
          preco: 7.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Goiaba com Queijo",
          descricao: "Cremosa, única e irresistível",
          preco: 7.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Chocolate com Oreo",
          descricao: "Crocante e irresistível",
          preco: 7.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Chocolate com Morango",
          descricao: "O clássico que conquista corações",
          preco: 8.0,
          quantidade: 0,
        },
      ],
      mayas: [
        {
          nome: "Esfirra - Camarão, tare, salsinha e queijo",
          descricao: "Recheio generoso e queijo derretendo",
          preco: 8.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Cebola Caramelizada, calabresa e creme cheese",
          descricao: "Doce e saborosa",
          preco: 7.5,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Carne à Moda e creme chees",
          descricao: "Suculenta e bem temperada",
          preco: 7.0,
          quantidade: 0,
        },
        {
          nome: "Esfirra - Bacon, queijo, barbecue e cebola",
          descricao: "Para os apaixonados por queijo derretido",
          preco: 7.0,
          quantidade: 0,
        },
      ],
    });

    function salvarPedido() {
      // empurra o objeto inteiro (como faz o burger.vue) para a categoria esfirras
      carrinho.esfirras.push(Esfirras.value);

      router.push("/");

      toast.success("Adicionado com sucesso!", {
        timeout: 2000,
        position: "top-right",
        icon: false,
        showCloseButtonOnHover: true,
      });
    }

    function voltar() {
      router.push("/");
    }

    return {
      Esfirras,
      voltar,
      salvarPedido,
    };
  },
};
</script>

<template>
  <div id="cardapio">
    <div id="listar">
      <div class="dotted-line">
        <hr />
        <span id="textDividers">Esfirras Tradicionais</span>
        <hr />
      </div>

      <div v-for="(item, index) in Esfirras.salgados" :key="index">
        <button class="botao1" @click="item.quantidade++">+</button>

        <button
          v-if="item.quantidade > 0"
          class="botao2"
          @click="item.quantidade--"
        >
          -
        </button>

        <label style="pointer-events: none" id="nomeItem">
          <span id="quantidadeDiv">{{ item.quantidade }}x</span>
          {{ item.nome }}
        </label>
        <label id="preco">R$: {{ item.preco.toFixed(2) }}</label>

        <p id="itens">{{ item.descricao }}</p>
      </div>

      <div class="dotted-line">
        <hr />
        <span id="textDividers">Sabores Especiais</span>
        <hr />
      </div>

      <div v-for="(item, index) in Esfirras.tradicionais" :key="'t' + index">
        <button class="botao1" @click="item.quantidade++">+</button>

        <button
          v-if="item.quantidade > 0"
          class="botao2"
          @click="item.quantidade--"
        >
          -
        </button>

        <label style="pointer-events: none" id="nomeItem">
          <span id="quantidadeDiv">{{ item.quantidade }}x</span>
          {{ item.nome }}
        </label>
        <label id="preco">R$: {{ item.preco.toFixed(2) }}</label>
        <p id="itens">{{ item.descricao }}</p>
      </div>

      <div
        v-if="Esfirras.especiais && Esfirras.especiais.length"
        class="dotted-line"
      >
        <hr />
        <span id="textDividers">Sabores especiais</span>
        <hr />
      </div>

      <div v-for="(item, index) in Esfirras.especiais" :key="'e' + index">
        <button class="botao1" @click="item.quantidade++">+</button>

        <button
          v-if="item.quantidade > 0"
          class="botao2"
          @click="item.quantidade--"
        >
          -
        </button>

        <label style="pointer-events: none" id="nomeItem">
          <span id="quantidadeDiv">{{ item.quantidade }}x</span>
          {{ item.nome }}
        </label>
        <label id="preco">R$: {{ item.preco.toFixed(2) }}</label>
        <p id="itens">{{ item.descricao }}</p>
      </div>

      <div class="dotted-line">
        <hr />
        <span id="textDividers">Esfirras doces</span>
        <hr />
      </div>

      <div v-for="(item, index) in Esfirras.doces" :key="'d' + index">
        <button class="botao1" @click="item.quantidade++">+</button>

        <button
          v-if="item.quantidade > 0"
          class="botao2"
          @click="item.quantidade--"
        >
          -
        </button>

        <label style="pointer-events: none" id="nomeItem">
          <span id="quantidadeDiv">{{ item.quantidade }}x</span>
          {{ item.nome }}
        </label>
        <label id="preco">R$: {{ item.preco.toFixed(2) }}</label>
        <p id="itens">{{ item.descricao }}</p>
      </div>

      <div class="dotted-line">
        <hr />
        <span id="textDividers">Esfirras à moda Maya's</span>
        <hr />
      </div>

      <div v-for="(item, index) in Esfirras.mayas" :key="'m' + index">
        <button class="botao1" @click="item.quantidade++">+</button>

        <button
          v-if="item.quantidade > 0"
          class="botao2"
          @click="item.quantidade--"
        >
          -
        </button>

        <label style="pointer-events: none" id="nomeItem">
          <span id="quantidadeDiv">{{ item.quantidade }}x</span>
          {{ item.nome }}
        </label>
        <label id="preco">R$: {{ item.preco.toFixed(2) }}</label>
        <p id="itens">{{ item.descricao }}</p>
      </div>

      <button id="butOpcoes" @click="salvarPedido" type="button">
        adicionar
      </button>
      <button id="butOpcoes2" @click="voltar()" type="button">voltar</button>
    </div>
  </div>
</template>

<style>
#observacao {
  padding: 5px;
  margin-bottom: 20px;
  height: 60px;
}
#quantidadeDiv {
  font-weight: bold;
  color: #f2994b;
  font-size: 20px;
}

#textDividers {
  color: #f2994b;
  font-family: "Great Vibes";
  font-size: 40px;
  font-weight: lighter;
}
.dotted-line {
  display: flex;
  align-items: center;
  text-align: center;
  margin: 20px 0;
}

.dotted-line hr {
  flex: 1;
  border: none;
  border-top: 2px dashed white;
  margin: 0 10px;
}

.dotted-line span {
  font-size: 18px;
  font-weight: bold;
  color: #333;
}

.botao1 {
  background-color: #f2994b;
  color: #000000;
  border: none;
  padding: 5px 10px;
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
  border-radius: 5px;
  border-bottom-left-radius: 20px;
  border-top-left-radius: 20px;
  width: 35px;
  margin-right: 2px;
}

.botao2 {
  background-color: #f2994b;
  color: #000000;
  border: none;
  padding: 5px 10px;
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
  border-radius: 5px;
  border-bottom-right-radius: 20px;
  border-top-right-radius: 20px;
  width: 35px;
  margin-left: 2px;
}

#nomeItem {
  font-size: 16px;
  margin-left: 7px;
}
#tituloRadio {
  display: flex;
  align-items: center;
}

#tituloDoRadio {
  margin-left: 3px;
}

input[type="radio"] {
  margin-left: -3px;
  border: 0px;
  width: 30px;
  height: 2em;
  accent-color: #f27141;
}
</style>
