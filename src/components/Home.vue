<template lang="html">
  <div class="container">
    <h1 style="margin-top: 20vw" class="display-1">{{title}}</h1>
    <div style="margin-top: 2vw" class="btn-group btn-group-lg" role="group">
      <button type="button" v-on:click="createWallet" class="btn btn-danger">New Wallet</button>
    </div>
    <br><br>
    <div id="panel1" class="console panel panel-default" :class="displayClass">
      <div class="panel-heading">
        <h3 class="panel-title"> Public Address </h3>
      </div>
      <div class="panel-body">
        {{ public_addr }}
      </div>
    </div>
    <div id="panel2" class="console panel panel-default" :class="displayClass">
      <div class="panel-heading">
        <h3 class="panel-title"> Mnemonic seed </h3>
      </div>
      <div class="panel-body">
        {{ mnemonicString }}
      </div>
    </div>
    <hr>
    <i>
      Source code @  <a target="_blank" href="https://github.com/troublesomepony/xmr-paper">Github.com/troublesomepony/XMR-Paper</a>
    </i>
  </div>
</template>

<script>
const walletUtils = require('mymonero-core-js/monero_utils/monero_wallet_utils')

export default {
  data () {
    return {
      title: 'Monero X Paper',
      displayClass: 'is-hidden',
      mnemonicString: '',
      public_addr: ''
    }
  },
  methods: {
    createWallet: function () {
      const wallet = walletUtils.NewlyCreatedWallet('english')
      this.public_addr = wallet.keys.public_addr
      this.mnemonicString = wallet.mnemonicString
      this.displayClass = ''
    }
  }
}
</script>

<style lang="css">
  .panel-body {
    font-size: 16px;
    text-align: left;
    color: #2bf22b;
    background-color: #000;
  }
  .console {
    overflow-wrap: break-word;
    margin: auto;
    max-width: 720px
  }

  .is-hidden {
    visibility: hidden;
  }
</style>
