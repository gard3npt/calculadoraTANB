<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora TANB</title>
    <style>
        .tanb-calculator {
            max-width: 100%;
            margin: 15px auto;
            font-family: Arial, sans-serif;
            background: #ffffff;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            overflow: hidden;
        }
        
        .calculator-header {
            background: #29aae1;
            color: white;
            padding: 15px 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .calculator-title {
            margin: 0;
            font-size: 1.4em;
            font-weight: bold;
        }
        
        .add-btn {
            background: #2ecc71;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 4px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s;
        }
        
        .add-btn:hover {
            background: #27ae60;
        }
        
        .calculator-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .calculator-table th {
            background: #3498db;
            color: white;
            padding: 12px 8px;
            text-align: center;
            font-weight: bold;
            border-right: 1px solid #2980b9;
        }
        
        .calculator-table th:last-child {
            border-right: none;
        }
        
        .calculator-table td {
            padding: 10px 8px;
            text-align: center;
            border-bottom: 1px solid #eee;
        }
        
        .calculator-table tr:nth-child(even) {
            background-color: #f8f9fa;
        }
        
        .calculator-table input {
            width: 75%;
            padding: 6px 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            text-align: center;
            font-size: 0.9em;
        }
        
        .calculator-table input:focus {
            border-color: #3498db;
            outline: none;
            box-shadow: 0 0 3px rgba(52, 152, 219, 0.3);
        }
        
        .result-cell {
            background-color: #e8f4fc;
            font-weight: bold;
            color: #2c3e50;
        }
        
        .delete-btn {
            background: #e74c3c;
            color: white;
            border: none;
            padding: 5px 10px;
            border-radius: 3px;
            cursor: pointer;
            font-size: 0.8em;
        }
        
        .delete-btn:hover {
            background: #c0392b;
        }
        
        .instructions {
            background: #f9f9f9;
            padding: 15px 20px;
            border-top: 1px solid #eee;
        }
        
        .instructions h3 {
            margin-top: 0;
            color: #2c3e50;
            font-size: 1.2em;
        }
        
        .instructions ul {
            margin: 10px 0;
            padding-left: 20px;
        }
        
        .instructions li {
            margin-bottom: 8px;
            line-height: 1.4;
        }
        
        .formula {
            background: #e8f4fc;
            padding: 10px 15px;
            border-radius: 4px;
            font-family: monospace;
            margin: 10px 0;
            text-align: center;
            font-weight: bold;
        }
        
        @media (max-width: 768px) {
            .calculator-header {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .add-btn {
                margin-top: 10px;
                align-self: flex-end;
            }
            
            .calculator-table {
                font-size: 0.85em;
            }
            
            .calculator-table th, 
            .calculator-table td {
                padding: 8px 4px;
            }
            
            .calculator-table input {
                width: 65%;
                font-size: 0.8em;
            }
        }
        
        @media (max-width: 480px) {
            .calculator-table {
                display: block;
                overflow-x: auto;
            }
        }
    </style>
</head>
<body>
    <div class="tanb-calculator">
        <div class="calculator-header">
            <h2 class="calculator-title">Calculadora TANB - Simulador</h2>
            <button class="add-btn" onclick="addRow()">+ Adicionar linha de novo Investimento</button>
        </div>
        
        <table class="calculator-table" id="calculator-table">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Montante a Investir (€)</th>
                    <th>% TANB</th>
                    <th>Dias</th>
                    <th>Juros Brutos (€)</th>
                    <th>Retenção (28%)</th>
                    <th>Juros Líquidos (€)</th>
                    <th>Juro Líquido por Dia (€)</th>
                    <th>Ação</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>1</td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="1" step="1" onchange="calculateRow(this)"></td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td><button class="delete-btn" onclick="deleteRow(this)">Eliminar</button></td>
                </tr>
                <tr>
                    <td>2</td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="1" step="1" onchange="calculateRow(this)"></td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td><button class="delete-btn" onclick="deleteRow(this)">Eliminar</button></td>
                </tr>
                <tr>
                    <td>3</td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="1" step="1" onchange="calculateRow(this)"></td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td><button class="delete-btn" onclick="deleteRow(this)">Eliminar</button></td>
                </tr>
                <tr>
                    <td>4</td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
                    <td><input type="number" value="" min="1" step="1" onchange="calculateRow(this)"></td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td class="result-cell">a calcular</td>
                    <td><button class="delete-btn" onclick="deleteRow(this)">Eliminar</button></td>
                </tr>
            </tbody>
        </table>
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<button class="add-btn" onclick="addRow()">+ Adicionar linha de novo Investimento</button>
<br>
<br>
        <div class="instructions">
            <h3>Como usar a Calculadora TANB:</h3>
            <ul>
                <li><strong>Montante a Investir (€):</strong> Insira o valor que pretende investir (em euros);</li>
                <li><strong>% TANB:</strong> Insira a Taxa Anual Nominal Bruta;</li>    
                <li><strong>Dias:</strong> Insira o período do investimento em dias;</li>
                <li><strong>Juros Brutos (€):</strong> Valor total calculado sem a retenção na fonte;</li>
                <li><strong>Retenção na fonte (€):</strong> Em conformidade com a regulamentação fiscal portuguesa, a taxa de retenção é de 28%;</li>
                <li><strong>Juros liquidos (€):</strong> Lucro calculado automaticamente referente aos dias colocados já com retenção na fonte;</li>
                <li><strong>Juro liquido por dia (€):</strong> Lucro calculado automaticamente como valor ganho por dia já com a retenção na fonte.</li>
                <li><strong>Ação:</strong> Eliminar a linha de simulação.</li>
                <br>
             
            </ul>
                </div>

    <script>
        // Calculate values for a specific row
        function calculateRow(inputElement) {
    const row = inputElement.closest('tr');
    
    const montante = parseFloat(row.cells[1].querySelector('input').value) || 0;
    const tanb = parseFloat(row.cells[2].querySelector('input').value) || 0;
    const dias = parseInt(row.cells[3].querySelector('input').value) || 0;
    
    // Juros brutos
    const jurosBrutos = montante * (tanb / 100) * (dias / 360);
    
    // Retenção 28%
    const retencao = jurosBrutos * 0.28;
    
    // Valor líquido a receber
    const valorReceber = jurosBrutos - retencao;
    
    // Ganho por dia (líquido)
    const ganhoDia = valorReceber / dias || 0;
    
    row.cells[4].textContent = jurosBrutos.toFixed(2);
    row.cells[5].textContent = retencao.toFixed(2);
    row.cells[6].textContent = valorReceber.toFixed(2);
    row.cells[7].textContent = ganhoDia.toFixed(4);
        }
        
        // Add a new row to the table
        function addRow() {
            const table = document.getElementById('calculator-table');
            const tbody = table.querySelector('tbody');
            const rowCount = tbody.rows.length;
            
            const newRow = document.createElement('tr');
            newRow.innerHTML = `
    <td>${rowCount + 1}</td>
    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
    <td><input type="number" value="" min="0" step="any" onchange="calculateRow(this)"></td>
    <td><input type="number" value="" min="1" step="1" onchange="calculateRow(this)"></td>
    <td class="result-cell">a calcular</td>
    <td class="result-cell">a calcular</td>
    <td class="result-cell">a calcular</td>
    <td class="result-cell">a calcular</td>
    <td><button class="delete-btn" onclick="deleteRow(this)">Eliminar</button></td>
`;
            
            tbody.appendChild(newRow);
            calculateRow(newRow.cells[1].querySelector('input'));
            updateRowNumbers();
        }
        
        // Delete a row from the table
        function deleteRow(button) {
            const row = button.closest('tr');
            if (document.querySelectorAll('#calculator-table tbody tr').length > 1) {
                row.remove();
                updateRowNumbers();
            } else {
                alert('É necessário ter pelo menos uma linha para simular o calculo TANB!');
            }
        }
        
        // Update row numbers after adding or deleting rows
        function updateRowNumbers() {
            const rows = document.querySelectorAll('#calculator-table tbody tr');
            rows.forEach((row, index) => {
                row.cells[0].textContent = index + 1;
            });
        }
        
        // Initialize calculations for all rows
        window.onload = function() {
            const inputs = document.querySelectorAll('input');
            inputs.forEach(input => {
                calculateRow(input);
            });
        };
    </script>
</body>
