<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro Autoamtáx</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* Use Inter font */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8; /* Light blue-gray background */
        }
        /* Style for required input feedback */
        .required-field {
            border-color: #f87171; /* Red-400 */
            box-shadow: 0 0 0 2px rgba(248, 113, 113, 0.3);
        }
        /* Style for table cells */
        th, td {
            padding: 10px 14px; /* Increased padding */
            text-align: left;
            border-bottom: 1px solid #e2e8f0; /* Slate-200 */
            vertical-align: middle; /* Align content vertically */
            font-size: 0.875rem; /* text-sm */
        }
        th {
            background-color: #f8fafc; /* Slate-50 */
            font-weight: 600; /* Semibold */
            color: #334155; /* Slate-700 */
            white-space: nowrap; /* Prevent header text wrapping */
        }
        td {
             color: #475569; /* Slate-600 */
        }
        /* Style for buttons */
        button, .button-like {
            transition: all 0.2s ease-in-out;
            cursor: pointer;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            padding: 9px 16px; /* Slightly taller buttons */
            border-radius: 0.375rem; /* rounded-md */
            font-weight: 500; /* Medium */
            box-shadow: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
            border: 1px solid transparent;
        }
        button:hover {
             filter: brightness(95%);
        }
        button:active {
             filter: brightness(90%);
             transform: scale(0.98);
        }
         /* Primary Button */
        .btn-primary {
             background-color: #2563eb; /* Blue-600 */
             color: white;
             border-color: #2563eb;
        }
        .btn-primary:hover {
             background-color: #1d4ed8; /* Blue-700 */
             border-color: #1d4ed8;
        }
         /* Secondary/Export Button */
        .btn-secondary {
             background-color: #ffffff;
             color: #3b82f6; /* Blue-500 */
             border-color: #d1d5db; /* Gray-300 */
        }
        .btn-secondary:hover {
             background-color: #f9fafb; /* Gray-50 */
             border-color: #9ca3af; /* Gray-400 */
        }
         /* Success Button */
        .btn-success {
             background-color: #16a34a; /* Green-600 */
             color: white;
             border-color: #16a34a;
        }
         .btn-success:hover {
             background-color: #15803d; /* Green-700 */
             border-color: #15803d;
        }
        /* Warning Button */
        .btn-warning {
             background-color: #f59e0b; /* Amber-500 */
             color: white;
             border-color: #f59e0b;
        }
        .btn-warning:hover {
             background-color: #d97706; /* Amber-600 */
             border-color: #d97706;
        }
        /* Danger/Delete Button */
        .btn-danger {
             background-color: #ef4444; /* Red-500 */
             color: white;
             border-color: #ef4444;
             padding: 4px 8px; /* Smaller padding for delete */
             font-size: 0.8rem; /* Smaller text */
        }
        .btn-danger:hover {
             background-color: #dc2626; /* Red-600 */
             border-color: #dc2626;
        }
         /* Check Button */
        .btn-check {
            background-color: #22c55e; /* Green-500 */
            color: white;
            padding: 4px 8px;
            font-size: 0.8rem;
            margin-left: 4px;
        }
        .btn-check:hover {
            background-color: #16a34a; /* Green-600 */
        }

        /* Input & Select Styles */
        input, select, textarea {
            min-height: 42px; /* Slightly taller inputs */
            border: 1px solid #d1d5db; /* Gray-300 */
            border-radius: 0.375rem; /* rounded-md */
            padding: 0.5rem 0.75rem;
            width: 100%;
            background-color: #fff;
            transition: border-color 0.2s ease, box-shadow 0.2s ease;
        }
        input:focus, select:focus, textarea:focus {
            outline: 2px solid transparent;
            outline-offset: 2px;
            border-color: #3b82f6; /* Blue-500 focus */
            box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
        }
        select {
            appearance: none; /* Remove default arrow */
            background-image: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' fill='none' viewBox='0 0 20 20'%3e%3cpath stroke='%236b7280' stroke-linecap='round' stroke-linejoin='round' stroke-width='1.5' d='M6 8l4 4 4-4'/%3e%3c/svg%3e");
            background-position: right 0.5rem center;
            background-repeat: no-repeat;
            background-size: 1.5em 1.5em;
            padding-right: 2.5rem;
        }

        /* Responsive table container */
        .table-container {
            overflow-x: auto;
            margin-top: 1.5rem; /* More space */
            border: 1px solid #e2e8f0; /* Slate-200 */
            border-radius: 0.5rem; /* Larger rounding */
            box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.05);
        }
        table {
             min-width: 100%;
             width: 100%;
             border-collapse: collapse;
             background-color: #ffffff;
        }
        /* Card style for sections */
        section {
            background-color: #ffffff;
            border-radius: 0.75rem; /* Larger rounding */
            padding: 1.5rem 2rem; /* More padding */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05), 0 2px 4px -2px rgba(0, 0, 0, 0.05);
            margin-bottom: 2rem; /* More space between sections */
        }
        section h2 {
             color: #1e3a8a; /* Blue-800 */
             border-bottom: 2px solid #e0e7ff; /* Indigo-100 */
             padding-bottom: 0.75rem;
             margin-bottom: 1.5rem;
        }
        section h3 {
             color: #1e40af; /* Blue-700 */
             margin-top: 1.5rem;
        }

        /* Status colors */
        .status-ok { color: #16a34a; font-weight: 500; } /* Green-600 */
        .status-revisar { color: #f59e0b; font-weight: 500; } /* Amber-500 */
        .status-caducado { color: #dc2626; font-weight: 600; } /* Red-600 */
        .status-reponer { color: #ea580c; font-weight: 500; } /* Orange-600 */

        /* Calculator styles */
        #calculator-result, #salary-calculator-result {
            margin-top: 1.5rem;
            padding: 1.25rem;
            background-color: #f5f3ff; /* Violet-50 */
            border: 1px solid #ddd6fe; /* Violet-200 */
            border-radius: 0.5rem;
        }
        #salary-calculator-result p { margin-bottom: 0.5rem; }
        #salary-calculator-result .label { font-weight: 500; color: #5b21b6; } /* Violet-700 */
        #salary-calculator-result .value { font-weight: 600; color: #1e293b; } /* Slate-800 */
        #salary-calculator-result .net-salary { font-size: 1.125rem; color: #166534; } /* Green-800 */

         /* Health Center List Styles */
        #health-centers-list li div {
            transition: box-shadow 0.2s ease, border-color 0.2s ease;
             border: 1px solid #e5e7eb; /* Gray-200 */
        }
         #health-centers-list li div:hover {
            box-shadow: 0 4px 10px -1px rgba(0, 0, 0, 0.1), 0 2px 6px -2px rgba(0, 0, 0, 0.06); /* Enhanced shadow */
             border-color: #a5b4fc; /* Indigo-300 */
        }
        /* General Container */
         .main-container {
             max-width: 80rem; /* Wider max-width */
             margin: 2rem auto;
             padding: 1.5rem;
             background-color: #ffffff;
             border-radius: 0.75rem;
             box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1);
         }
          .main-title {
             color: #1e3a8a; /* Darker blue */
             font-weight: 700; /* Bold */
         }
    </style>
</head>
<body class="bg-blue-50">
    <div class="main-container">
        <h1 class="text-3xl md:text-4xl main-title text-center mb-10">Registro de Actividad - Autoamtáx</h1>

        <section id="shift-section">
            <h2 class="text-2xl font-semibold">Registro de Turno</h2>
            <form id="shift-form" class="grid grid-cols-1 md:grid-cols-3 gap-5 mb-5">
                <div>
                    <label for="start-time" class="block text-sm font-medium text-gray-700 mb-1">Inicio Turno:</label>
                    <input type="datetime-local" id="start-time" name="start-time" required>
                </div>
                <div>
                    <label for="end-time" class="block text-sm font-medium text-gray-700 mb-1">Fin Turno:</label>
                    <input type="datetime-local" id="end-time" name="end-time" required>
                </div>
                <div>
                    <label for="kilometers" class="block text-sm font-medium text-gray-700 mb-1">Kilómetros:</label>
                    <input type="number" id="kilometers" name="kilometers" min="0" step="0.1" required>
                </div>
            </form>
            <button type="button" onclick="saveShift()" class="btn-primary">
                 <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2"> <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" /> </svg>
                 Guardar Turno
            </button>

            <div class="flex justify-between items-center mt-8 mb-2">
                <h3 class="text-xl font-semibold text-gray-700">Turnos Registrados</h3>
                 <div>
                     <label for="month-select" class="text-sm font-medium text-gray-700 mr-2">Ver Mes:</label>
                     <select id="month-select" onchange="renderShifts()" class="w-auto text-sm"></select>
                 </div>
            </div>
            <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Inicio</th>
                            <th>Fin</th>
                            <th>Duración</th>
                            <th>Kilómetros</th>
                            <th>Acción</th>
                        </tr>
                    </thead>
                    <tbody id="shift-list">
                        </tbody>
                </table>
            </div>
             <button type="button" onclick="exportMonthlyShiftsToCSV()" class="btn-secondary mt-4">
                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-4 h-4 mr-1">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M3 16.5v2.25A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75V16.5M16.5 12 12 16.5m0 0L7.5 12m4.5 4.5V3" />
                </svg>
                Exportar Mes Seleccionado (CSV)
            </button>
        </section>

        {/* Salary Calculator Section */}
        <section id="salary-calculator">
             <h2 class="text-2xl font-semibold">Calculadora de Salario Mensual (Estimado)</h2>
             <p class="text-sm text-gray-600 mb-4">Introduce el total de horas trabajadas en el mes para calcular el salario bruto y neto estimado (IRPF fijo: 774 €).</p>
             <div class="grid grid-cols-1 md:grid-cols-3 gap-5 mb-4 items-end">
                  <div>
                     <label for="total-hours" class="block text-sm font-medium text-gray-700 mb-1">Total Horas Mes:</label>
                     <input type="number" id="total-hours" name="total-hours" min="0" step="0.1" placeholder="Ej: 210.5" required>
                  </div>
                  <div>
                     <button type="button" onclick="calculateSalary()" class="btn-success w-full md:w-auto">
                          <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2"> <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 15.75V18m-7.5-6.75h.008v.008H8.25v-.008Zm0 2.25h.008v.008H8.25V13.5Zm0 2.25h.008v.008H8.25v-.008Zm0 2.25h.008v.008H8.25V18Zm2.498-6.75h.007v.008h-.007v-.008Zm0 2.25h.007v.008h-.007V13.5Zm0 2.25h.007v.008h-.007v-.008Zm0 2.25h.007v.008h-.007V18Zm2.504-6.75h.008v.008h-.008v-.008Zm0 2.25h.008v.008h-.008V13.5Zm0 2.25h.008v.008h-.008v-.008Zm0 2.25h.008v.008h-.008V18Zm2.498-6.75h.008v.008h-.008v-.008Zm0 2.25h.008v.008h-.008V13.5ZM8.25 6h7.5v2.25h-7.5V6ZM12 2.25c-1.892 0-3.758.11-5.593.322C5.15 2.74 4.063 3.513 3.54 4.462A14.95 14.95 0 0 0 2.25 8.25c0 4.343 1.412 8.157 3.538 10.928a14.95 14.95 0 0 0 2.66 2.565c1.83.951 3.923.951 5.752 0 1.14-.592 2.18-1.448 2.996-2.565C19.837 16.406 21.75 12.592 21.75 8.25c0-1.96-.59-3.84-1.64-5.465-.493-.948-1.57-1.72-2.808-1.968C15.758 2.36 13.892 2.25 12 2.25Z" /> </svg>
                          Calcular Salario
                     </button>
                  </div>
             </div>
             <div id="salary-calculator-result" class="hidden">
                 {/* Results will be displayed here */}
             </div>
        </section>

        <section id="materials-section">
            <h2 class="text-2xl font-semibold">Gestión de Material y Servicios</h2>
            <form id="material-form" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-5 mb-5">
                <div>
                    <label for="material-name" class="block text-sm font-medium text-gray-700 mb-1">Nombre Material/Servicio:</label>
                    <input type="text" id="material-name" name="material-name" required>
                </div>
                <div>
                    <label for="material-quantity" class="block text-sm font-medium text-gray-700 mb-1">Cantidad:</label>
                    <input type="number" id="material-quantity" name="material-quantity" min="0" required>
                </div>
                <div>
                    <label for="material-expiry" class="block text-sm font-medium text-gray-700 mb-1">Caducidad:</label>
                    <input type="date" id="material-expiry" name="material-expiry">
                </div>
                 <div>
                    <label for="material-status" class="block text-sm font-medium text-gray-700 mb-1">Estado Inicial:</label>
                    <select id="material-status" name="material-status">
                        <option value="OK">OK</option>
                        <option value="Revisar">Revisar</option>
                        <option value="Reponer">Reponer</option>
                        <option value="Caducado">Caducado</option>
                    </select>
                </div>
            </form>
            <button type="button" onclick="addMaterial()" class="btn-success">
                 <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2"> <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" /> </svg>
                 Añadir Material
             </button>

            <h3 class="text-xl font-semibold text-gray-700">Inventario</h3>
             <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Nombre</th>
                            <th>Cantidad</th>
                            <th>Caducidad</th>
                            <th>Estado</th>
                            <th>Últ. Revisión</th>
                            <th>Acciones</th>
                        </tr>
                    </thead>
                    <tbody id="material-list">
                        </tbody>
                </table>
            </div>
             <button type="button" onclick="exportToCSV('materials', 'materiales.csv')" class="btn-secondary mt-4">
                 <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-4 h-4 mr-1">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M3 16.5v2.25A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75V16.5M16.5 12 12 16.5m0 0L7.5 12m4.5 4.5V3" />
                </svg>
                Exportar Material (CSV)
            </button>
        </section>

        <section id="patient-section">
            <h2 class="text-2xl font-semibold">Datos de Paciente</h2>
            <form id="patient-form" class="grid grid-cols-1 md:grid-cols-2 gap-5 mb-5">
                <div>
                    <label for="patient-name" class="block text-sm font-medium text-gray-700 mb-1">Nombre Paciente:</label>
                    <input type="text" id="patient-name" name="patient-name" required>
                </div>
                <div>
                    <label for="patient-number" class="block text-sm font-medium text-gray-700 mb-1">Nº Identificación/Contacto:</label>
                    <input type="text" id="patient-number" name="patient-number">
                </div>
                <div class="md:col-span-2">
                    <label for="patient-info" class="block text-sm font-medium text-gray-700 mb-1">Información Relevante:</label>
                    <textarea id="patient-info" name="patient-info" rows="3"></textarea>
                </div>
            </form>
            <button type="button" onclick="savePatient()" class="btn-warning text-gray-800">
                 <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2"> <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" /> </svg>
                 Guardar Datos Paciente
             </button>

            <h3 class="text-xl font-semibold text-gray-700">Pacientes Registrados</h3>
             <div class="table-container">
                <table>
                    <thead>
                        <tr>
                            <th>Nombre</th>
                            <th>Nº ID/Contacto</th>
                            <th>Información</th>
                            <th>Acción</th>
                        </tr>
                    </thead>
                    <tbody id="patient-list">
                        </tbody>
                </table>
            </div>
             <button type="button" onclick="exportToCSV('patients', 'pacientes.csv')" class="btn-secondary mt-4">
                 <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-4 h-4 mr-1">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M3 16.5v2.25A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75V16.5M16.5 12 12 16.5m0 0L7.5 12m4.5 4.5V3" />
                </svg>
                Exportar Pacientes (CSV)
            </button>
        </section>

        <section id="calculator-section">
            <h2 class="text-2xl font-semibold">Calculadora Estimada Cuota Autónomo</h2>
            <p class="text-sm text-gray-600 mb-4">Introduce tus rendimientos netos mensuales estimados para ver la cuota mínima según los tramos vigentes. Esto es una estimación y no sustituye el cálculo oficial.</p>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-5 mb-4 items-end">
                 <div>
                    <label for="net-income" class="block text-sm font-medium text-gray-700 mb-1">Rendimiento Neto Mensual (€):</label>
                    <input type="number" id="net-income" name="net-income" min="0" step="0.01" placeholder="Ej: 1500">
                 </div>
                 <div>
                    <button type="button" onclick="calculateAutonomoFee()" class="bg-purple-600 hover:bg-purple-700 text-white font-semibold w-full md:w-auto">
                         <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 mr-2"> <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 15.75V18m-7.5-6.75h.008v.008H8.25v-.008Zm0 2.25h.008v.008H8.25V13.5Zm0 2.25h.008v.008H8.25v-.008Zm0 2.25h.008v.008H8.25V18Zm2.498-6.75h.007v.008h-.007v-.008Zm0 2.25h.007v.008h-.007V13.5Zm0 2.25h.007v.008h-.007v-.008Zm0 2.25h.007v.008h-.007V18Zm2.504-6.75h.008v.008h-.008v-.008Zm0 2.25h.008v.008h-.008V13.5Zm0 2.25h.008v.008h-.008v-.008Zm0 2.25h.008v.008h-.008V18Zm2.498-6.75h.008v.008h-.008v-.008Zm0 2.25h.008v.008h-.008V13.5ZM8.25 6h7.5v2.25h-7.5V6ZM12 2.25c-1.892 0-3.758.11-5.593.322C5.15 2.74 4.063 3.513 3.54 4.462A14.95 14.95 0 0 0 2.25 8.25c0 4.343 1.412 8.157 3.538 10.928a14.95 14.95 0 0 0 2.66 2.565c1.83.951 3.923.951 5.752 0 1.14-.592 2.18-1.448 2.996-2.565C19.837 16.406 21.75 12.592 21.75 8.25c0-1.96-.59-3.84-1.64-5.465-.493-.948-1.57-1.72-2.808-1.968C15.758 2.36 13.892 2.25 12 2.25Z" /> </svg>
                         Calcular Cuota Estimada
                    </button>
                 </div>
            </div>
            <div id="calculator-result" class="hidden">
                <p class="font-medium text-gray-800">Resultados de la estimación:</p>
                <p class="text-sm text-gray-700">Base de cotización mínima: <span id="result-base-min" class="font-semibold"></span> €</p>
                <p class="text-sm text-gray-700">Base de cotización máxima: <span id="result-base-max" class="font-semibold"></span> €</p>
                <p class="text-base text-purple-700">Cuota mensual mínima: <span id="result-fee-min" class="font-semibold text-lg"></span> €</p>
                 <p class="text-xs text-gray-500 mt-2">Nota: Cuota basada en los tramos generales proporcionados. La cuota real puede variar.</p>
            </div>
        </section>

         <section id="health-centers-section">
            <h2 class="text-2xl font-semibold">Centros de Salud (Huelva y Provincia - Ejemplo)</h2>
            <p class="text-sm text-gray-600 mb-6">Esta es una lista de ejemplo y puede no ser exhaustiva. Verifica la información antes de usarla.</p>

            <ul id="health-centers-list" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
                {/* Health center list items remain the same */}
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Los Rosales</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> C/ Amadís de Gaula, 4, 21007 Huelva <a href="https://www.google.com/maps/search/?api=1&query=Avenida+Hispano+América,+9,+21001+Huelva8" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959005330" class="text-blue-700 hover:underline">959 00 53 30</a> (Info) / <a href="tel:955545060" class="text-blue-700 hover:underline">955 54 50 60</a> (Citas) </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Huelva-Centro (Casa del Mar)</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> Av. Hispano América, 9, 21001 Huelva <a href="https://www.google.com/maps/search/?api=1&query=Avenida+Hispano+América,+9,+21001+Huelva9" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959650793" class="text-blue-700 hover:underline">959 65 07 93</a> (Info) / <a href="tel:955545060" class="text-blue-700 hover:underline">955 54 50 60</a> (Citas) </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS La Orden</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> Av. de Diego Morón, 1, 21005 Huelva <a href="https://www.google.com/maps/search/?api=1&query=Avenida+de+Diego+Morón,+1,+21005+Huelva0" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959650540" class="text-blue-700 hover:underline">959 65 05 40</a> (Info) / <a href="tel:955545060" class="text-blue-700 hover:underline">955 54 50 60</a> (Citas) </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Isla Chica</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> Plaza Perlita de Huelva, s/n, Huelva <a href="https://www.google.com/maps/search/?api=1&query=Avenida+de+Diego+Morón,+1,+21005+Huelva1" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959650523" class="text-blue-700 hover:underline">959 65 05 23</a> (Info) / <a href="tel:955545060" class="text-blue-700 hover:underline">955 54 50 60</a> (Citas) </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Aljaraque</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> Av. Alcalde José Conceglieri s/n, 21110 Aljaraque <a href="https://www.google.com/maps/search/?api=1&query=Avenida+de+Diego+Morón,+1,+21005+Huelva2" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959011657" class="text-blue-700 hover:underline">959 01 16 57</a> </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Almonte</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> Av. de Ballestares, s/n, 21730 Almonte <a href="https://www.google.com/maps/search/?api=1&query=Avenida+de+Diego+Morón,+1,+21005+Huelva3" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959005057" class="text-blue-700 hover:underline">959 00 50 57</a> / <a href="tel:959439894" class="text-blue-700 hover:underline">959 43 98 94</a> (Citas) </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Lepe</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> Av. de la Romería, s/n, 21440 Lepe (Verificar) <a href="https://www.google.com/maps/search/?api=1&query=Avenida+de+Diego+Morón,+1,+21005+Huelva4" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:955545060" class="text-blue-700 hover:underline">955 54 50 60</a> (Citas SAS) </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Aracena</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> C/ Zalema, s/n, 21200 Aracena <a href="https://www.google.com/maps/search/?api=1&query=Avenida+de+Diego+Morón,+1,+21005+Huelva5" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959129613" class="text-blue-700 hover:underline">959 12 96 13</a> </p> </div> </li>
                 <li class="list-none"> <div class="bg-white p-5 rounded-lg shadow border h-full flex flex-col"> <h3 class="font-semibold text-blue-800 mb-2 text-base">CS Valverde del Camino</h3> <p class="text-sm text-gray-600 mb-1"> <span class="font-medium text-gray-700">Dirección:</span> C/ Dr. Marañón, s/n, 21600 Valverde del Camino <a href="https://www.google.com/maps/search/?api=1&query=Avenida+de+Diego+Morón,+1,+21005+Huelva6" target="_blank" class="text-blue-600 hover:underline ml-1 text-xs font-medium">(Ver mapa)</a> </p> <p class="text-sm text-gray-600"> <span class="font-medium text-gray-700">Teléfono:</span> <a href="tel:959559566" class="text-blue-700 hover:underline">959 55 95 66</a> </p> </div> </li>
            </ul>
        </section>

    </div>

    <script>
        // --- Constants ---
        const NORMAL_HOURS_LIMIT = 189;
        const NORMAL_RATE = 14.2;
        const EXTRA_RATE = 11.5;
        const IRPF_DEDUCTION = 774;

        // --- Initial Data (Pre-populated from image) ---
        const initialMaterials = [
            // IDs adjusted to be potentially unique across sessions
            { id: 1714000000001, name: "Botella Oxigeno Medicinal", quantity: 1, expiry: "2024-12-01", status: "OK", lastChecked: null }, { id: 1714000000002, name: "Mascarilla para Adulto", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000003, name: "Mascarilla para Niño", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000004, name: "Resucitador Adulto (Ambú)", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000005, name: "Resucitador Niño (Ambú)", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000006, name: "Manómetro Control Presión", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000007, name: "Caudalímetro", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000008, name: "Gafas Nasales", quantity: 1, expiry: "2025-10-01", status: "OK", lastChecked: null }, { id: 1714000000009, name: "Bote Humidificador Esterilizado", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000010, name: "Tubuladora Recta Esterilizada", quantity: 1, expiry: "2025-01-01", status: "OK", lastChecked: null }, { id: 1714000000011, name: "Tubuladora Curva Esterilizada", quantity: 1, expiry: "2025-11-01", status: "OK", lastChecked: null }, { id: 1714000000012, name: "Pinza Disección con Dientes Esterilizada", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000013, name: "Algodón", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000014, name: "Esparadrapo de Tela", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000015, name: "Esparadrapo de Papel", quantity: 1, expiry: "2027-07-01", status: "OK", lastChecked: null }, { id: 1714000000016, name: "Vendas Gasa", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000017, name: "Solución Aséptica", quantity: 1, expiry: null, status: "Revisar", lastChecked: null }, { id: 1714000000018, name: "Apósitos 6x6 (Paquete Gasas)", quantity: 10, expiry: "2025-09-01", status: "OK", lastChecked: null }, { id: 1714000000019, name: "Suero para Lavados", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000020, name: "Cánulas Guedel nº 00", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000021, name: "Cánulas Guedel nº 1", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000022, name: "Cánulas Guedel nº 2", quantity: 1, expiry: "2027-03-01", status: "OK", lastChecked: null }, { id: 1714000000023, name: "Cánulas Guedel nº 3", quantity: 1, expiry: "2027-03-01", status: "OK", lastChecked: null }, { id: 1714000000024, name: "Cánulas Guedel nº 4", quantity: 1, expiry: "2027-03-01", status: "OK", lastChecked: null }, { id: 1714000000025, name: "Cánulas Guedel nº 5", quantity: 1, expiry: "2027-03-01", status: "OK", lastChecked: null }, { id: 1714000000026, name: "Desfibrilador", quantity: 1, expiry: null, status: "Revisar", lastChecked: null }, { id: 1714000000027, name: "Parches Marcapasos Adulto", quantity: 1, expiry: "2025-12-01", status: "OK", lastChecked: null }, { id: 1714000000028, name: "Gasas Estériles", quantity: 1, expiry: "2028-05-28", status: "OK", lastChecked: null }, { id: 1714000000029, name: "Compresas", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000030, name: "Kit de Parto", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000031, name: "Paños Verdes Estériles", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000032, name: "Pinzas Umbilicales", quantity: 1, expiry: "2027-06-01", status: "OK", lastChecked: null }, { id: 1714000000033, name: "Tijeras Rectas Estériles", quantity: 1, expiry: null, status: "OK", lastChecked: null }, { id: 1714000000034, name: "Guantes Estériles (S, M, G)", quantity: 3, expiry: "2027-06-01", status: "OK", lastChecked: null },
        ];

        // --- Utility Functions ---
        function getData(key, defaultValue = [], isArray = true) { const data = localStorage.getItem(key); const defaultVal = isArray ? [] : {}; if (data) { try { return JSON.parse(data); } catch (e) { console.error(`Error parsing localStorage key "${key}":`, e); return defaultValue || defaultVal; } } if (key === 'materials' && defaultValue.length > 0 && !localStorage.getItem(key)) { saveData(key, defaultValue); return defaultValue; } return defaultValue || defaultVal; }
        function saveData(key, data) { localStorage.setItem(key, JSON.stringify(data)); }
        function formatDateTime(dateTimeString) { if (!dateTimeString) return 'N/A'; try { const date = new Date(dateTimeString); return date.toLocaleString('es-ES', { day: '2-digit', month: '2-digit', year: 'numeric', hour: '2-digit', minute: '2-digit', hour12: false }); } catch (e) { return dateTimeString; } }
        function formatDate(dateString) { if (!dateString) return 'N/A'; try { const date = new Date(dateString); const offset = date.getTimezoneOffset() * 60000; const adjustedDate = new Date(date.getTime() + offset); return adjustedDate.toLocaleDateString('es-ES', { day: '2-digit', month: '2-digit', year: 'numeric' }); } catch (e) { return dateString; } }
        function getCurrentDate() { const today = new Date(); const year = today.getFullYear(); const month = String(today.getMonth() + 1).padStart(2, '0'); const day = String(today.getDate()).padStart(2, '0'); return `${year}-${month}-${day}`; }
        function getMonthYear(dateString) { if (!dateString) return null; try { const date = new Date(dateString); const year = date.getFullYear(); const month = String(date.getMonth() + 1).padStart(2, '0'); return `${year}-${month}`; } catch (e) { console.error("Error getting month/year from date:", dateString, e); return null; } }
        function validateForm(formId) { const form = document.getElementById(formId); let isValid = true; form.querySelectorAll('[required]').forEach(input => { input.classList.remove('required-field'); if (!input.value.trim()) { isValid = false; input.classList.add('required-field'); } }); return isValid; }
        function calculateDuration(startDateTimeString, endDateTimeString) { if (!startDateTimeString || !endDateTimeString) { return "N/A"; } try { const startDate = new Date(startDateTimeString); const endDate = new Date(endDateTimeString); if (isNaN(startDate) || isNaN(endDate) || endDate < startDate) { return "Inválido"; } const durationMs = endDate - startDate; const totalMinutes = Math.floor(durationMs / (1000 * 60)); const hours = Math.floor(totalMinutes / 60); const minutes = totalMinutes % 60; return `${hours}h ${minutes}m`; } catch (e) { console.error("Error calculating duration:", e); return "Error"; } }

        // --- Shift Functions ---
        function saveShift() { if (!validateForm('shift-form')) { alert('Por favor, completa todos los campos obligatorios del turno.'); return; } const startTimeInput = document.getElementById('start-time'); const endTimeInput = document.getElementById('end-time'); const kilometersInput = document.getElementById('kilometers'); const startTime = startTimeInput.value; const endTime = endTimeInput.value; const kilometers = kilometersInput.value; if (!startTime) { alert('La hora de inicio es obligatoria para determinar el mes.'); startTimeInput.classList.add('required-field'); return; } if (startTime && endTime && new Date(endTime) < new Date(startTime)) { alert('La hora de fin del turno no puede ser anterior a la hora de inicio.'); return; } const monthYear = getMonthYear(startTime); if (!monthYear) { alert("No se pudo determinar el mes a partir de la fecha de inicio."); return; } const allShiftsData = getData('shifts', {}, false); const shiftsForMonth = allShiftsData[monthYear] || []; const newShift = { id: Date.now(), startTime, endTime, kilometers }; shiftsForMonth.push(newShift); shiftsForMonth.sort((a, b) => new Date(a.startTime) - new Date(b.startTime)); allShiftsData[monthYear] = shiftsForMonth; saveData('shifts', allShiftsData); renderShifts(monthYear); document.getElementById('shift-form').reset(); document.querySelectorAll('#shift-form [required]').forEach(input => input.classList.remove('required-field')); }
        function renderShifts(selectMonth = null) { const allShiftsData = getData('shifts', {}, false); const monthSelector = document.getElementById('month-select'); const shiftList = document.getElementById('shift-list'); shiftList.innerHTML = ''; const availableMonths = Object.keys(allShiftsData).sort().reverse(); const currentSelectedValue = monthSelector.value; monthSelector.innerHTML = ''; if (availableMonths.length === 0) { monthSelector.innerHTML = '<option value="">No hay turnos</option>'; monthSelector.disabled = true; } else { monthSelector.disabled = false; availableMonths.forEach(month => { const option = document.createElement('option'); option.value = month; const [year, monthNum] = month.split('-'); const monthName = new Date(year, monthNum - 1).toLocaleString('es-ES', { month: 'long' }); option.textContent = `${monthName.charAt(0).toUpperCase() + monthName.slice(1)} ${year}`; monthSelector.appendChild(option); }); if (selectMonth && availableMonths.includes(selectMonth)) { monthSelector.value = selectMonth; } else if (currentSelectedValue && availableMonths.includes(currentSelectedValue)) { monthSelector.value = currentSelectedValue; } else if (availableMonths.length > 0) { monthSelector.value = availableMonths[0]; } } const selectedMonthKey = monthSelector.value; const shiftsToDisplay = allShiftsData[selectedMonthKey] || []; shiftsToDisplay.forEach(shift => { const row = shiftList.insertRow(); const duration = calculateDuration(shift.startTime, shift.endTime); row.innerHTML = ` <td>${formatDateTime(shift.startTime)}</td> <td>${formatDateTime(shift.endTime)}</td> <td>${duration}</td> <td>${shift.kilometers || 'N/A'}</td> <td class="whitespace-nowrap"><button class="btn-danger" onclick="deleteShift(${shift.id}, '${selectedMonthKey}')">Borrar</button></td> `; }); }
        function deleteShift(id, monthYear) { let allShiftsData = getData('shifts', {}, false); if (!allShiftsData[monthYear]) return; allShiftsData[monthYear] = allShiftsData[monthYear].filter(shift => shift.id !== id); if (allShiftsData[monthYear].length === 0) { delete allShiftsData[monthYear]; } saveData('shifts', allShiftsData); renderShifts(); }

        // --- Salary Calculator Function ---
        function calculateSalary() { const totalHoursInput = document.getElementById('total-hours'); const resultDiv = document.getElementById('salary-calculator-result'); const totalHours = parseFloat(totalHoursInput.value); totalHoursInput.classList.remove('required-field'); if (isNaN(totalHours) || totalHours < 0) { alert("Por favor, introduce un total de horas válido (número positivo)."); totalHoursInput.classList.add('required-field'); resultDiv.classList.add('hidden'); return; } const normalHours = Math.min(totalHours, NORMAL_HOURS_LIMIT); const extraHours = Math.max(0, totalHours - NORMAL_HOURS_LIMIT); const normalPay = normalHours * NORMAL_RATE; const extraPay = extraHours * EXTRA_RATE; const grossSalary = normalPay + extraPay; const netSalary = grossSalary - IRPF_DEDUCTION; const formatCurrency = (amount) => amount.toLocaleString('es-ES', { style: 'currency', currency: 'EUR' }); resultDiv.innerHTML = ` <p><span class="label">Horas Normales (${NORMAL_RATE.toFixed(2)} €/h):</span> <span class="value">${normalHours.toFixed(2)} h</span> = <span class="value">${formatCurrency(normalPay)}</span></p> <p><span class="label">Horas Extra (${EXTRA_RATE.toFixed(2)} €/h):</span> <span class="value">${extraHours.toFixed(2)} h</span> = <span class="value">${formatCurrency(extraPay)}</span></p> <hr class="my-2 border-gray-300"> <p><span class="label">Salario Bruto Total:</span> <span class="value font-bold">${formatCurrency(grossSalary)}</span></p> <p><span class="label">Retención IRPF (Fija):</span> <span class="value text-red-600">-${formatCurrency(IRPF_DEDUCTION)}</span></p> <hr class="my-2 border-gray-300"> <p><span class="label">Salario Neto Estimado:</span> <span class="value font-bold net-salary">${formatCurrency(netSalary)}</span></p> `; resultDiv.classList.remove('hidden'); }

        // --- Material Functions ---
        function addMaterial() { if (!validateForm('material-form')) { alert('Por favor, completa el nombre y la cantidad del material.'); return; } const name = document.getElementById('material-name').value; const quantity = document.getElementById('material-quantity').value; const expiry = document.getElementById('material-expiry').value; const status = document.getElementById('material-status').value; const materials = getData('materials', initialMaterials, true); const newMaterial = { id: Date.now(), name, quantity, expiry, status: expiry && new Date(expiry) < new Date().setHours(0,0,0,0) ? 'Caducado' : status, lastChecked: null }; materials.push(newMaterial); saveData('materials', materials); renderMaterials(); document.getElementById('material-form').reset(); document.querySelectorAll('#material-form [required]').forEach(input => input.classList.remove('required-field')); }
        function checkMaterial(id) { let materials = getData('materials', initialMaterials, true); const today = getCurrentDate(); materials = materials.map(material => { if (material.id === id) { const isExpired = material.expiry && new Date(material.expiry) < new Date().setHours(0,0,0,0); const newStatus = isExpired ? 'Caducado' : 'OK'; return { ...material, lastChecked: today, status: newStatus }; } return material; }); saveData('materials', materials); renderMaterials(); }
        function updateMaterialStatus(id, newStatus) { let materials = getData('materials', initialMaterials, true); materials = materials.map(material => { if (material.id === id) { const isExpired = material.expiry && new Date(material.expiry) < new Date().setHours(0,0,0,0); return { ...material, status: isExpired ? 'Caducado' : newStatus }; } return material; }); saveData('materials', materials); renderMaterials(); }
        function renderMaterials() { const materials = getData('materials', initialMaterials, true); const list = document.getElementById('material-list'); list.innerHTML = ''; const today = new Date().setHours(0, 0, 0, 0); materials.forEach(material => { const row = list.insertRow(); let isExpired = material.expiry && new Date(material.expiry) < today; let currentStatus = material.status; if (isExpired && currentStatus !== 'Caducado') { currentStatus = 'Caducado'; } let statusClass = ''; switch(currentStatus) { case 'OK': statusClass = 'status-ok'; break; case 'Revisar': statusClass = 'status-revisar'; break; case 'Caducado': statusClass = 'status-caducado'; break; case 'Reponer': statusClass = 'status-reponer'; break; default: statusClass = ''; } const expiryDateFormatted = formatDate(material.expiry); const expiryCellClass = isExpired ? 'text-red-600 font-semibold' : ''; row.innerHTML = ` <td>${material.name}</td> <td>${material.quantity}</td> <td class="${expiryCellClass}">${expiryDateFormatted}</td> <td> <select class="text-xs p-1 border-gray-300 rounded w-full bg-white" onchange="updateMaterialStatus(${material.id}, this.value)" title="Cambiar estado"> <option value="OK" ${currentStatus === 'OK' ? 'selected' : ''}>OK</option> <option value="Revisar" ${currentStatus === 'Revisar' ? 'selected' : ''}>Revisar</option> <option value="Reponer" ${currentStatus === 'Reponer' ? 'selected' : ''}>Reponer</option> <option value="Caducado" ${currentStatus === 'Caducado' ? 'selected' : ''} ${!isExpired ? 'disabled' : ''}>Caducado</option> </select> </td> <td>${formatDate(material.lastChecked)}</td> <td class="flex items-center space-x-1 whitespace-nowrap"> <button class="btn-check" onclick="checkMaterial(${material.id})" title="Marcar como revisado hoy"> <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2.5" stroke="currentColor" class="w-3 h-3"> <path stroke-linecap="round" stroke-linejoin="round" d="m4.5 12.75 6 6 9-13.5" /> </svg> </button> <button class="btn-danger" onclick="deleteMaterial(${material.id})" title="Borrar material">Borrar</button> </td> `; }); }
        function deleteMaterial(id) { let materials = getData('materials', initialMaterials, true); materials = materials.filter(material => material.id !== id); saveData('materials', materials); renderMaterials(); }

        // --- Patient Functions ---
        function savePatient() { if (!validateForm('patient-form')) { alert('Por favor, completa el nombre del paciente.'); return; } const name = document.getElementById('patient-name').value; const number = document.getElementById('patient-number').value; const info = document.getElementById('patient-info').value; const patients = getData('patients', [], true); const newPatient = { id: Date.now(), name, number, info }; patients.push(newPatient); saveData('patients', patients); renderPatients(); document.getElementById('patient-form').reset(); document.querySelectorAll('#patient-form [required]').forEach(input => input.classList.remove('required-field')); }
        function renderPatients() { const patients = getData('patients', [], true); const list = document.getElementById('patient-list'); list.innerHTML = ''; patients.forEach(patient => { const row = list.insertRow(); const shortInfo = patient.info.length > 50 ? patient.info.substring(0, 50) + '...' : patient.info; row.innerHTML = ` <td>${patient.name}</td> <td>${patient.number || 'N/A'}</td> <td title="${patient.info}">${shortInfo || 'N/A'}</td> <td><button class="btn-danger" onclick="deletePatient(${patient.id})">Borrar</button></td> `; }); }
        function deletePatient(id) { let patients = getData('patients', [], true); patients = patients.filter(patient => patient.id !== id); saveData('patients', patients); renderPatients(); }

        // --- Autónomo Calculator Functions --- (UPDATED BRACKETS)
        function calculateAutonomoFee() {
            const incomeInput = document.getElementById('net-income');
            const resultDiv = document.getElementById('calculator-result');
            const income = parseFloat(incomeInput.value);

            if (isNaN(income) || income < 0) {
                alert("Por favor, introduce un rendimiento neto mensual válido (número positivo).");
                resultDiv.classList.add('hidden');
                incomeInput.classList.add('required-field');
                return;
            }
             incomeInput.classList.remove('required-field');

            // Updated Brackets based on user input
            const brackets = [
                // Assuming lower brackets exist, add them if needed. Starting from G-1 provided.
                // Example lower brackets (replace with actual if available):
                 { minIncome: 0, maxIncome: 670, minBase: 735.29, maxBase: 751.63, fee: 230 }, // Example Reduced Bracket 1
                 { minIncome: 670.01, maxIncome: 900, minBase: 751.64, maxBase: 900, fee: 260 }, // Example Reduced Bracket 2
                 { minIncome: 900.01, maxIncome: 1166.70, minBase: 849.67, maxBase: 1166.70, fee: 275 }, // Example Reduced Bracket 3
                // General Brackets provided by user
                { minIncome: 1166.70, maxIncome: 1300, minBase: 950.98, maxBase: 1300, fee: 280 }, // G-1 (Note: minIncome adjusted slightly to avoid gap)
                { minIncome: 1300.01, maxIncome: 1500, minBase: 960.78, maxBase: 1500, fee: 294 }, // G-2
                { minIncome: 1500.01, maxIncome: 1700, minBase: 960.78, maxBase: 1700, fee: 294 }, // G-3
                { minIncome: 1700.01, maxIncome: 1850, minBase: 1143.79, maxBase: 1850, fee: 350 }, // G-4
                { minIncome: 1850.01, maxIncome: 2030, minBase: 1209.15, maxBase: 2030, fee: 370 }, // G-5
                { minIncome: 2030.01, maxIncome: 2330, minBase: 1274.51, maxBase: 2330, fee: 390 }, // G-6
                { minIncome: 2330.01, maxIncome: 2760, minBase: 1356.21, maxBase: 2760, fee: 415 }, // G-7
                { minIncome: 2760.01, maxIncome: 3190, minBase: 1437.91, maxBase: 3190, fee: 465 }, // G-8
                { minIncome: 3190.01, maxIncome: 3620, minBase: 1519.61, maxBase: 3620, fee: 490 }, // G-9
                { minIncome: 3620.01, maxIncome: 4050, minBase: 1601.31, maxBase: 4050, fee: 515 }, // G-10
                { minIncome: 4050.01, maxIncome: 6000, minBase: 1732.03, maxBase: 4909.50, fee: 530 }, // G-11
                { minIncome: 6000.01, maxIncome: Infinity, minBase: 1928.10, maxBase: 4909.50, fee: 590 }  // G-12
            ];

            let selectedBracket = brackets.find(b => income > b.minIncome && income <= b.maxIncome);

             // Handle the lowest bracket explicitly if income is within its range or lower
             if (income <= brackets[0].maxIncome) {
                 selectedBracket = brackets[0];
             }
            // Handle the highest bracket explicitly if income exceeds the second to last maxIncome
             else if (income > brackets[brackets.length - 2].maxIncome) {
                 selectedBracket = brackets[brackets.length - 1];
             }


             if (selectedBracket) {
                // Use the provided 'fee' directly as the minimum monthly fee
                const estimatedFee = selectedBracket.fee;

                document.getElementById('result-base-min').textContent = selectedBracket.minBase.toFixed(2);
                document.getElementById('result-base-max').textContent = selectedBracket.maxBase.toFixed(2);
                // Display the exact minimum fee from the table
                document.getElementById('result-fee-min').textContent = estimatedFee.toFixed(2);
                resultDiv.classList.remove('hidden');
            } else {
                 // This case should ideally not happen with the updated logic, but keep as fallback
                 alert("No se encontró un tramo para el rendimiento introducido. Verifica el valor.");
                 resultDiv.classList.add('hidden');
            }
        }

        // --- Export to CSV Functions ---
        function exportToCSV(dataKey, filename) { const isMaterials = dataKey === 'materials'; const data = getData(dataKey, isMaterials ? initialMaterials : [], true); if (data.length === 0) { alert(`No hay datos en la sección "${dataKey}" para exportar.`); return; } let headers = []; let rows = []; if (isMaterials) { headers = ['ID', 'Nombre', 'Cantidad', 'Caducidad', 'Estado', 'Última Revisión']; rows = data.map(item => [ item.id, item.name, item.quantity, formatDate(item.expiry), item.status, formatDate(item.lastChecked) ]); } else if (dataKey === 'patients') { headers = ['ID', 'Nombre Paciente', 'Nº ID/Contacto', 'Información Relevante']; rows = data.map(item => [ item.id, item.name, item.number, `"${String(item.info || '').replace(/"/g, '""')}"` ]); } else { console.error("Use exportMonthlyShiftsToCSV for shifts. Key not recognized for general export:", dataKey); return; } triggerCSVDownload(headers, rows, filename); }
        function exportMonthlyShiftsToCSV() { const monthSelector = document.getElementById('month-select'); const selectedMonth = monthSelector.value; if (!selectedMonth) { alert("Por favor, selecciona un mes para exportar."); return; } const allShiftsData = getData('shifts', {}, false); const shiftsForMonth = allShiftsData[selectedMonth] || []; if (shiftsForMonth.length === 0) { alert(`No hay turnos registrados para el mes ${selectedMonth} para exportar.`); return; } const headers = ['ID', 'Inicio Turno', 'Fin Turno', 'Duración', 'Kilómetros']; const rows = shiftsForMonth.map(item => [ item.id, formatDateTime(item.startTime), formatDateTime(item.endTime), calculateDuration(item.startTime, item.endTime), item.kilometers ]); const filename = `turnos_${selectedMonth}.csv`; triggerCSVDownload(headers, rows, filename); }
        function triggerCSVDownload(headers, rows, filename) { let csvContent = "data:text/csv;charset=utf-8,"; csvContent += headers.join(";") + "\r\n"; rows.forEach(rowArray => { let row = rowArray.map(field => { let stringField = field === null || typeof field === 'undefined' ? '' : String(field); if (stringField.includes(';') || stringField.includes(',') || stringField.includes('\n') || stringField.includes('"')) { stringField = `"${stringField.replace(/"/g, '""')}"`; } return stringField; }).join(";"); csvContent += row + "\r\n"; }); const encodedUri = encodeURI(csvContent); const link = document.createElement("a"); link.setAttribute("href", encodedUri); link.setAttribute("download", filename); document.body.appendChild(link); link.click(); document.body.removeChild(link); }

        // --- Initial Load ---
        window.onload = () => {
            renderShifts(); // Will also populate month selector
            renderMaterials();
            renderPatients();
        };
    </script>
</body>
</html>
