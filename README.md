# Requerimientos del Proyecto - SimpleDEX en Scroll Sepolia

Se deben desplegar contratos inteligentes en la red de **Scroll Sepolia** (verificados y publicados) para implementar un **exchange descentralizado simple** que intercambie dos tokens ERC-20.

## Funcionalidades requeridas

La solución debe permitir:

- **Añadir liquidez**:  
  El `owner` puede depositar pares de tokens en el pool para proporcionar liquidez.

- **Intercambiar tokens**:  
  Los usuarios pueden intercambiar uno de los tokens por el otro utilizando el pool de liquidez.

- **Retirar liquidez**:  
  El `owner` puede retirar sus participaciones en el pool.

## Requisitos técnicos

- **Tokens ERC-20**:  
  Se deben crear dos tokens ERC-20 simples.  
  - Los contratos de los tokens deben tener obligatoriamente los nombres: `TokenA` y `TokenB`.

- **Contrato de Exchange - `SimpleDEX`**:  
  Debe implementarse un contrato inteligente llamado **SimpleDEX** que:
  - Mantenga un **pool de liquidez** para `TokenA` y `TokenB`.
  - Utilice la fórmula del **producto constante** para calcular los precios de intercambio:  
    ```
    (x + dx)(y - dy) = xy
    ```
  - Permita **añadir y retirar liquidez**.
  - Permita **intercambiar** `TokenA` por `TokenB` y viceversa.

### Funciones obligatorias del contrato `SimpleDEX`

El contrato debe contar **obligatoriamente y sin modificación** en su interfaz con las siguientes funciones:

```solidity
constructor(address _tokenA, address _tokenB)
addLiquidity(uint256 amountA, uint256 amountB)
swapAforB(uint256 amountAIn)
swapBforA(uint256 amountBIn)
removeLiquidity(uint256 amountA, uint256 amountB)
getPrice(address _token)
