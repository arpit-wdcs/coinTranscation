# coinTranscation 
# Transfer ETH from one account to another.
  Using Javascript snippet.

const Web3 = require('web3');
const web3 = new Web3('https://ropsten.infura.io/v3/59fd57aba709479fa514e3657958f04e')

const privateKey = 'bf4053ec2c76998bb1f3591622bf404f70cada7f81fb62503617220c0f907f31'
const fromAdress = '0x444E0Ee26a0dd479537B17dE7802a7E3a070F25F'
const toAddress = '0x1B59584017c9Dea400B4A3de113ACC1486Ea6D9a'

async function eth_transaction() {
    var value = web3.utils.toWei('0.1', 'ether')

    var SignedTransaction = await web3.eth.accounts.signTransaction({
        to: toAddress,
        value: value,
        gas: 2000000
    }, privateKey);

    web3.eth.sendSignedTransaction(SignedTransaction.rawTransaction) .then((reciept)=>{
        console.log(reciept);
    });
}

eth_transaction()
