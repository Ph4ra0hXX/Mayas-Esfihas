<script>
import { ref, watch, onUpdated } from "vue";
import { carrinhoStore } from "../store/produtos";
import { useToast } from "vue-toastification";
import router from "../router/index";

export default {
  setup() {
    const toast = useToast();

    const carrinho = carrinhoStore();

    const Batata = ref({
      batataFrita: [
        {
          nome: "Pastel - Carne moída, queijo coalho e cebola",
          preco: 11.0,
          quantidade: 0,
        },
        {
          nome: "Pastel - Carne de sol, queijo coalho e cebola",
          preco: 12.0,
          quantidade: 0,
        },
        {
          nome: "Pastel - Carne de sol, queijo especial",
          preco: 12.5,
          quantidade: 0,
        },
        {
          nome: "Pastel - Frango com queijo especial",
          preco: 12.5,
          quantidade: 0,
        },
        {
          nome: "Pastel - Frango, queijo coalho e bacon",
          preco: 12.0,
          quantidade: 0,
        },
        {
          nome: "Pastel - Frango, queijo catupiry e calabresa",
          preco: 11.5,
          quantidade: 0,
        },
        {
          nome: "Pastel - Camarão e queijo especial",
          preco: 15.0,
          quantidade: 0,
        },
        {
          nome: "Pastel - Lombinho, queijo coalho, creme cheese, azeitona e cebola",
          preco: 15.0,
          quantidade: 0,
        },
        {
          nome: "Pastel Maya's - carne moída, calabresa, queijo especial, cebola, azeitona e queijo cheddar",
          preco: 16.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Carne moída, queijo coalho e cebola",
          preco: 19.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Carne de sol, queijo coalho e cebola",
          preco: 19.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Carne de sol, queijo especial",
          preco: 20.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Frango com queijo especial",
          preco: 20.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Frango, queijo coalho, azeitona e bacon",
          preco: 20.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Frango, queijo catupiry e calabresa",
          preco: 20.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Camarão e queijo especial",
          preco: 28.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão - Lombinho, queijo coalho, creme cheese, azeitona e cebola",
          preco: 28.0,
          quantidade: 0,
        },
        {
          nome: "Pastelão Maya's - carne moída, calabresa, queijo mussarela, cebola, azeitona e queijo cheddar",
          preco: 29.0,
          quantidade: 0,
        },
      ],
    });

    function salvarPedido() {
      carrinho.batatas.push(Batata.value);

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
      Batata,
      salvarPedido,
      voltar,
    };
  },
};
</script>

<template>
  <div id="cardapio">
    <div id="listar">
      <div class="dotted-line">
        <hr />
        <span id="textDividers">Pastéis</span>
        <hr />
      </div>

      <div v-for="(item, index) in Batata.batataFrita" :key="item.nome">
        <button class="botao1" @click="item.quantidade++">+</button>

        <button
          v-if="item.quantidade > 0"
          class="botao2"
          @click="item.quantidade--"
        >
          -
        </button>

        <label style="pointer-events: none" id="nomeItem" for="adicional"
          ><span id="quantidadeDiv">{{ item.quantidade }}x</span>
          {{ item.nome }}</label
        >
        <label id="preco">R$: {{ item.preco.toFixed(2) }}</label>
        <p id="itens"></p>
        <br />
      </div>

      <!---------------------------->

      <button @click="salvarPedido" id="butOpcoes" type="submit" value="Submit">
        adicionar
      </button>

      <button id="butOpcoes2" @click="voltar()" type="submit" value="Submit">
        voltar
      </button>
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

.categoria-section {
  margin-top: 20px;
  margin-bottom: 10px;
}

.categoria-titulo {
  color: #f2994b;
  font-size: 24px;
  font-weight: bold;
  margin-bottom: 15px;
  text-align: left;
  padding-left: 10px;
}
</style>
