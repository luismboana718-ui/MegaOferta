import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";

export default function App() {
  const [cart, setCart] = useState([]);
  const [search, setSearch] = useState("");

  const products = [
    { id: 1, name: "Sapatilhas", min: 2300, max: 6000, category: "Calçado" },
    { id: 2, name: "T-shirt", min: 300, max: 900, category: "Roupas" },
    { id: 3, name: "Calças jeans", min: 800, max: 3000, category: "Roupas" },
    { id: 4, name: "Calções", min: 500, max: 1800, category: "Roupas" },
    { id: 5, name: "Vestidos", min: 1000, max: 4000, category: "Feminina" },
    { id: 6, name: "Blusas femininas", min: 500, max: 2000, category: "Feminina" },
    { id: 7, name: "Casacos leves", min: 1500, max: 5000, category: "Roupas" },
    { id: 8, name: "Camisas sociais", min: 800, max: 3500, category: "Roupas" },
    { id: 9, name: "Bonés", min: 200, max: 800, category: "Acessórios" },
    { id: 10, name: "Cachecóis", min: 300, max: 1000, category: "Acessórios" },
    { id: 11, name: "Meias", min: 100, max: 400, category: "Acessórios" },
    { id: 12, name: "Roupa interior", min: 150, max: 800, category: "Acessórios" },
    { id: 13, name: "Bolsas femininas", min: 500, max: 3000, category: "Feminina" },
    { id: 14, name: "Mochilas escolares", min: 800, max: 3500, category: "Acessórios" },
    { id: 15, name: "Sapatos formais", min: 1500, max: 5000, category: "Calçado" },
    { id: 16, name: "Chinelos/Sandálias", min: 200, max: 1500, category: "Calçado" },
    { id: 17, name: "Hoodies", min: 1200, max: 3500, category: "Roupas" },
    { id: 18, name: "Saias femininas", min: 600, max: 2500, category: "Feminina" },
    { id: 19, name: "Acessórios (colares/pulseiras)", min: 100, max: 1500, category: "Acessórios" },
    { id: 20, name: "Roupa de segunda mão", min: 50, max: 1500, category: "Roupas" },
  ];

  const getPrice = (product) =>
    Math.round((product.min + product.max) / 2);

  const addToCart = (product) => {
    setCart([...cart, { ...product, price: getPrice(product) }]);
  };

  const removeFromCart = (index) => {
    const newCart = [...cart];
    newCart.splice(index, 1);
    setCart(newCart);
  };

  const total = cart.reduce((sum, item) => sum + item.price, 0);

  const payWithVendusPay = () => {
    const vendusPayLink = `https://SEU-LINK-VENDUSPAY.com/pagar?valor=${total}`;
    window.open(vendusPayLink, "_blank");
  };

  const filteredProducts = products.filter((p) =>
    p.name.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <h1 className="text-3xl font-bold text-center mb-6">
        MegaOferta Loja de Roupas
      </h1>

      <div className="max-w-md mx-auto mb-6">
        <Input
          placeholder="Pesquisar produtos..."
          value={search}
          onChange={(e) => setSearch(e.target.value)}
        />
      </div>

      <div className="grid md:grid-cols-3 gap-6">
        {filteredProducts.map((product) => (
          <Card key={product.id} className="shadow-lg rounded-2xl">
            <CardContent className="p-4">
              <h2 className="font-bold text-lg">{product.name}</h2>
              <p className="text-sm text-gray-500">{product.category}</p>
              <p className="text-green-600 font-semibold mt-1">
                {product.min} - {product.max} MZN
              </p>

              <Button
                className="mt-3 w-full"
                onClick={() => addToCart(product)}
              >
                Adicionar ao Carrinho
              </Button>
            </CardContent>
          </Card>
        ))}
      </div>

      <div className="mt-10 max-w-2xl mx-auto bg-white p-6 rounded-2xl shadow-xl">
        <h2 className="text-xl font-bold mb-4">🛒 Carrinho de Compras</h2>

        {cart.length === 0 && (
          <p className="text-gray-500">O carrinho está vazio</p>
        )}

        {cart.map((item, i) => (
          <div key={i} className="flex justify-between border-b py-2">
            <span>{item.name}</span>
            <div className="flex gap-4">
              <span>{item.price} MZN</span>
              <button
                className="text-red-500"
                onClick={() => removeFromCart(i)}
              >
                Remover
              </button>
            </div>
          </div>
        ))}

        <h3 className="mt-4 text-lg font-bold">Total: {total} MZN</h3>

        <Button
          className="mt-4 w-full bg-black text-white"
          onClick={payWithVendusPay}
        >
          Finalizar Compra com VendusPay
        </Button>
      </div>
    </div>
  );
}
