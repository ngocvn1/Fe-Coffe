<template>
<div class="nav-container primary-menu">
    <div class="mobile-topbar-header">
        <div>
            <img src="/assets/images/logo-icon.png" class="logo-icon" alt="logo icon">
        </div>
        <div>
            <h4 class="logo-text">Rukada</h4>
        </div>
        <div class="toggle-icon ms-auto"><i class='bx bx-arrow-to-left'></i>
        </div>
    </div>
    <nav class="navbar navbar-expand-xl w-100">
        <ul class="navbar-nav justify-content-start flex-grow-1 gap-1">
            <li class="nav-item dropdown">
                <a href="javascript:;" class="nav-link dropdown-toggle dropdown-toggle-nocaret"
                    data-bs-toggle="dropdown">
                    <div class="parent-icon"><i class='bx bx-home-circle'></i>
                    </div>
                    <div class="menu-title">Dashboard</div>
                </a>
                <ul class="dropdown-menu">
                    <li> <a class="dropdown-item" href="index.html"><i
                                class="bx bx-right-arrow-alt"></i>Default</a>
                    </li>
                    <li> <a class="dropdown-item" href="index2.html"><i
                                class="bx bx-right-arrow-alt"></i>Alternate</a>
                    </li>
                    <li> <a class="dropdown-item" href="index3.html"><i
                                class="bx bx-right-arrow-alt"></i>Graphical</a>
                    </li>
                </ul>
            </li>
            <li class="nav-item">
                <router-link to="/admin/danh-muc">
                    <a href="/admin/danh-muc" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-list"></i>
                        </div>
                        <div class="menu-title">Danh Mục</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/nhan-vien">
                    <a href="/admin/nhan-vien" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-person"></i>
                        </div>
                        <div class="menu-title">Nhân Viên</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/chuc-vu">
                    <a href="/admin/chuc-vu" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-skull-crossbones"></i>
                        </div>
                        <div class="menu-title">Chức Vụ</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/ban">
                    <a href="/admin/ban" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-inbox"></i>
                        </div>
                        <div class="menu-title">Bàn</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/khu-vuc">
                    <a href="/admin/khu-vuc" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-map"></i>
                        </div>
                        <div class="menu-title">Khu Vực</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/nha-cung-cap">
                    <a href="/admin/nha-cung-cap" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-house"></i>
                        </div>
                        <div class="menu-title">Nhà Cung Cấp</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/nguyen-lieu">
                    <a href="/admin/nguyen-lieu" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-cubes-stacked"></i>
                        </div>
                        <div class="menu-title">Nguyên Liệu</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/mon-an">
                    <a href="/admin/mon-an" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-plate-wheat"></i>
                        </div>
                        <div class="menu-title">Món Ăn</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/nhap-kho">
                    <a href="/admin/nhap-kho" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-map"></i>
                        </div>
                        <div class="menu-title">Nhập Kho</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/chuyen-muc">
                    <a href="/admin/chuyen-muc" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-bars"></i>
                        </div>
                        <div class="menu-title">Chuyên Mục</div>
                    </a>
                </router-link>
            </li>
            <li class="nav-item">
                <router-link to="/admin/bai-viet">
                    <a href="/admin/bai-viet" class="nav-link">
                        <div class="parent-icon">
                            <i class="fa-solid fa-newspaper"></i>
                        </div>
                        <div class="menu-title">Bài Viết</div>
                    </a>
                </router-link>
            </li>
        </ul>
    </nav>
</div>
</template>
<script>
export default {
    
}
</script>
<style>
    
</style>