To get a price on uniswap
pair = IUniswapV2Pair(UniswapV2Library.pairFor(factory, input, output))
array reserves = pair.getReserves()
router.quote(uint amountA, uint reserveA, uint reserveB) 

Now let's say our profitable pair is OXT-PNK

we fetch the pair (oxt, pnk) from uniswap

we also fetch (dai, oxt)

first we lock locket with lock(input:oxt, output:pnk, inputDai, outputDai)
this registers the trade under msg.sender.

Now we have a locketCallee which implements the Icallee
On lock, locket registers the tokens, expectedDai, inputDai, msg.sender, direction into a mapping

Now we call (dai, WETH).swap(amount0, amount1, to:locketCallee, new bytes(1)) where amount1==0

locketCallee inspects msg.sender and retrieves registered parameters.

uniswap buy -> oxt with dai.

if(direction==Behodler){

    buy PNK with OXT on Behodler //get pyroOXT
    Sell OXT for PNK on Uniswap

}else {
   buy PNK with OXT on uniswap
   sell OXT for PNK on Behodler //get pyroOXT
}
Sell PNK for newDAI on uniswap 
require(newDai >Dai)
find out required amount
send required to uniswap
send newDai-required to sender

**if favourable trade is Dai->MKR:**

if(direction==Behodler){

    buy MKR with Dai on Behodler //burn WeiDai
    sell MKR for Dai on uniswap

}
else {

    buy MKR with Dai on uniswap
    sell MKR for Dai on Behodler //burn WeiDai

}
require(newDai >Dai)
find out required amount
send required to uniswap
send newDai-required to sender

if pair includes weth then call (dai, usdtc //or whatever has high liquidity).swap
