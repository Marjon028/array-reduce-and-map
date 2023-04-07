<script>
    import { bind } from "svelte/internal";


   
let obj = {you: 2, me:3, foo: 4, bar: 15};
let arr = structuredClone([obj]);

let entries = Object.entries(obj);

// [["you",100],["me",75],["foo",116],["bar",15]]

let arr1 = Object.values(obj);  
let sorted = entries.sort();
let get_obj = Object.keys(obj);

let txt1 = "";
let txt2 = "";

let newArr1 = arr1.reduce(myFunction_reduce)
let newArr =arr1.map(myFunction_map)

function myFunction_map(num) {
  return num *3;
}
function myFunction_reduce(total,num) {
  return total + num ;
}
function pushme(num){
 
    arr1.push(Number(num));
    arr1=arr1
    newArr.push(myFunction_map(num));
   newArr1= arr1.reduce(myFunction_reduce)
    entries.push(myFunction_map(num));
    entries=entries;
    newArr=newArr;
  




}

/*git remote add origin https://github.com/Marjon028/array-reduce-and-map.git
git branch -M main
git push -u origin main*/

    </script>
     <input type="text" bind:value={txt2} placeholder="search arr data">
     {#if arr1.includes(Number(txt2))}
     <h1>hello</h1>
        
     {/if}
    <input type="text" bind:value={txt1} placeholder="for add data objects">
<button on:click={()=>pushme(txt1)}> push</button>



<h1>array contents = {arr1}</h1>
<h1>example of reduce array add whole data = {newArr1}</h1>
<h1>example of map array *3 the contents = {newArr}</h1>
{#each newArr as c ,i}
<p>sorted: {sorted[i]} </p>
  
{/each}

{#each newArr as c ,i}

<h2>entries get value {entries[i]}</h2>
{#if newArr[i]%2===0}
<p>even {newArr[i]}</p>
{:else}
<p>odd {newArr[i]}</p>
{/if}

    
{/each}

 
 
