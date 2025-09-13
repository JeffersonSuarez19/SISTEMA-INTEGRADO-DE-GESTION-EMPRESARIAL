<script setup>
import { ref } from 'vue'

// Datos simulados de supermercado y sucursales
const inventario = ref([
  {
    producto: 'Arroz', stock: 2, minimo: 5, sucursal: 2,
    entrada: '2025-09-10', proveedor: 'Proveedor A', bodega: 'Central', almacenamiento: 'Estante 1', salida: '2025-09-16'
  },
  {
    producto: 'Aceite', stock: 50, minimo: 10, sucursal: 1,
    entrada: '2025-09-09', proveedor: 'Proveedor B', bodega: 'Norte', almacenamiento: 'Estante 2', salida: '2025-09-17'
  },
  {
    producto: 'Leche', stock: 3, minimo: 8, sucursal: 5,
    entrada: '2025-09-08', proveedor: 'Proveedor C', bodega: 'Sur', almacenamiento: 'Refrigerador', salida: '2025-09-15'
  },
  {
    producto: 'Azúcar', stock: 30, minimo: 5, sucursal: 3,
    entrada: '2025-09-07', proveedor: 'Proveedor D', bodega: 'Central', almacenamiento: 'Estante 3', salida: '2025-09-18'
  },
  {
    producto: 'Huevos', stock: 0, minimo: 2, sucursal: 5,
    entrada: '2025-09-06', proveedor: 'Proveedor E', bodega: 'Sur', almacenamiento: 'Refrigerador', salida: '2025-09-14'
  },
  {
    producto: 'Pan', stock: 40, minimo: 10, sucursal: 4,
    entrada: '2025-09-05', proveedor: 'Proveedor F', bodega: 'Norte', almacenamiento: 'Estante 4', salida: '2025-09-19'
  },
  {
    producto: 'Sal', stock: 1, minimo: 5, sucursal: 2,
    entrada: '2025-09-04', proveedor: 'Proveedor G', bodega: 'Central', almacenamiento: 'Estante 5', salida: '2025-09-20'
  },
  {
    producto: 'Frijoles', stock: 15, minimo: 8, sucursal: 1,
    entrada: '2025-09-11', proveedor: 'Proveedor H', bodega: 'Central', almacenamiento: 'Estante 6', salida: '2025-09-21'
  },
  {
    producto: 'Cereal', stock: 25, minimo: 10, sucursal: 3,
    entrada: '2025-09-12', proveedor: 'Proveedor I', bodega: 'Norte', almacenamiento: 'Estante 7', salida: '2025-09-22'
  },
  {
    producto: 'Jugo', stock: 5, minimo: 6, sucursal: 4,
    entrada: '2025-09-13', proveedor: 'Proveedor J', bodega: 'Sur', almacenamiento: 'Refrigerador', salida: '2025-09-23'
  },
  {
    producto: 'Café', stock: 18, minimo: 7, sucursal: 2,
    entrada: '2025-09-14', proveedor: 'Proveedor K', bodega: 'Central', almacenamiento: 'Estante 8', salida: '2025-09-24'
  },
  {
    producto: 'Galletas', stock: 22, minimo: 10, sucursal: 3,
    entrada: '2025-09-15', proveedor: 'Proveedor L', bodega: 'Norte', almacenamiento: 'Estante 9', salida: '2025-09-25'
  },
  {
    producto: 'Atún', stock: 12, minimo: 6, sucursal: 4,
    entrada: '2025-09-16', proveedor: 'Proveedor M', bodega: 'Sur', almacenamiento: 'Estante 10', salida: '2025-09-26'
  },
  {
    producto: 'Tomate', stock: 8, minimo: 5, sucursal: 2,
    entrada: '2025-09-17', proveedor: 'Proveedor N', bodega: 'Central', almacenamiento: 'Estante 11', salida: '2025-09-27'
  },
  {
    producto: 'Queso', stock: 14, minimo: 7, sucursal: 1,
    entrada: '2025-09-18', proveedor: 'Proveedor O', bodega: 'Central', almacenamiento: 'Refrigerador', salida: '2025-09-28'
  },
])

const ventas = ref([
  {
    producto: 'Arroz', cantidad: 10, fecha: '2025-09-10', entrada: '2025-09-10', datos: 'Juan Pérez', cc: '123456789', factura: 'FAC-001', radicado: 'RAD-1001'
  },
  {
    producto: 'Aceite', cantidad: 5, fecha: '2025-09-09', entrada: '2025-09-09', datos: 'Ana Gómez', cc: '987654321', factura: 'FAC-002', radicado: 'RAD-1002'
  },
  {
    producto: 'Leche', cantidad: 8, fecha: '2025-09-08', entrada: '2025-09-08', datos: 'Carlos Ruiz', cc: '456789123', factura: 'FAC-003', radicado: 'RAD-1003'
  },
  {
    producto: 'Frijoles', cantidad: 7, fecha: '2025-09-11', entrada: '2025-09-11', datos: 'Laura Torres', cc: '321654987', factura: 'FAC-004', radicado: 'RAD-1004'
  },
  {
    producto: 'Cereal', cantidad: 12, fecha: '2025-09-12', entrada: '2025-09-12', datos: 'Pedro Martínez', cc: '654987321', factura: 'FAC-005', radicado: 'RAD-1005'
  },
  {
    producto: 'Jugo', cantidad: 3, fecha: '2025-09-13', entrada: '2025-09-13', datos: 'Sofía Ramírez', cc: '789123456', factura: 'FAC-006', radicado: 'RAD-1006'
  },
  {
    producto: 'Café', cantidad: 9, fecha: '2025-09-14', entrada: '2025-09-14', datos: 'Miguel Castro', cc: '852963741', factura: 'FAC-007', radicado: 'RAD-1007'
  },
  {
    producto: 'Galletas', cantidad: 6, fecha: '2025-09-15', entrada: '2025-09-15', datos: 'Andrea López', cc: '963852741', factura: 'FAC-008', radicado: 'RAD-1008'
  },
  {
    producto: 'Atún', cantidad: 4, fecha: '2025-09-16', entrada: '2025-09-16', datos: 'Fernando Díaz', cc: '147258369', factura: 'FAC-009', radicado: 'RAD-1009'
  },
  {
    producto: 'Tomate', cantidad: 11, fecha: '2025-09-17', entrada: '2025-09-17', datos: 'Paola Jiménez', cc: '258369147', factura: 'FAC-010', radicado: 'RAD-1010'
  },
  {
    producto: 'Queso', cantidad: 5, fecha: '2025-09-18', entrada: '2025-09-18', datos: 'Ricardo Gómez', cc: '369147258', factura: 'FAC-011', radicado: 'RAD-1011'
  },
])

const logistica = ref([
  {
    producto: 'Arroz', estado: 'Pendiente', llegada: '2025-09-15', entrada: '2025-09-10', proveedor: 'Proveedor A', mercancia: 'Granos', rutaEntrega: 'Bodega Central → Sucursal 2', salida: '2025-09-16',
    tipoTransporte: 'Camión',
    conductor: 'Luis Torres',
    placa: 'ABC-123',
    observaciones: 'Entrega urgente',
    destinoFinal: 'Sucursal 2',
    costoEnvio: '$50.000'
  },
  {
    producto: 'Huevos', estado: 'En tránsito', llegada: '2025-09-13', entrada: '2025-09-09', proveedor: 'Proveedor B', mercancia: 'Alimentos frescos', rutaEntrega: 'Granja → Sucursal 5', salida: '2025-09-14',
    tipoTransporte: 'Moto',
    conductor: 'Marta Díaz',
    placa: 'XYZ-789',
    observaciones: 'Requiere refrigeración',
    destinoFinal: 'Sucursal 5',
    costoEnvio: '$20.000'
  },
])

const productosDesabastecidos = ref(inventario.value.filter(p => p.stock < p.minimo).length)
const productosExceso = ref(inventario.value.filter(p => p.stock > p.minimo * 3).length)
const totalVentas = ref(ventas.value.reduce((acc, v) => acc + v.cantidad, 0))
const alertas = ref([
  ...inventario.value.filter(p => p.stock < p.minimo).map(p => `Desabastecimiento: ${p.producto} (Sucursal ${p.sucursal})`),
  ...inventario.value.filter(p => p.stock > p.minimo * 3).map(p => `Exceso inventario: ${p.producto} (Sucursal ${p.sucursal})`),
])

// Modal
const showModal = ref(false)
const modalTitle = ref('')
const modalItems = ref([])

function openModal(tipo) {
  if (tipo === 'desabastecidos') {
    modalTitle.value = 'Sucursales desabastecidas';
    modalItems.value = inventario.value.filter(p => p.stock < p.minimo);
    modalType.value = 'desabastecidos';
  } else if (tipo === 'exceso') {
    modalTitle.value = 'Sucursales con exceso de inventario';
    modalItems.value = inventario.value.filter(p => p.stock > p.minimo * 3);
    modalType.value = 'exceso';
  } else if (tipo === 'alerta') {
    modalTitle.value = 'Alertas';
    modalItems.value = inventario.value.filter(p => p.stock < p.minimo).map(p => ({ tipo: 'Desabastecimiento', producto: p.producto, sucursal: p.sucursal }))
      .concat(inventario.value.filter(p => p.stock > p.minimo * 3).map(p => ({ tipo: 'Exceso', producto: p.producto, sucursal: p.sucursal })));
    modalType.value = 'alerta';
  } else if (tipo === 'ventas') {
    modalTitle.value = 'Ventas registradas';
    modalItems.value = ventas.value;
    modalType.value = 'ventas';
  }
  showModal.value = true;
}

const modalType = ref('');
function closeModal() {
  showModal.value = false
}
</script>

<template>
  <div class="dashboard">
    <h1 class="title-gradient">SISTEMA INTEGRADO DE GESTION EMPRESARIAL <span>Cadena de Suministro</span></h1>
    <div class="kpi-container">
      <button class="kpi kpi-red" @click="openModal('desabastecidos')">
        <div class="icon">
          <svg width="32" height="32" viewBox="0 0 24 24">
            <circle cx="12" cy="12" r="10" fill="#e74c3c" /><text x="12" y="16" text-anchor="middle" font-size="16"
              fill="#fff">!</text>
          </svg>
        </div>
        <h2>Desabastecidos</h2>
        <span>{{ productosDesabastecidos }}</span>
      </button>
      <button class="kpi kpi-blue" @click="openModal('exceso')">
        <div class="icon">
          <svg width="32" height="32" viewBox="0 0 24 24">
            <rect x="4" y="4" width="16" height="16" rx="4" fill="#2980b9" /><text x="12" y="16" text-anchor="middle"
              font-size="16" fill="#fff">+</text>
          </svg>
        </div>
        <h2>Exceso Inventario</h2>
        <span>{{ productosExceso }}</span>
      </button>
      <button class="kpi kpi-green" @click="openModal('ventas')">
        <div class="icon">
          <!-- ...SVG... -->
        </div>
        <h2>Total Ventas</h2>
        <span>{{ totalVentas }}</span>
      </button>
      <button class="kpi kpi-orange" @click="openModal('alerta')">
        <div class="icon">
          <svg width="32" height="32" viewBox="0 0 24 24">
            <circle cx="12" cy="12" r="10" fill="#e67e22" /><text x="12" y="16" text-anchor="middle" font-size="16"
              fill="#fff">!</text>
          </svg>
        </div>
        <h2>Alertas</h2>
        <span>{{ alertas.length }}</span>
      </button>
    </div>

    <!-- Modal mejorado con tabla -->
    <div v-if="showModal" class="modal-overlay" @click.self="closeModal">
      <div class="modal">
        <h2>{{ modalTitle }}</h2>
        <div v-if="modalType === 'desabastecidos'">
          <table>
            <thead>
              <tr>
                <th>Sucursal</th>
                <th>Producto</th>
                <th>Stock</th>
                <th>Mínimo</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in modalItems" :key="item.producto + item.sucursal">
                <td>{{ item.sucursal }}</td>
                <td>{{ item.producto }}</td>
                <td>{{ item.stock }}</td>
                <td>{{ item.minimo }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div v-else-if="modalType === 'exceso'">
          <table>
            <thead>
              <tr>
                <th>Sucursal</th>
                <th>Producto</th>
                <th>Stock</th>
                <th>Mínimo</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in modalItems" :key="item.producto + item.sucursal">
                <td>{{ item.sucursal }}</td>
                <td>{{ item.producto }}</td>
                <td>{{ item.stock }}</td>
                <td>{{ item.minimo }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div v-else-if="modalType === 'alerta'">
          <table>
            <thead>
              <tr>
                <th>Tipo</th>
                <th>Producto</th>
                <th>Sucursal</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in modalItems" :key="item.tipo + item.producto + item.sucursal">
                <td>{{ item.tipo }}</td>
                <td>{{ item.producto }}</td>
                <td>{{ item.sucursal }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <div v-else-if="modalType === 'ventas'">
          <table>
            <thead>
              <tr>
                <th>Producto</th>
                <th>Cantidad</th>
                <th>Fecha</th>
                <th>Cliente</th>
                <th>C.C.</th>
                <th>Factura</th>
                <th>Radicado</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="item in modalItems" :key="item.producto + item.fecha + item.datos">
                <td>{{ item.producto }}</td>
                <td>{{ item.cantidad }}</td>
                <td>{{ item.fecha }}</td>
                <td>{{ item.datos }}</td>
                <td>{{ item.cc }}</td>
                <td>{{ item.factura }}</td>
                <td>{{ item.radicado }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        <button class="close-btn" @click="closeModal">Cerrar</button>
      </div>
    </div>

    <div class="section">
      <h3 class="section-title">Inventario</h3>
      <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th>Producto</th>
              <th>Stock</th>
              <th>Mínimo</th>
              <th>Entrada</th>
              <th>Proveedor</th>
              <th>Bodega</th>
              <th>Almacenamiento</th>
              <th>Salida</th>
              <th>Estado</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in inventario" :key="item.producto">
              <td>{{ item.producto }}</td>
              <td :class="{ low: item.stock < item.minimo, high: item.stock > item.minimo * 3 }">{{ item.stock }}</td>
              <td>{{ item.minimo }}</td>
              <td>{{ item.entrada }}</td>
              <td>{{ item.proveedor }}</td>
              <td>{{ item.bodega }}</td>
              <td>{{ item.almacenamiento }}</td>
              <td>{{ item.salida }}</td>
              <td>
                <span v-if="item.stock < item.minimo" class="alert">Desabastecido</span>
                <span v-else-if="item.stock > item.minimo * 3" class="alert">Exceso</span>
                <span v-else class="normal">Normal</span>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <div class="section">
      <h3 class="section-title">Ventas recientes</h3>
      <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th>Producto</th>
              <th>Cantidad</th>
              <th>Fecha</th>
              <th>Entrada</th>
              <th>Datos</th>
              <th>C.C.</th>
              <th>Factura</th>
              <th>Radicado</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="venta in ventas" :key="venta.producto + venta.fecha">
              <td>{{ venta.producto }}</td>
              <td>{{ venta.cantidad }}</td>
              <td>{{ venta.fecha }}</td>
              <td>{{ venta.entrada }}</td>
              <td>{{ venta.datos }}</td>
              <td>{{ venta.cc }}</td>
              <td>{{ venta.factura }}</td>
              <td>{{ venta.radicado }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <div class="section">
      <h3 class="section-title">Logística</h3>
      <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th>Producto</th>
              <th>Estado</th>
              <th>Entrada</th>
              <th>Proveedor</th>
              <th>Mercancía</th>
              <th>Ruta Entrega Final</th>
              <th>Llegada estimada</th>
              <th>Salida</th>
              <th>Tipo Transporte</th>
              <th>Conductor</th>
              <th>Placa</th>
              <th>Observaciones</th>
              <th>Destino Final</th>
              <th>Costo Envío</th>
              <!-- Tracking eliminado -->
            </tr>
          </thead>
          <tbody>
            <tr v-for="log in logistica" :key="log.producto">
              <td>{{ log.producto }}</td>
              <td>{{ log.estado }}</td>
              <td>{{ log.entrada }}</td>
              <td>{{ log.proveedor }}</td>
              <td>{{ log.mercancia }}</td>
              <td>{{ log.rutaEntrega }}</td>
              <td>{{ log.llegada }}</td>
              <td>{{ log.salida }}</td>
              <td>{{ log.tipoTransporte }}</td>
              <td>{{ log.conductor }}</td>
              <td>{{ log.placa }}</td>
              <td>{{ log.observaciones }}</td>
              <td>{{ log.destinoFinal }}</td>
              <td>{{ log.costoEnvio }}</td>
              <!-- Tracking eliminado -->
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <div class="section">
      <h3 class="section-title">Alertas</h3>
      <ul class="alert-list">
        <li v-for="a in alertas" :key="a" class="alert">{{ a }}</li>
      </ul>
    </div>
  </div>
</template>



<style scoped>
.dashboard {
  max-width: 1000px;
  margin: 0 auto;
  padding: 2rem;
  font-family: 'Segoe UI', Arial, sans-serif;
  background: linear-gradient(120deg, #f4f6fb 60%, #eaf6ff 100%);
  border-radius: 18px;
  box-shadow: 0 4px 32px #0002;
}

.title-gradient {
  font-size: 2.2rem;
  font-weight: 700;
  background: linear-gradient(90deg, #2980b9, #e67e22);
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  margin-bottom: 2rem;
  text-align: center;
}

.title-gradient span {
  font-size: 1.2rem;
  font-weight: 400;
  display: block;
  margin-top: 0.5rem;
  background: none;
  -webkit-text-fill-color: initial;
  color: #2c3e50;
}

.kpi-container {
  display: flex;
  gap: 2rem;
  margin-bottom: 2.5rem;
  flex-wrap: wrap;
}

.kpi {
  background: linear-gradient(120deg, #fff 80%, #f4f6fb 100%);
  border-radius: 14px;
  padding: 1.2rem 2rem;
  box-shadow: 0 2px 12px #0001;
  text-align: center;
  flex: 1 1 180px;
  min-width: 180px;
  transition: transform 0.2s;
  position: relative;
  overflow: hidden;
}

.kpi:hover {
  transform: translateY(-4px) scale(1.03);
  box-shadow: 0 6px 24px #0002;
}

.kpi h2 {
  font-size: 1.1rem;
  margin-bottom: 0.5rem;
  color: #2c3e50;
}

.kpi span {
  font-size: 2.2rem;
  font-weight: bold;
  color: #2c3e50;
  display: block;
  margin-top: 0.3rem;
}

.kpi .icon {
  margin-bottom: 0.3rem;
}

.kpi-red {
  border-left: 6px solid #e74c3c;
}

.kpi-blue {
  border-left: 6px solid #2980b9;
}

.kpi-green {
  border-left: 6px solid #27ae60;
}

.kpi-orange {
  border-left: 6px solid #e67e22;
}

.section {
  margin-bottom: 2.5rem;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 2px 8px #0001;
  padding: 1.2rem 1rem;
}

.section-title {
  font-size: 1.2rem;
  font-weight: 600;
  color: #2980b9;
  margin-bottom: 1rem;
}

.table-responsive {
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 1rem;
  background: #f8fafc;
  border-radius: 8px;
  overflow: hidden;
}

th,
td {
  border: 1px solid #e0e0e0;
  padding: 0.6rem 1rem;
  text-align: left;
}

th {
  background: #eaf6ff;
  color: #2980b9;
  font-weight: 600;
}

.low {
  color: #e74c3c;
  font-weight: bold;
  animation: pulse 1s infinite alternate;
}

.high {
  color: #2980b9;
  font-weight: bold;
}

.alert {
  color: #e67e22;
  font-weight: bold;
  animation: pulse 1s infinite alternate;
}

.normal {
  color: #27ae60;
  font-weight: bold;
}

.alert-list {
  list-style: none;
  padding: 0;
}

.alert-list li {
  margin-bottom: 0.5rem;
  padding: 0.5rem 1rem;
  background: #fff7e6;
  border-radius: 6px;
  box-shadow: 0 1px 4px #e67e2211;
}

@keyframes pulse {
  0% {
    opacity: 1;
  }

  100% {
    opacity: 0.7;
  }
}

@media (max-width: 700px) {
  .dashboard {
    padding: 0.5rem;
  }

  .kpi-container {
    flex-direction: column;
    gap: 1rem;
  }

  .section {
    padding: 0.7rem 0.3rem;
  }
}
</style>
