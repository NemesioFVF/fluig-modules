# fluig-modules

Visto que <em><strong>desenvolvedores Fluig</strong></em> apresentam uma grande dificuldade durante
o desenvolvimento no ciclo de vida de um projeto/produto no inicio de suas carreiras, 
este repositório tem como objetivo disponibilizar uma coleção de modulos e scripts que
irão <em><strong>aumentar a sua produtividade no desenvolvimento dentro da plataforma Fluig</strong></em>.

> Validate Form

<details>
<summary>1. Capturar entradas vazias em inputs e gera mensagem</summary>

```js 
/*
    Recebe o formulário e uma lista de NAMEs e Referências de inputs
    Verifica se há inputs vazios
    Retorna quantidade de inputs vazios
    Retorna lista/mensagem de inputs vazios
*/

/**
 * 
 * @param {Array} nameList
 * @param {Array} idList
 */


function getEmptyInputs(form, idList, nameList) {
    var emptyInputs = 0;

    var message = 'Os seguintes campos são obrigatórios!\n';

    for (var index = 0; index < nameList.length; index++) {
        if (form.getValue(idList[index]) == '') {
            emptyInputs++;
            message += (index + 1) + ' - ' + nameList[index] + '.\n';
        }

    }

    return { emptyInputs, message }
}
```
</details>

<details>
<summary>
2. Exemplo de uso no validateForm.js
</summary>

```js
function validateForm(form) {
    var numState = getValue('VKNumState');

    if (numState == 0) {

        // Lista de IDs de inputs da atividade -> numState
        var inputsIdList = ['user_name', 'user_passowrd'];

        // lista de NAMEs de inputs da atividade -> numState
        var inputsNamesList = ['User Name', 'User Password'];

        var { emptyInputs, message } = getEmptyInputs(form, inputsIdList, inputsNamesList);

        if(emptyInputs > 0)
            throw message;
    }

}
```
</details>
    