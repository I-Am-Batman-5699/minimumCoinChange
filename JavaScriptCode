function min(param1,param2){
    return (param1<param2) ? param1: param2 ;
}
function minCoinChange(coins,value){
    const coinsArry = coins.sort();
    const sum = value;
    let distTable = [[]];
    coinsArry.forEach(el => distTable.push([]));
    for (let index = 0; index <= value; index++) {
        distTable[0].push(index);
    }
    for(let i=1 ; i<=coinsArry.length ; i++){
        for (let j = 0; j <= value; j++) {
            if(coinsArry[i-1]>j){
                distTable[i][j] = distTable[i-1][j];
            }else{
                distTable[i][j] = min(distTable[i-1][j] , distTable[i][j-coinsArry[i-1]] +1 );
            }
        }
    }
    return distTable[distTable.length-1][distTable[distTable.length-1].length-1];
}

const result = minCoinChange([ 9, 6, 5, 1 ], 11);
console.table(result);
