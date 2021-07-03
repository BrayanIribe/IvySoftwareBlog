<template>
  <div>
    <main class="page w-100 p-0" style="overflow-x: hidden">
      <div class="bg-white text-dark landing w-100 rounded shadow-sm mb-3">
        <div class="row" style="overflow-y: hidden; margin: 0">
          <div class="col-sm-6 text-center mb-3 middle">
            <div>
              <h1 class="mb-3">Adaptable, simple y seguro</h1>
              <span class="mb-1 d-block"
                >Así es como definimos nuestro sistema estrella.</span
              >
              <span class="mb-4 d-block"
                >Déjanos tu negocio en nuestras manos.</span
              >
              <b-button variant="primary" to="/explicaciones/introducing-pos"
                >Consultar el manual</b-button
              >
            </div>
          </div>
          <div class="col-sm-6 text-left mb-3">
            <img src="/data/assets/tpos.png" style="max-height: 20rem" />
          </div>
        </div>
      </div>
      <div class="row system-features">
        <div
          class="
            col-sm-4
            offset-sm-1
            p-0
            text-center
            mb-3
            bg-white
            border
            rounded
            d-flex
            align-items-start
            justify-content-start
          "
          v-for="(feature, i) of principalFunctions"
          :class="[`text-${feature.variant}`]"
          :style="{ animationDelay: (i + 3) * 500 + 'ms' }"
          :key="'functions' + i"
          style="overflow: hidden; position: relative"
        >
          <div
            class="d-block"
            style="
              width: 0.4rem;
              height: 100%;
              position: relative;
              left: 0;
              top: 0;
            "
            :class="[`bg-${feature.variant}`]"
          ></div>
          <div>
            <div class="d-flex align-items-center p-2">
              <img
                :src="'/data/assets/' + feature.icon + '.svg'"
                class="icon mr-2"
                style="display: none"
                :class="[{ show: true }, `fill-${feature.variant}`]"
              />
              <span class="w-100 d-block title">{{ feature.title }}</span>
            </div>
          </div>
        </div>
      </div>
      <div class="w-100 mb-5" style="min-height: 10rem">
        <div class="container p-3 border bg-white shadow-sm rounded">
          <h2
            class="ml-2 text-left w-100 mb-4 text-primary"
            style="border: none; font-weight: normal"
          >
            Nuestros clientes
          </h2>
          <div
            class="w-100"
            style="position: relative; overflow: hidden; height: 7rem"
          >
            <div
              v-if="customers"
              class="
                i-customers
                d-flex
                align-items-middle
                justify-content-middle
              "
            >
              <div
                v-for="(client, a) of customers"
                :key="`tx$${a}`"
                :class="{
                  'mr-5': a < customers.length - 1 || true,
                  'ml-5': a === 0,
                }"
              >
                <a :href="client.href">
                  <div
                    :style="
                      'background-image: url(' +
                      '/data/assets/clientes/' +
                      client.src +
                      ')'
                    "
                    class="client-image mb-sm-5 mb-md-0"
                  />
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
      <!-- begin system features -->
      <div
        class="row-feature bg-white border shadow-sm mb-5 p-3"
        v-for="(f, i) of features"
        :class="{ 'bg-faded': (i + 1) % 2 == 0 }"
        :key="'feature' + i"
      >
        <div class="row">
          <div
            class="col-sm-5 feature-legend"
            :class="{ 'order-1': i % 2 == 0, 'order-2': i % 2 != 0 }"
          >
            <h2 class="text-primary">{{ f.title }}</h2>
            <p class="mb-1">{{ f.body }}</p>
            <p class="text-muted mb-0" v-if="f.legend">
              <small>{{ f.legend }}</small>
            </p>
          </div>
          <div
            class="col-sm-7 text-center"
            style="height: 15rem; overflow: hidden"
            :class="{ 'order-1': i % 2 != 0, 'order-2': i % 2 == 0 }"
          >
            <template v-if="f.media && f.media.type === 'image'">
              <img :src="f.media.url" :style="f.media.style" />
            </template>
            <template v-else-if="f.media && f.media.type === 'reports'">
              <img
                :src="`/data/assets/report-${i}.png`"
                class="report-img"
                :class="{ animate: i != 0 && i >= hideReport }"
                :style="{ left: i * 3 + 'rem', top: i * 3 + 'rem' }"
                v-for="i of f.media.quant"
                :key="'media_quant_' + i"
              />
            </template>
          </div>
        </div>
      </div>
      <!-- end system features -->
      <footer
        class="
          w-100
          d-block
          bg-white
          text-dark
          shadow-sm
          border
          rounded
          mt-3
          p-3
        "
      >
        <div class="row">
          <div class="col-sm-6 text-left mb-sm-3 mb-md-0" style="opacity: 0.8">
            <p class="mb-1">
              <fa :icon="['fa', 'location-arrow']" fixed-width />&nbsp; Avenida
              Morelos Esq. Poniente #5 88950 Río Bravo (Tamaulipas)
            </p>
            <p class="mb-3">
              <fa :icon="['fa', 'phone']" fixed-width />&nbsp; (899) 934 - 2917
            </p>
            <p class="mb-0">
              Hecho con
              <fa
                :icon="['fa', 'heart']"
                class="text-danger"
                fixed-width
              />&nbsp;por TecPyme.
            </p>
          </div>
          <div class="col-sm-6 text-right mb-sm-3 mb-md-0">
            <img src="/data/assets/tecpyme-ov.png" style="max-height: 5rem" />
          </div>
        </div>
      </footer>
    </main>
  </div>
</template>

<script>
import Customers from "./../customers";

export default {
  data() {
    return {
      transparentScroll: true,
      hideReport: 9999,
      hideReportsInterval: null,
    };
  },
  computed: {
    customers() {
      return Customers;
    },
    features() {
      return [
        {
          title: "Tu venta no se detiene.",
          body: "¿Ocurrió un apagón? ¿Se cayó el servidor? No te preocupes, nuestro potente cliente TecPyme POS está preparado para esa situación.",
          legend:
            "* Para poder hacer uso de esta función se necesita haber hecho apertura de caja primero y haber recibido el paquete de datos. Solo las funciones vitales de ventas del POS estarán disponibles. Devoluciones, cortes o reimpresiones no estarán disponibles durante este lapso hasta que se resuelva la sincronización.",
          media: {
            type: "image",
            url: "/data/assets/offline.png",
          },
        },
        {
          title: "Un sistema, muchos reportes.",
          body: "¿Qué deseas saber? ¿tu venta del día de ayer? ¿como se comportaron las existencias hace una semana? Hay un reporte para cada cosa que quieres. Sin ningún costo adicional.",
          legend:
            "* El sistema además incluye la opción de exportar los datos directamente en formato CSV, de esta forma si una gráfica o reporte no llena tus necesidades podrás trabajarlos a tu gusto.",
          media: {
            type: "reports",
            quant: [0, 1, 2],
          },
        },
        {
          title: "Aplicación móvil.",
          body: "Realiza ajustes de inventario, tablajerías, consulta las estadísticas de ventas en tiempo real. Todo esto desde la palma de tu mano.",
          legend:
            "* Esta aplicación se encuentra aún en desarrollo. Si desea participar en el sistema de pruebas puede hacerlo saber al momento de hacer su contratación.",
          media: {
            type: "image",
            url: "/data/assets/mobile.png",
            style: "height:20rem;",
          },
        },
        {
          title: "Conoce lo que sucede en tu negocio, segundo a segundo.",
          body: "Déjanos la parte difícil. Olvida tener que conectar a cada sucursal y cambiar precios. Actualiza tu lista de productos, haz transferencia de inventarios entre sucursales y consulta el rendimiento de cada una, todo esto en tiempo real..",
          legend:
            "* Para hacer uso de esta característica es necesario contratar TecPyme ADMIN, el cual tiene un costo adicional.",
          media: {
            type: "image",
            url: "/data/assets/admin.png",
          },
        },
      ];
    },
    principalFunctions() {
      return [
        {
          title: "Punto de venta",
          icon: "cart-outline",
          variant: "primary",
        },
        {
          title: "Facturación",
          icon: "document-outline",
          variant: "danger",
        },
        {
          title: "Compras",
          icon: "cube-outline",
          variant: "success",
        },
        {
          title: "Reportes",
          icon: "bar-chart-outline",
          variant: "secondary",
        },
      ];
    },
  },
  methods: {
    handleScroll() {
      const s = document.documentElement.scrollTop;
      this.transparentScroll = s <= 30;
      if (this.hideReport == 9999 && s >= 430) {
        this.hideReports();
      }
    },
    hideReports() {
      if (this.hideReportsInterval) return;
      this.hideReport = 3;
      this.hideReportsInterval = setInterval(() => {
        this.hideReport--;
        if (this.hideReport == 0) {
          clearInterval(this.hideReportsInterval);
        }
      }, 1000);
    },
  },
  created() {
    console.log(this);
    this.$nextTick(() => {
      window.addEventListener("scroll", this.handleScroll);
      setTimeout(() => {
        // this.hideReports();
      }, 2000);
    });
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
};
</script>

<style>
.landing {
  padding: 0 !important;
  margin: 0 !important;
  max-width: none !important;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='80' height='80' viewBox='0 0 80 80'%3E%3Cg fill='%23000000' fill-opacity='0.06'%3E%3Cpath fill-rule='evenodd' d='M11 0l5 20H6l5-20zm42 31a3 3 0 1 0 0-6 3 3 0 0 0 0 6zM0 72h40v4H0v-4zm0-8h31v4H0v-4zm20-16h20v4H20v-4zM0 56h40v4H0v-4zm63-25a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm10 0a3 3 0 1 0 0-6 3 3 0 0 0 0 6zM53 41a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm10 0a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm10 0a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm-30 0a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm-28-8a5 5 0 0 0-10 0h10zm10 0a5 5 0 0 1-10 0h10zM56 5a5 5 0 0 0-10 0h10zm10 0a5 5 0 0 1-10 0h10zm-3 46a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm10 0a3 3 0 1 0 0-6 3 3 0 0 0 0 6zM21 0l5 20H16l5-20zm43 64v-4h-4v4h-4v4h4v4h4v-4h4v-4h-4zM36 13h4v4h-4v-4zm4 4h4v4h-4v-4zm-4 4h4v4h-4v-4zm8-8h4v4h-4v-4z'/%3E%3C/g%3E%3C/svg%3E");
  animation: parallax 20s linear infinite;
  background-size: 15rem;
}

@keyframes parallax {
  0% {
    background-position-x: left;
    background-position-y: top;
  }
  100% {
    background-position-x: right;
    background-position-y: bottom;
  }
}

.landing.move {
  background-position-x: right;
  background-position-y: bottom;
}

.landing-description {
  padding: 1rem;
  padding-top: 6rem;
  padding-bottom: 0rem;
}

.tecpyme-pos-img {
  animation: fadeInUp;
  animation-duration: 1s;
}

.middle {
  display: flex;
  justify-content: center;
  align-items: center;
}

.system-features {
  margin-top: 1rem;
  margin-bottom: 1rem;
  border-bottom: 1px solid #ececec;
}

.system-features .title {
  font-size: 1.3rem;
}

.system-features h3 {
  font-weight: normal;
}

.system-features .icon {
  font-size: 2rem;
}

.icon.show {
  display: inline-block !important;
  width: 1.5rem;
}

.client-image {
  width: 6.5rem;
  height: 6.5rem;
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
  transition: 250ms;
  filter: none;
}

.client-image:hover {
  opacity: 0.7;
}

.logo-footer {
  max-width: 12rem;
  filter: grayscale(1) brightness(1.5);
}

.bg-faded {
  background-color: #efefef;
}

.row-feature {
  padding: 3rem;
  padding-top: 1rem;
  padding-bottom: 0;
}

.row-feature,
.row-feature .row,
.row-feature .col-sm-6 {
  overflow: hidden;
}

.row-feature img {
  max-width: 100%;
}

.feature-legend p {
  font-weight: normal;
}

.feature-legend p.text-muted {
  line-height: 1.2rem;
}

.report-img {
  max-width: 40rem !important;
  position: absolute;
  transition: 1000ms;
}

.report-img.animate {
  top: 100% !important;
}

.i-customers {
  position: absolute;
  top: 0px;
  left: 0px;
  overflow: hidden;
  white-space: nowrap;
  animation: bannermove 10s linear -5s infinite alternate forwards;
  animation-delay: 3s;
}

@keyframes bannermove {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(-10%, 0);
  }
}
</style>