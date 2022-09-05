# minimumCoinChange
To get Minimum number of coins when there is an infinite supply of coins

inputs are coins,value
const coinsArry = coins.sort();
1. Create an nXm array
   let distTable = [[]];
   n = coins array length + 1
   m = given value
   coinsArry.forEach(el => distTable.push([]));
2. array[0] = 0 to m
   for (let index = 0; index <= value; index++) {
        distTable[0].push(index);
    }
3. Iterate for each coin 
   for(let i=1 ; i<=coinsArry.length ; i++){
        for (let j = 0; j <= value; j++) {
            if(coinsArry[i-1]>j){
                distTable[i][j] = distTable[i-1][j];
            }else{
                distTable[i][j] = min(distTable[i-1][j] , distTable[i][j-coinsArry[i-1]] +1 );
            }
        }
    }
┌─────────┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬────┬────┐
│ (index) │ 0 │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │ 11 │
├─────────┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼────┼────┤
│    0    │ 0 │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │ 11 │
│    1    │ 0 │ 1 │ 2 │ 3 │ 4 │ 5 │ 6 │ 7 │ 8 │ 9 │ 10 │ 11 │
│    2    │ 0 │ 1 │ 2 │ 3 │ 4 │ 1 │ 2 │ 3 │ 4 │ 5 │ 2  │ 3  │
│    3    │ 0 │ 1 │ 2 │ 3 │ 4 │ 1 │ 1 │ 2 │ 3 │ 4 │ 2  │ 2  │
│    4    │ 0 │ 1 │ 2 │ 3 │ 4 │ 1 │ 1 │ 2 │ 3 │ 1 │ 2  │ 2  │
└─────────┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴────┴────┘
   if the value of coin is greater than the index then we are considering index because coins value is more. ( we cant give 1 buck note from 50bucks)
   else we consider min of (the above value and value from the same colum where index will be index-coinValuem + 1
4. Whatever the value you get at the last row last colum will be the minimum number of coins
   distTable[distTable.length-1][distTable[distTable.length-1].length-1];
