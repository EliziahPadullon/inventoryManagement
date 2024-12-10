<script>
    import { CirclePlusSolid } from 'flowbite-svelte-icons';

    let products = [
        {
            id: 1,
            name: "Leather back pack",
            category: "Keychain",
            dimensions: "23 × 45 × 23",
            stock: 200,
            price: 100.0,
        },
    ];

    let searchQuery = "";
    let categoryFilter = "All categories";

    function editProduct(id) {
        alert(`Editing product with ID: ${id}`);
    }

    function deleteProduct(id) {
        const confirmation = confirm("Are you sure you want to delete this product?");
        if (confirmation) {
            products = products.filter((product) => product.id !== id);
        }
    }

    function addProduct() {
        alert("Adding new product...");
    }

    function filterProducts() {
        return products.filter((product) =>
            product.name.toLowerCase().includes(searchQuery.toLowerCase())
        );
    }
</script>

<div class="flex flex-col min-h-screen">
    <!-- Header and Main Content -->
    <div class="flex-grow p-4">
        <!-- Search and Filter + Add Product -->
        <div class="flex justify-between items-center mb-4">
            <!-- Add Product Button (Top-left) -->
            <button
                on:click={addProduct}
                class="flex items-center bg-green-500 hover:bg-green-600 text-white font-medium py-2 px-4 rounded"
            >
                <CirclePlusSolid class="w-5 h-5 mr-2" /> Add Product
            </button>

            <!-- Search and Filter (Top-right) -->
            <div class="flex items-center space-x-4">
                <input
                    type="text"
                    placeholder="Search"
                    bind:value={searchQuery}
                    class="w-64 border rounded-lg px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
                <select
                    bind:value={categoryFilter}
                    class="border rounded-lg px-3 py-2 focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                    <option>All categories</option>
                    <option>Keychain</option>
                </select>
            </div>
        </div>

        <!-- Product Table -->
        <div class="relative overflow-x-auto shadow-md sm:rounded-lg">
            <table class="w-full text-sm text-left text-gray-500">
                <thead class="text-xs text-gray-700 uppercase bg-gray-50">
                    <tr>
                        <th scope="col" class="px-6 py-3">Product</th>
                        <th scope="col" class="px-6 py-3">Category</th>
                        <th scope="col" class="px-6 py-3">Stock</th>
                        <th scope="col" class="px-6 py-3">Price</th>
                        <th scope="col" class="px-6 py-3">Actions</th>
                    </tr>
                </thead>
                <tbody>
                    {#each filterProducts() as product}
                        <tr class="bg-white border-b hover:bg-gray-50">
                            <td class="px-6 py-4">
                                <div>
                                    <strong>{product.name}</strong>
                                    <br />
                                    <small>Dimensions: {product.dimensions}</small>
                                </div>
                            </td>
                            <td class="px-6 py-4">{product.category}</td>
                            <td class="px-6 py-4">{product.stock}</td>
                            <td class="px-6 py-4">P{product.price.toFixed(2)}</td>
                            <td class="px-6 py-4 flex space-x-2">
                                <button
                                    on:click={() => editProduct(product.id)}
                                    class="bg-green-500 text-white px-3 py-2 rounded hover:bg-green-600"
                                >
                                    Edit
                                </button>
                                <button
                                    on:click={() => deleteProduct(product.id)}
                                    class="bg-red-500 text-white px-3 py-2 rounded hover:bg-red-600"
                                >
                                    Delete
                                </button>
                            </td>
                        </tr>
                    {/each}
                </tbody>
            </table>
        </div>
    </div>

    <!-- Footer Pagination -->
    <footer class="bg-gray-50 border-t py-4 sticky bottom-0 w-full">
        <div class="flex justify-between items-center max-w-7xl mx-auto px-4">
            <span class="text-sm text-gray-700">Showing 1-10 of 1000</span>
            <nav class="inline-flex space-x-1">
                <button class="px-3 py-1 bg-gray-100 text-gray-600 rounded">1</button>
                <button class="px-3 py-1 bg-gray-100 text-gray-600 rounded">2</button>
                <button class="px-3 py-1 bg-gray-100 text-gray-600 rounded">...</button>
                <button class="px-3 py-1 bg-gray-100 text-gray-600 rounded">100</button>
            </nav>
        </div>
    </footer>
</div>
