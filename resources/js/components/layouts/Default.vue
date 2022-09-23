<template>
    <div>
        <header id="header" class="header fixed-top d-flex align-items-center bg-success">
         <div class="d-flex align-items-center justify-content-between"> <a href="index.html" class="logo d-flex align-items-center"><router-link :to="{name:'dashboard'}" class="navbar-brand">
                    <h2>
                        <span class="text-white">Past</span>
                        <span class="text-warning">Papers</span>
                    </h2>
                </router-link></a> <i class="bi bi-list toggle-sidebar-btn"></i></div>
         <div class="search-bar">
            <form class="search-form d-flex align-items-center" method="POST" action="#"> <input type="text" name="query" placeholder="Search" title="Enter search keyword"> <button type="submit" title="Search"><i class="bi bi-search"></i></button></form>
         </div>
         <nav class="header-nav ms-auto">
            <ul class="d-flex align-items-center">
               <li class="nav-item d-block d-lg-none"> <a class="nav-link nav-icon search-bar-toggle " href="#"> <i class="bi bi-search"></i> </a></li>
               
               <li class="nav-item dropdown pe-3">
                  <a class="nav-link nav-profile d-flex align-items-center pe-0" href="#" data-bs-toggle="dropdown"> <span class="d-none d-md-block dropdown-toggle ps-2">{{ user.first_name }} </span> </a>
                  <ul class="dropdown-menu dropdown-menu-end dropdown-menu-arrow profile">
                     <li class="dropdown-header">
                        <h6>Jassa</h6>
                        <span>Web Designer</span>
                     </li>
                     <li>
                        <hr class="dropdown-divider">
                     </li>
                     <li> <a class="dropdown-item d-flex align-items-center" href="users-profile.html"> <i class="bi bi-person"></i> <span>My Profile</span> </a></li>
                     <li>
                        <hr class="dropdown-divider">
                     </li>
                     <li> <a class="dropdown-item d-flex align-items-center" href="users-profile.html"> <i class="bi bi-gear"></i> <span>Account Settings</span> </a></li>
                     <li>
                        <hr class="dropdown-divider">
                     </li>
                     <li> <a class="dropdown-item d-flex align-items-center" href="pages-faq.html"> <i class="bi bi-question-circle"></i> <span>Need Help?</span> </a></li>
                     <li>
                        <hr class="dropdown-divider">
                     </li>
                     <li> <a class="dropdown-item d-flex align-items-center" href="#"> <i class="bi bi-box-arrow-right"></i> <span>Sign Out</span> </a></li>
                  </ul>
               </li>
            </ul>
         </nav>
      </header>
      <aside id="sidebar" class="sidebar">
         <ul class="sidebar-nav" id="sidebar-nav">
            <li class="nav-item"> <a class="nav-link " href="index.html"> <i class="bi bi-grid"></i> <span>Dashboard</span> </a></li>
            <li class="nav-item"> <a class="nav-link collapsed" href="users-profile.html"> <i class="bi bi-person"></i> <span>Users</span> </a></li>
            <li class="nav-item"> <a class="nav-link collapsed" href="pages-faq.html"> <i class="bi bi-question-circle"></i> <span>Faculties</span> </a></li>
            <li class="nav-item"> <a class="nav-link collapsed" href="pages-contact.html"> <i class="bi bi-envelope"></i> <span>Courses</span> </a></li>
            <li class="nav-item"> <a class="nav-link collapsed" href="pages-contact.html"> <i class="bi bi-envelope"></i> <span>Units</span> </a></li>
            
            <li class="nav-heading">Pages</li>
            
            <li class="nav-item"> <a class="nav-link collapsed" href="users-profile.html"> <i class="bi bi-person"></i> <span>Profile</span> </a></li>
            <li class="nav-item"> <a class="nav-link collapsed" href="pages-faq.html"> <i class="bi bi-question-circle"></i> <span>F.A.Q</span> </a></li>
            <li class="nav-item"> <a class="nav-link collapsed" href="pages-contact.html"> <i class="bi bi-envelope"></i> <span>Contact</span> </a></li>
         </ul>
      </aside>
        <main id="main" class="main">
            <router-view></router-view>
        </main>
        <footer id="footer" class="footer">
         <div class="copyright"> &copy; Copyright <strong><span>Compnay Name</span></strong>. All Rights Reserved</div>
         <div class="credits"> with love <a href="https://freeetemplates.com/">FreeeTemplates</a></div>
      </footer>
    </div>
</template>

<script>
import {mapActions} from 'vuex'
export default {
    name:"default-layout",
    data(){
        return {
            user:this.$store.state.auth.user
        }
    },
    methods:{
        ...mapActions({
            signOut:"auth/logout"
        }),
        async logout(){
            await axios.post('/logout').then(({data})=>{
                this.signOut()
                this.$router.push({name:"login"})
            })
        }
    }
}
</script>
<style>
/*--------------------------------------------------------------
# General
--------------------------------------------------------------*/
:root {
	scroll-behavior: smooth;
  }
   
  a {
	color: #4154f1;
	text-decoration: none;
  }
  
  a:hover {
	color: #717ff5;
	text-decoration: none;
  }

  
  /*--------------------------------------------------------------
  # Main
  --------------------------------------------------------------*/
  #main {
	margin-top: 60px;
	padding: 20px 30px;
	transition: all 0.3s;
  }
  @media (max-width: 1199px) {
	#main {
	  padding: 20px;
	}
  }
  
  
  
  /*--------------------------------------------------------------
  # Back to top button
  --------------------------------------------------------------*/
  .back-to-top {
	position: fixed;
	visibility: hidden;
	opacity: 0;
	right: 15px;
	bottom: 15px;
	z-index: 99999;
	background: #4154f1;
	width: 40px;
	height: 40px;
	border-radius: 4px;
	transition: all 0.4s;
  }
  .back-to-top i {
	font-size: 24px;
	color: #fff;
	line-height: 0;
  }
  .back-to-top:hover {
	background: #6776f4;
	color: #fff;
  }
  .back-to-top.active {
	visibility: visible;
	opacity: 1;
  }
  
  /*--------------------------------------------------------------
  # Override some default Bootstrap stylings
  --------------------------------------------------------------*/
  /* Dropdown menus */
  .dropdown-menu {
	border-radius: 4px;
	padding: 10px 0;
	-webkit-animation-name: dropdown-animate;
	animation-name: dropdown-animate;
	-webkit-animation-duration: 0.2s;
	animation-duration: 0.2s;
	-webkit-animation-fill-mode: both;
	animation-fill-mode: both;
	border: 0;
	box-shadow: 0 5px 30px 0 rgba(82, 63, 105, 0.2);
  }
  .dropdown-menu .dropdown-header, .dropdown-menu .dropdown-footer {
	text-align: center;
	font-size: 15px;
	padding: 10px 25px;
  }
  .dropdown-menu .dropdown-footer a {
	color: #444444;
	text-decoration: underline;
  }
  .dropdown-menu .dropdown-footer a:hover {
	text-decoration: none;
  }
  .dropdown-menu .dropdown-divider {
	color: #a5c5fe;
	margin: 0;
  }
  .dropdown-menu .dropdown-item {
	font-size: 14px;
	padding: 10px 15px;
	transition: 0.3s;
  }
  .dropdown-menu .dropdown-item i {
	margin-right: 10px;
	font-size: 18px;
	line-height: 0;
  }
  .dropdown-menu .dropdown-item:hover {
	background-color: #f6f9ff;
  }
  
  @media (min-width: 768px) {
	.dropdown-menu-arrow::before {
	  content: "";
	  width: 13px;
	  height: 13px;
	  background: #fff;
	  position: absolute;
	  top: -7px;
	  right: 20px;
	  transform: rotate(45deg);
	  border-top: 1px solid #eaedf1;
	  border-left: 1px solid #eaedf1;
	}
  }
  @-webkit-keyframes dropdown-animate {
	0% {
	  opacity: 0;
	}
	100% {
	  opacity: 1;
	}
	0% {
	  opacity: 0;
	}
  }
  @keyframes dropdown-animate {
	0% {
	  opacity: 0;
	}
	100% {
	  opacity: 1;
	}
	0% {
	  opacity: 0;
	}
  }
 

  
  /* Bordered Tabs */
  .nav-tabs-bordered {
	border-bottom: 2px solid #ebeef4;
  }
  .nav-tabs-bordered .nav-link {
	margin-bottom: -2px;
	border: none;
	color: #2c384e;
  }
  .nav-tabs-bordered .nav-link:hover, .nav-tabs-bordered .nav-link:focus {
	color: #4154f1;
  }
  .nav-tabs-bordered .nav-link.active {
	background-color: #fff;
	color: #4154f1;
	border-bottom: 2px solid #4154f1;
  }
  
  /*--------------------------------------------------------------
  # Header
  --------------------------------------------------------------*/
  .logo {
	line-height: 1;
  }
  @media (min-width: 1200px) {
	.logo {
	  width: 280px;
	}
  }
  .logo img {
	max-height: 26px;
	margin-right: 6px;
  }
  .logo span {
	font-size: 26px;
	font-weight: 700;
	color: #012970;
	font-family: "Nunito", sans-serif;
  }
  
  .header {
	transition: all 0.5s;
	z-index: 997;
	height: 60px;
	box-shadow: 0px 2px 20px rgba(1, 41, 112, 0.1);
	background-color: #fff;
	padding-left: 20px;
	/* Toggle Sidebar Button */
	/* Search Bar */
  }
  .header .toggle-sidebar-btn {
	font-size: 32px;
	padding-left: 10px;
	cursor: pointer;
	color: #012970;
  }
  .header .search-bar {
	min-width: 360px;
	padding: 0 20px;
  }
  @media (max-width: 1199px) {
	.header .search-bar {
	  position: fixed;
	  top: 50px;
	  left: 0;
	  right: 0;
	  padding: 20px;
	  box-shadow: 0px 0px 15px 0px rgba(1, 41, 112, 0.1);
	  background: white;
	  z-index: 9999;
	  transition: 0.3s;
	  visibility: hidden;
	  opacity: 0;
	}
	.header .search-bar-show {
	  top: 60px;
	  visibility: visible;
	  opacity: 1;
	}
  }
  .header .search-form {
	width: 100%;
  }
  .header .search-form input {
	border: 0;
	font-size: 14px;
	color: #012970;
	border: 1px solid rgba(1, 41, 112, 0.2);
	padding: 7px 38px 7px 8px;
	border-radius: 3px;
	transition: 0.3s;
	width: 100%;
  }
  .header .search-form input:focus, .header .search-form input:hover {
	outline: none;
	box-shadow: 0 0 10px 0 rgba(1, 41, 112, 0.15);
	border: 1px solid rgba(1, 41, 112, 0.3);
  }
  .header .search-form button {
	border: 0;
	padding: 0;
	margin-left: -30px;
	background: none;
  }
  .header .search-form button i {
	color: #012970;
  }
  
  /*--------------------------------------------------------------
  # Header Nav
  --------------------------------------------------------------*/
  .header-nav ul {
	list-style: none;
  }
  .header-nav > ul {
	margin: 0;
	padding: 0;
  }
  .header-nav .nav-icon {
	font-size: 20px;
	color: #012970;
  }
  .header-nav .nav-profile {
	color: #012970;
  }
  .header-nav .nav-profile img {
	max-height: 36px;
  }
  .header-nav .nav-profile span {
	font-size: 14px;
	font-weight: 600;
  }
  .header-nav .badge-number {
	position: absolute;
	inset: 4px 6px auto auto;
	font-weight: normal;
	font-size: 11px;
	padding: 3px 6px;
  }
  .header-nav .notifications .notification-item {
	display: flex;
	align-items: center;
	padding: 15px 10px;
	transition: 0.3s;
  }
  .header-nav .notifications .notification-item i {
	margin: 0 20px 0 10px;
	font-size: 24px;
  }
  .header-nav .notifications .notification-item h4 {
	font-size: 16px;
	font-weight: 600;
	margin-bottom: 5px;
  }
  .header-nav .notifications .notification-item p {
	font-size: 13px;
	margin-bottom: 3px;
	color: #919191;
  }
  .header-nav .notifications .notification-item:hover {
	background-color: #f6f9ff;
  }
  .header-nav .messages .message-item {
	padding: 15px 10px;
	transition: 0.3s;
  }
  .header-nav .messages .message-item a {
	display: flex;
  }
  .header-nav .messages .message-item img {
	margin: 0 20px 0 10px;
	max-height: 40px;
  }
  .header-nav .messages .message-item h4 {
	font-size: 16px;
	font-weight: 600;
	margin-bottom: 5px;
	color: #444444;
  }
  .header-nav .messages .message-item p {
	font-size: 13px;
	margin-bottom: 3px;
	color: #919191;
  }
  .header-nav .messages .message-item:hover {
	background-color: #f6f9ff;
  }
  .header-nav .profile {
	min-width: 240px;
	padding-bottom: 0;
  }
  .header-nav .profile .dropdown-header h6 {
	font-size: 18px;
	margin-bottom: 0;
	font-weight: 600;
	color: #444444;
  }
  .header-nav .profile .dropdown-header span {
	font-size: 14px;
  }
  .header-nav .profile .dropdown-item {
	font-size: 14px;
	padding: 10px 15px;
	transition: 0.3s;
  }
  .header-nav .profile .dropdown-item i {
	margin-right: 10px;
	font-size: 18px;
	line-height: 0;
  }
  .header-nav .profile .dropdown-item:hover {
	background-color: #f6f9ff;
  }
  
  /*--------------------------------------------------------------
  # Sidebar
  --------------------------------------------------------------*/
  .sidebar {
	position: fixed;
	top: 60px;
	left: 0;
	bottom: 0;
	width: 300px;
	z-index: 996;
	transition: all 0.3s;
	padding: 20px;
	overflow-y: auto;
	scrollbar-width: thin;
	scrollbar-color: #aab7cf transparent;
	box-shadow: 0px 0px 20px rgba(1, 41, 112, 0.1);
	background-color: #fff;
  }
  @media (max-width: 1199px) {
	.sidebar {
	  left: -300px;
	}
  }
  .sidebar::-webkit-scrollbar {
	width: 5px;
	height: 8px;
	background-color: #fff;
  }
  .sidebar::-webkit-scrollbar-thumb {
	background-color: #aab7cf;
  }
  
  @media (min-width: 1200px) {
	#main, #footer {
	  margin-left: 300px;
	}
  }
  @media (max-width: 1199px) {
	.toggle-sidebar .sidebar {
	  left: 0;
	}
  }
  @media (min-width: 1200px) {
	.toggle-sidebar #main, .toggle-sidebar #footer {
	  margin-left: 0;
	}
	.toggle-sidebar .sidebar {
	  left: -300px;
	}
  }
  
  .sidebar-nav {
	padding: 0;
	margin: 0;
	list-style: none;
  }
  .sidebar-nav li {
	padding: 0;
	margin: 0;
	list-style: none;
  }
  .sidebar-nav .nav-item {
	margin-bottom: 5px;
  }
  .sidebar-nav .nav-heading {
	font-size: 11px;
	text-transform: uppercase;
	color: #899bbd;
	font-weight: 600;
	margin: 10px 0 5px 15px;
  }
  .sidebar-nav .nav-link {
	display: flex;
	align-items: center;
	font-size: 15px;
	font-weight: 600;
	color: #4154f1;
	transition: 0.3;
	background: #f6f9ff;
	padding: 10px 15px;
	border-radius: 4px;
  }
  .sidebar-nav .nav-link i {
	font-size: 16px;
	margin-right: 10px;
	color: #4154f1;
  }
  .sidebar-nav .nav-link.collapsed {
	color: #012970;
	background: #fff;
  }
  .sidebar-nav .nav-link.collapsed i {
	color: #899bbd;
  }
  .sidebar-nav .nav-link:hover {
	color: #4154f1;
	background: #f6f9ff;
  }
  .sidebar-nav .nav-link:hover i {
	color: #4154f1;
  }
  .sidebar-nav .nav-link .bi-chevron-down {
	margin-right: 0;
	transition: transform 0.2s ease-in-out;
  }
  .sidebar-nav .nav-link:not(.collapsed) .bi-chevron-down {
	transform: rotate(180deg);
  }
  .sidebar-nav .nav-content {
	padding: 5px 0 0 0;
	margin: 0;
	list-style: none;
  }
  .sidebar-nav .nav-content a {
	display: flex;
	align-items: center;
	font-size: 14px;
	font-weight: 600;
	color: #012970;
	transition: 0.3;
	padding: 10px 0 10px 40px;
	transition: 0.3s;
  }
  .sidebar-nav .nav-content a i {
	font-size: 6px;
	margin-right: 8px;
	line-height: 0;
	border-radius: 50%;
  }
  .sidebar-nav .nav-content a:hover, .sidebar-nav .nav-content a.active {
	color: #4154f1;
  }
  .sidebar-nav .nav-content a.active i {
	background-color: #4154f1;
  }
  
  
  
  /*--------------------------------------------------------------
  # Footer
  --------------------------------------------------------------*/
  .footer {
	padding: 20px 0;
	font-size: 14px;
	transition: all 0.3s;
	border-top: 1px solid #cddfff;
  }
  .footer .copyright {
	text-align: center;
	color: #012970;
  }
  .footer .credits {
	padding-top: 5px;
	text-align: center;
	font-size: 13px;
	color: #012970;
  }
</style>