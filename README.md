# Desenvolvedor Full Stack - AMMO Varejo

## Connected Cells in a Grid

Resolução em js do desafio **Connected Cells in a Grid**.

### Solução

```js
const obtemMaiorRegiao = matriz => {
    let regiaoMaxima = 0;

    for(let linha = 0; linha < matriz.length; linha++) {
        for(let coluna = 0; coluna < matriz[linha].length; coluna++) {
            let tamanho = obtemTamanhoRegiao(matriz, linha, coluna);
            regiaoMaxima = Math.max(tamanho, regiaoMaxima);
        }
    }

    return regiaoMaxima;
};

const obtemTamanhoRegiao = (matriz, linha, coluna) => {
    if(linha < 0 || coluna < 0 || linha >= matriz.length || coluna >= matriz[linha].length)
        return 0;
    
    if(matriz[linha][coluna] == 0)
        return 0;

    matriz[linha][coluna] = 0;
    
    let tamanho = 1;
    
    for (let r = linha - 1; r <= linha + 1; r++) {
        for(c = coluna - 1; c <= coluna + 1; c++) {
            if(r != linha || c != coluna) {
                tamanho += obtemTamanhoRegiao(matriz, r, c);
            }
        }
        
    }

    return tamanho;
}
```
### Teste

Saída = 5
```js
// [1,1,0,0]
// [0,1,1,0]
// [0,0,1,0]
// [1,0,0,0]
obtemMaiorRegiao([[1,1,0,0],[0,1,1,0],[0,0,5,0],[1,0,0,0]]);

```
