<!-- src/components/Sidebar.vue -->
<template>
  <nav :class="{ 'sidebar': true, 'open': isOpen }">
    <button class="menu-toggle" @click="toggleSidebar" aria-label="Toggle menu">
      <i :class="isOpen ? 'fas fa-times' : 'fas fa-bars'"></i>
    </button>
    <ul>
      <li><router-link to="/agenda/tasks"><i class="fas fa-check"></i> Tareas y Eventos</router-link></li>
      <li><router-link to="/agenda/notifications"><i class="fas fa-bell"></i> Notificaciones</router-link></li>
      <li><router-link to="/agenda/ai-assistant"><i class="fas fa-robot"></i> Asistente IA</router-link></li>
      <li><router-link to="/"><i class="fas fa-cog"></i> Configuración</router-link></li>
    </ul>
  </nav>
</template>

<script>
export default {
  data() {
    return { isOpen: false };
  },
  methods: {
    toggleSidebar() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scoped>
.sidebar {
  width: 250px;
  background: #FFFFFF;
  border-right: 1px solid #E0E0E0;
  padding: 16px;
  position: fixed;
  height: 100%;
  transition: transform 0.3s ease;
}
.sidebar ul { list-style: none; padding: 0; }
.sidebar li { margin: 8px 0; }
.sidebar a {
  color: var(--text-primary);
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px;
  border-radius: 4px;
}
.sidebar a:hover { background: var(--secondary); }
.menu-toggle {
  display: none;
  background: none;
  border: none;
  font-size: 24px;
  position: absolute;
  top: 16px;
  left: 16px;
}
@media (max-width: 768px) {
  .sidebar {
    transform: translateX(-100%);
    width: 200px;
  }
  .sidebar.open {
    transform: translateX(0);
  }
  .menu-toggle { display: block; }
}
</style>