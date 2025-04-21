# 🧠 Atividade: Criando um Contador com React + Vite

Você irá desenvolver um contador simples usando React com Vite, sem necessidade de backend.

---

## 🚀 Criação do projeto

1. Crie o projeto com Vite:

```bash
npm create vite@latest contador-react --template react
cd contador-react
npm install
npm run dev
```

2. Edite o arquivo `src/App.jsx` para implementar seu contador.

---

## ✅ Requisitos

- Mostrar um número que começa em 0.
- Botões: **Incrementar** e **Zerar**.
- Estilo simples com os elementos centralizados.

---

## 💡 Dica: Como funciona o `useState`

- `useState` é usado para armazenar e atualizar o valor do contador.
- Exemplo de uso:

```jsx
const [contador, setContador] = useState(0);
```

- `contador` guarda o valor atual.  
- `setContador` atualiza esse valor.  
- Você pode usar em eventos como `onClick` para modificar o estado.

---

## ⭐ Extras (opcional)

- Botão “Diminuir”.
- Mostrar mensagem especial ao chegar em 10.
