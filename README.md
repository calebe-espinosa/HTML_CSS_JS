## Código de Gerenciamento de Atividades

Este código é um sistema de gerenciamento de atividades que permite criar, listar, marcar como concluídas e exibir atividades em uma página web. Ele utiliza a biblioteca `dayjs` para manipulação e formatação de datas.

### Funções e Variáveis Principais

#### 1. **`formatador`** 
Esta função recebe uma data e retorna um objeto com a data formatada, incluindo o dia, mês e hora.

- **Parâmetros**:
  - `data`: Uma data a ser formatada.

- **Retorno**:
  - Um objeto com:
    - `dia`: Contendo o dia em formato numérico, curto e longo.
    - `mes`: O nome do mês por extenso.
    - `hora`: A hora no formato "HH:mm".

- **Exemplo de Uso**:
  ```javascript
  const dataFormatada = formatador(new Date());
  ```

#### 2. **`atividade`**
Objeto que representa uma atividade com propriedades:
- `nome`: Nome da atividade.
- `data`: Data e hora da atividade.
- `finalizada`: Status de conclusão da atividade (`true` ou `false`).

#### 3. **`atividades`**
Lista de objetos `atividade`. Armazena as atividades a serem exibidas e manipuladas.

#### 4. **`criarItemDeAtividade`**
Função que cria o item HTML para exibir uma atividade na página.

- **Parâmetros**:
  - `atividade`: Um objeto que representa uma atividade.

- **Retorno**:
  - Uma string contendo o HTML para representar a atividade.

- **Exemplo de Uso**:
  ```javascript
  const itemHtml = criarItemDeAtividade(atividade);
  ```

#### 5. **`atualizarListaDeAtividades`**
Atualiza a lista de atividades exibida na página. Se a lista estiver vazia, exibe uma mensagem informando.

- **Funcionamento**:
  - Limpa o conteúdo da seção HTML.
  - Verifica se a lista de atividades está vazia.
  - Itera sobre as atividades e insere o HTML correspondente na página.

#### 6. **`salvarAtividade`**
Função chamada ao submeter um formulário para salvar uma nova atividade.

- **Parâmetros**:
  - `event`: O evento de submissão do formulário.

- **Funcionamento**:
  - Previne a submissão padrão do formulário.
  - Obtém os dados do formulário.
  - Verifica se a atividade já existe com a mesma data/hora.
  - Adiciona a nova atividade à lista e atualiza a exibição.

#### 7. **`criarDiasSelecao`**
Popula um elemento `<select>` com opções de dias para seleção.

- **Funcionamento**:
  - Define uma lista de dias.
  - Itera sobre os dias, formatando-os para exibição.
  - Atualiza o elemento `<select>` na página com as opções de dias.

#### 8. **`criarHorasSelecao`**
Popula um elemento `<select>` com opções de horários disponíveis.

- **Funcionamento**:
  - Define horários disponíveis das 6h às 22h30.
  - Itera sobre os horários e cria opções de seleção.
  - Atualiza o elemento `<select>` na página com as opções de horários.

#### 9. **`concluirAtividade`**
Marca ou desmarca uma atividade como concluída com base na interação do usuário.

- **Parâmetros**:
  - `event`: O evento de mudança no checkbox.

- **Funcionamento**:
  - Obtém a atividade correspondente ao checkbox.
  - Alterna o status de conclusão (`finalizada`).

### Uso do Código

1. **Formatação de Datas**: A função `formatador` utiliza a biblioteca `dayjs` para formatar datas e horas de maneira amigável.

2. **Listagem de Atividades**: As atividades são listadas e exibidas dinamicamente na página. Cada atividade possui um checkbox para marcar como concluída.

3. **Formulário de Cadastro de Atividades**: Permite adicionar novas atividades, com verificação para evitar conflitos de horários.

4. **Seleção de Dias e Horários**: Popula elementos de seleção (`<select>`) com dias e horários possíveis para facilitar a criação de atividades.

### Exemplos de Estrutura HTML Esperada
A página que utiliza este código deve conter elementos como:
- Uma `<section>` para listar atividades.
- Um formulário com campos para `atividade`, `dia`, e `hora`.
- Elementos `<select>` para seleção de dias e horários.

### Observações
- O código assume que o `dayjs` está disponível globalmente para formatação de datas.
- Certifique-se de ter elementos com os seletores esperados no HTML (`section`, `select[name="dia"]`, etc.).
- A função `concluirAtividade` requer um atributo `onchange` no HTML dos checkboxes para funcionar corretamente.