# Aula 06 - Trabalhando com varios inputs
📄 Link de acesso aos <a href="https://cord-delivery-7eb.notion.site/React-Avan-ado-0dd7bebfaf364c1f8544098923b060e5">resumos</a>. 

🖼 Link de <a href="https://glittery-travesseiro-cc25ad.netlify.app/">demonstração</a>.

Para trabalhar com um objeto com múltiplos valores, nós modificamos a função do handler para ler os valores de forma genérica usando a desestruturação de objetos no event para extrairmos o alvo, nome e seu valor.

```jsx
    const handleInputChange = (event) => {
        const { target } = event
        const { name } = target
        const { value } = target

        setInputs({
            ...inputs,
            [name]: value
        })
    }
```

Código na prática.

```jsx
const Form = (props) => {

    const [inputs, setInputs] = useState({
        image: '',
        value: '',
        suit: ''
    })

    const handleInputChange = (event) => {
        const { target } = event
        const { name } = target
        const { value } = target

        setInputs({
            ...inputs,
            [name]: value
        })
    }

    const handleSubmit = (event) => {
        event.preventDefault()
        props.addCard(inputs)
    }

    return (
        <>
            <form onSubmit={handleSubmit}>
                <div>
                    <label htmlFor='image'>Endereço da imagem da carta</label>
                    <input type="text" id="image" name="image" onChange={handleInputChange} value={inputs.image}/>
                </div>
                <div>
                    <label htmlFor='value'>Nome da Carta</label>
                    <input type="text" id="value" name="value" onChange={handleInputChange} value={inputs.name}/>
                </div>
                <div>
                    <label htmlFor='suit'>Naipe da carta</label>
                    <input type="text" id="suit" name="suit" onChange={handleInputChange} value={inputs.suit}/>
                </div>
                <input type="submit" />
            </form>
        </>
    )
}
```