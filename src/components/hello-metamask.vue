<template>
  <div class='metamask-info'>
    <p>Metamask: {{ web3.isInjected }}</p>
    <p>Network: {{ web3.networkId }}</p>
    <p>Account: {{ web3.coinbase }}</p>
    <p>Balance: {{ web3.balance }}</p>
    <a @click="send">send bnb</a>
  </div>
</template>

<script>
export default {
  name: 'hello-metamask',
  computed: {
    web3 () {
      return this.$store.state.web3
    }
  },
  methods:{
    send(){
      this.web3.web3Instance().eth.sendTransaction(
        {
          from: '0x3014734DC6E7A17a7783517393053DeFF324790e', 
          to:'0x1953e2A26c1325C924BFDD11ed3C0Cd9E498f869', 
          value: web3.toWei(0.1, 'ether'), 
          gasLimit: 21000, 
          gasPrice: 20000000000
        },function(err, transactionHash) {
          if (!err)
            console.log(transactionHash); 
        }
      )
    }
  }
}
</script>

<style scoped></style>
