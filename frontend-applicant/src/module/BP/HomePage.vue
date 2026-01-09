<template>
  <div class="app-container">
    <nav class="navbar">
      <div class="logo-section">
        <div class="logo-text">
          <p class="main-title">CONSTRUCTION PERMIT</p>
          <h1 class="sub-title">MANAGEMENT SYSTEM</h1>
        </div>
      </div>
      <div class="user-profile-wrapper">
        <button class="profile-btn" @click="toggleDropdown">
          <div class="avatar">JR</div>
          <div class="user-info">
            <span class="user-name">Jose Rizal</span>
            <span class="user-role">Architect</span>
          </div>
          <span class="dropdown-icon">▼</span>
        </button>
        <div v-if="showDropdown" class="dropdown-menu">
          <div class="dropdown-header">
            <div class="dropdown-name">Jose Rizal</div>
            <div class="dropdown-subtitle">Architectural</div>
          </div>
          <div class="dropdown-divider"></div>
          <div class="dropdown-item logout" @click.stop="logout">
            <span class="logout-icon">↪</span>
            <span>Log Out</span>
          </div>
        </div>
      </div>
    </nav>

    <header class="hero">
      <div class="hero-content">
        <h2 class="welcome-title">Welcome to the One-Stop Shop System</h2>
        <p class="hero-description">
          The <strong>Construction Permit Management System</strong> is a
          comprehensive digital platform designed to streamline and simplify the
          process of <strong>building permit application</strong> process. Our
          <strong>one-stop shop system</strong> provides citizens, contractors,
          and developers with convenient access to essential services including
          <strong>building permit applications</strong>,
          <strong>occupancy permit processing</strong>, and
          <strong>compliance monitoring</strong>. By centralizing permit-related
          services in one efficient online portal, we eliminate the need for
          multiple office visits, reduce processing time, and ensure
          transparency throughout the entire permit lifecycle. Our system is
          committed to delivering fast, reliable, and user-friendly services
          that support safe and compliant construction practices in our
          community.
        </p>
      </div>
    </header>

    <section class="services-section">
      <div class="section-header">
        <h2 class="section-title">ONE STOP SHOP SERVICES</h2>
      </div>

      <div class="services-grid">
        <div
          v-for="service in services"
          :key="service.title"
          class="service-card"
        >
          <div
            class="service-icon"
            :style="{ backgroundColor: service.iconBg }"
          >
            <span class="icon-text">{{ service.icon }}</span>
          </div>
          <div class="service-body">
            <h3 class="service-name">{{ service.title }}</h3>
            <p class="service-desc">{{ service.description }}</p>
            <button class="apply-now-btn">Apply Now</button>
          </div>
        </div>
      </div>
    </section>

    <section class="requirements-section">
      <div class="section-header">
        <h2 class="section-title">Requirements & Documentation</h2>
      </div>
      <div class="requirements-grid">
        <div
          v-for="list in requirementLists"
          :key="list.category"
          class="requirement-card"
        >
          <div
            class="requirement-icon"
            :style="{ backgroundColor: list.iconBg }"
          >
            <span class="icon-text">{{ list.icon }}</span>
          </div>
          <h3 class="category-title">{{ list.category }}</h3>
          <ul class="item-list">
            <li v-for="item in list.items" :key="item" class="requirement-item">
              <span class="check-icon">✓</span>
              {{ item }}
            </li>
          </ul>
        </div>
      </div>
    </section>

    <footer class="footer">
      <p>© 2026 Construction Permit Management System. All rights reserved.</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from "vue";

const applicationNumber = ref("BP-2026-000001");
const showDropdown = ref(false);

const toggleDropdown = () => {
  showDropdown.value = !showDropdown.value;
};

const logout = () => {
  console.log("Logging out...");
  // Add your logout logic here
  // For example: router.push('/login') or clear session
  showDropdown.value = false;
};

// Close dropdown when clicking outside
if (typeof window !== "undefined") {
  window.addEventListener("click", (e) => {
    if (!e.target.closest(".user-profile-wrapper")) {
      showDropdown.value = false;
    }
  });
}

const services = [
  {
    title: "Building Permit Application",
    description:
      "Submit and track your building permit applications online. Our streamlined process ensures quick review and approval for your construction projects.",
    icon: "📄",
    iconBg: "#2563eb",
  },
  {
    title: "Occupancy Permit Application",
    description:
      "Apply for occupancy permits with ease. Get your property certified for safe occupancy with our efficient digital application system.",
    icon: "🏠",
    iconBg: "#16a34a",
  },
  {
    title: "Compliance Monitoring",
    description:
      "Monitor and maintain compliance with building codes and regulations. Stay updated on inspection schedules and compliance requirements.",
    icon: "🛡️",
    iconBg: "#dc2626",
  },
];

const requirementLists = [
  {
    category: "Requirements for Applying Building Permit",
    icon: "📄",
    iconBg: "#2563eb",
    items: [
      "Completed application form with notarized signature",
      "Certified true copy of Transfer Certificate of Title (TCT) or Tax Declaration",
      "Complete architectural plans and specifications signed by licensed architect",
      "Structural plans signed and sealed by licensed civil/structural engineer",
      "Electrical plans signed and sealed by licensed electrical engineer",
      "Plumbing and sanitary plans signed by licensed master plumber",
      "Mechanical plans (if applicable) signed by licensed mechanical engineer",
      "Fire safety evaluation clearance from Bureau of Fire Protection",
      "Barangay clearance and locational clearance",
      "Environmental compliance certificate (for projects requiring ECC)",
    ],
  },
  {
    category: "Requirements for Occupancy Permit",
    icon: "🏠",
    iconBg: "#16a34a",
    items: [
      "Approved building permit and complete as-built plans",
      "Certificate of completion signed by licensed professionals",
      "Final inspection report from building official",
      "Fire safety inspection certificate from Bureau of Fire Protection",
      "Electrical safety inspection certificate",
      "Plumbing and sanitary inspection clearance",
      "Structural integrity certification from licensed engineer",
      "Proof of payment of all applicable fees and taxes",
      "Affidavit of undertaking for completion of minor deficiencies (if any)",
      "Environmental compliance monitoring report (if required)",
    ],
  },
  {
    category: "Compliance Monitoring Requirements",
    icon: "🛡️",
    iconBg: "#dc2626",
    items: [
      "Valid building permit and occupancy permit documents",
      "Regular submission of progress reports during construction",
      "Compliance with approved architectural and engineering plans",
      "Adherence to National Building Code and local ordinances",
      "Proper waste management and environmental protection measures",
      "Safety protocols and signage at construction site",
      "Valid insurance coverage for workers and third-party liability",
      "Regular inspection schedules and access for building officials",
      "Documentation of all changes or deviations from approved plans",
      "Timely renewal of permits and clearances as required",
    ],
  },
];
</script>

<style scoped>
/* Layout Resets */
.app-container {
  font-family: "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  color: #333;
  margin: 0;
  padding: 0;
  background-color: #f9f9f9;
}

/* Navbar */
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 50px;
  background: white;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
  height: 88px;
}

.logo-section {
  display: flex;
  align-items: center;
}

.logo-text {
  display: flex;
  flex-direction: column;
  line-height: 1.2;
}

.main-title {
  font-size: 14px;
  font-weight: 400;
  color: black;
  margin: 0;
  letter-spacing: 0.5px;
}

.sub-title {
  font-size: 18px;
  font-weight: 700;
  color: black;
  margin: 0;
  letter-spacing: 0.5px;
}

.user-profile-wrapper {
  position: relative;
  display: flex;
  align-items: center;
}

.profile-btn {
  display: flex;
  align-items: center;
  gap: 8px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 6px 12px;
  border-radius: 6px;
  transition: background-color 0.2s;
}

.profile-btn:hover {
  background-color: #f5f5f5;
}

.avatar {
  width: 32px;
  height: 32px;
  background-color: #1565c0;
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 10px;
}

.user-info {
  display: flex;
  flex-direction: column;
  text-align: left;
}

.user-name {
  font-size: 12px;
  font-weight: bold;
  color: #555;
  white-space: nowrap;
  line-height: 1.2;
}

.user-role {
  font-size: 12px;
  font-weight: 500;
  color: #888;
  white-space: nowrap;
  line-height: 1.2;
}

.dropdown-icon {
  font-size: 10px;
  color: #666;
  margin-left: 4px;
}

.dropdown-menu {
  position: absolute;
  top: calc(100% + 4px);
  right: 0;
  background: white;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
  min-width: 200px;
  z-index: 1000;
  overflow: hidden;
}

.dropdown-header {
  padding: 12px 16px;
}

.dropdown-name {
  font-size: 14px;
  font-weight: 700;
  color: #222;
}

.dropdown-subtitle {
  font-size: 12px;
  color: #666;
}

.dropdown-divider {
  height: 1px;
  background-color: #e0e0e0;
  margin: 4px 0;
}

.dropdown-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px 16px;
  cursor: pointer;
  transition: background-color 0.2s;
  font-size: 14px;
}

.dropdown-item.logout {
  color: #c62828;
}

.dropdown-item:hover {
  background-color: #f5f5f5;
}

.logout-icon {
  font-size: 16px;
}

/* Hero Section */
.hero {
  background: linear-gradient(135deg, #e0f2fe 0%, #f0f9ff 100%);
  padding: 80px 50px;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

.welcome-title {
  font-size: 36px;
  line-height: 1.3;
  margin-bottom: 30px;
  font-weight: 700;
  color: #1e293b;
}

.hero-description {
  font-size: 16px;
  line-height: 1.8;
  color: #475569;
  max-width: 1000px;
  margin: 0 auto;
  text-align: justify;
}

/* Services */
.services-section {
  padding: 80px 50px;
  max-width: 1200px;
  margin: 0 auto;
  background: white;
}

.section-header {
  text-align: center;
  margin-bottom: 60px;
}

.section-title {
  color: #1e293b;
  font-size: 32px;
  font-weight: 700;
  margin-bottom: 10px;
  letter-spacing: 1px;
}

.section-subtitle {
  color: #64748b;
  font-size: 16px;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 40px;
}

.service-card {
  background: white;
  border-radius: 16px;
  border: 1px solid #e2e8f0;
  padding: 45px 35px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  transition: all 0.3s ease;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
}

.service-card:hover {
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
  transform: translateY(-3px);
}

.service-icon {
  width: 70px;
  height: 70px;
  border-radius: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  font-size: 36px;
}

.service-body {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  width: 100%;
}

.service-name {
  color: #1e293b;
  margin: 0 0 15px 0;
  font-size: 20px;
  font-weight: 600;
}

.service-desc {
  color: #64748b;
  font-size: 14px;
  line-height: 1.6;
  margin-bottom: 25px;
  flex-grow: 1;
}

.apply-now-btn {
  background-color: #1e293b;
  color: white;
  border: none;
  padding: 14px 32px;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  font-size: 14px;
  transition: all 0.3s ease;
  width: 100%;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.apply-now-btn:hover {
  background-color: #0f172a;
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
}

/* Requirements */
.requirements-section {
  padding: 60px 50px;
  max-width: 1200px;
  margin: 0 auto;
  background: #f8fafc;
}

.requirements-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 25px;
}

.requirement-card {
  background: white;
  padding: 35px 30px;
  border-radius: 16px;
  border: 1px solid #e2e8f0;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.requirement-card:hover {
  box-shadow: 0 6px 16px rgba(0, 0, 0, 0.1);
}

.requirement-icon {
  width: 64px;
  height: 64px;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
  font-size: 32px;
}

.category-title {
  font-size: 17px;
  font-weight: 600;
  color: #1e293b;
  margin-bottom: 18px;
  line-height: 1.4;
}

.item-list {
  list-style: none;
  padding: 0;
  margin: 0;
  width: 100%;
  text-align: left;
}

.requirement-item {
  display: flex;
  gap: 10px;
  padding: 8px 0;
  color: #475569;
  font-size: 13px;
  line-height: 1.4;
  border-bottom: 1px solid #f1f5f9;
}

.requirement-item:last-child {
  border-bottom: none;
}

.check-icon {
  color: #16a34a;
  font-weight: bold;
  font-size: 14px;
  flex-shrink: 0;
}

.footer {
  text-align: center;
  padding: 40px;
  border-top: 1px solid #eee;
  color: #888;
  font-size: 13px;
}

/* Responsive */
@media (max-width: 900px) {
  .hero-content,
  .services-grid,
  .requirements-grid {
    flex-direction: column;
    grid-template-columns: 1fr;
  }
  .navbar {
    padding: 15px 20px;
  }
}
</style>