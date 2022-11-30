<template>
  <div class="box">
    <div class="columns">
      <div
        class="column is-8"
        role="form"
        aria-label="formulário de crição para uma nova taréfa."
      >
        <input
          type="text"
          class="input"
          placeholder="Qual tarefá você deseja iniciar?"
          v-model="descriçao"
        />
      </div>
      <div class="column">
        <div
          class="is-flex is-align-items-center is-justify-content-space-between"
        >
        <section>
          <strong>
            {{ tempoDeCorrido }}
          </strong>
        </section>

          <button class="button" @click="iniciar()" :disabled="CronometroRodando">
            <span class="icon">
              <i class="fas fa-play"></i>
            </span>
            <span>play</span>
          </button>
          <button class="button" @click="finalizar()" :disabled="!CronometroRodando">
            <span class="icon">
              <i class="fas fa-pause"></i>
            </span>
            <span>stop</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Formulario-vue",
  emits:['aoTemporizador', 'aoSalvarTarefa'],
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      CronometroRodando: false,
      descriçao: ''
    };
  },
  computed: {
    tempoDeCorrido() {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8);
    },
  },
  methods: {
    iniciar() {
      this.CronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
    },
    finalizar() {
      this.CronometroRodando = false
      clearInterval(this.cronometro);
      this.$emit('aoTemporizador', this.tempoEmSegundos)
      this.tempoEmSegundos = 0
      this.$emit('aoSalvarTarefa', this.tempoDeCorrido)
      this.descriçao = ''
    },
  },
};
</script>
