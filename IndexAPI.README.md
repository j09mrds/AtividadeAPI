# AtividadeAPI
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestão de produtos higiênicos para bebês</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" crossorigin="anonymous">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.10.5/font/bootstrap-icons.css">
</head>

<body>
    <nav class="navbar bg-primary">
        <div class="container-fluid">
            <span class="navbar-brand mb-0 h1">Gestão de produtos higiênicos para bebês</span>
        </div>
    </nav>

    <div id="container">
        <div class="m-3 d-flex align-items-center ">
            <label for="search" class="form-label">Buscar:</label>
            <input type="search" class="form-control" id="search" onkeyup="buscarDados()">
            <button class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal"
            style="border-radius: 50%;"><i class="bi bi-plus-lg"></i></button>
        </div>
        <div>
            <table class="table table-striped table-hover">
                <thead>
                    <tr>
                        <th>Produto(Nome)</th>
                        <th>Marca</th>
                        <th>Lote(idDemanda)</th>
                        <th>Preco de revenda</th>
                        <th>Validade(x/x/x)</th>
                        <th>Imagem</th>
                        <th>Editar</th>
                        <th>Excluir</th>
                    </tr>
                </thead>
                <tbody id="dadosProdutos">

                </tbody>
            </table>
        </div>
    </div>
    

    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h1 class="modal-title fs-5" id="exampleModalLabel">Cadastrar no Sistema</h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div class="d-flex align-items-center">
                        <label for="inputNome" class="form-label">Produto(Nome):</label>
                        <input type="text" class="form-control" id="inputNome">
                    </div>
                    <div class="d-flex align-items-center">
                        <label for="inputMarca" class="form-label">Marca:</label>
                        <input type="text" class="form-control" id="inputCategoria">
                    </div>
                    <div clas="d-flex align-items-center">
                        <label for="inputLote">Lote: </label>
                        <input type="text" class="form-control" id="inputPreco">
                    </div>
                    <div class="d-flex align-items-center">
                        <label for="inputPreco" class="form-label">Preço:</label>
                        <input type="text" class="form-control" id="inputPreco">
                    </div>

                    
                    <div class="d-flex align-items-center">
                        <label for="inputTelefone" class="form-label">Validade: (xx/xx/xxxx)</label>
                        <input type="text" class="form-control" id="inputValidade">
                    </div>
                    
                    <div class="d-flex align-items-center" style="width: 550px; aspect-ratio: 16/9; cursor: pointer; color: #797878; border: 2px dashed currentcolor">
                        <label for="inputImagem">
                            <span id="pictureImage">Faça a escolha da imagem do produto: </span>
                        </label>
                        <input type="file" accept="image/*" class="form-control" id="inputImagem" style="display:none;">
                    </div>

                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-primary" onclick="cadastrar()">Salvar</button>
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Excluir dados do sistema -->
    <div class="modal fade" id="modalRemover" tabindex="-1" aria-labelledby="modalRemover" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-body">
                    <div class="d-flex align-items-center justify-content-center">
                        <i class="bi bi-x-octagon-fill text-danger" style="font-size: 5rem;"></i>
                    </div>
                    <div class="d-flex align-items-center justify-content-center">
                        <p class="h4">Tem certeza que deseja excluir do sistema?</p>
                    </div>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-primary" id="remover">Excluir</button>
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Editar informações do sistema-->
    <div class="modal fade" id="editModal" tabindex="-1" aria-labelledby="editModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h1 class="modal-title fs-5" id="editModalLabel">Editar</h1>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div class="d-flex align-items-center">
                        <label for="editNome" class="form-label">Nome:</label>
                        <input type="text" class="form-control" id="editNome">
                    </div>
                    <div class="d-flex align-items-center">
                        <label for="editMarca" class="form-label">Marca:</label>
                        <input type="text" class="form-control" id="editMarca">
                    </div>
                    <div class="d-flex align-items-center">
                        <label for="editLote">Lote:</label>
                        <input type="number" class="form-control" id="editLote">
                    </div>
                    <div class="d-flex align-items-center">
                        <label for="editPreco">Preço:</label>
                        <input type="number" class="form-control" id="editPreco">
                    </div>
                    <div class="d-flex align-items-center">
                        <label for="editValidade">Validade:</label>
                        <input type="number" class="form-control" id="editValidade">
                    </div>
                  
                    <div class="d-flex align-items-center">
                        <label for="editImagem">Imagem</label>
                        <input type="file" accept="image/*" class="form-control" id="editImagem">
                    </div>
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-primary" id="editar">Editar</button>
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancelar</button>
                </div>
            </div>
        </div>
    </div>

    <script src="main.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"
    integrity="sha384-geWF76RCwLtnZ8qwWowPQNguL3RmwHVBC9FhGdlKrxdiJJigb/j/68SIy3Te4Bkz"crossorigin="anonymous"></script>
</body>
</html>
