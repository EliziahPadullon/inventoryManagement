<script lang="ts">
    import { GridSolid, ClipboardListSolid, FileChartBarOutline } from 'flowbite-svelte-icons';
    import { page } from '$app/stores'; // Import the SvelteKit $page store
    import '../app.css';

    let isOpen = true;

    // List of routes where the sidebar should appear
    const sidebarRoutes = ['/dashboard', '/products', '/reports'];

    function toggleSidebar() {
        isOpen = !isOpen;
    }
</script>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous">
    <link href="https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,300..900;1,300..900&display=swap" rel="stylesheet">
    <link href='https://unpkg.com/boxicons@2.1.4/css/boxicons.min.css' rel='stylesheet'>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.7.1/css/all.min.css" rel="stylesheet">
</svelte:head>

<style>
    .layout {
        display: flex;
        height: 100vh;
    }

    .sidebar {
        background-color: #6e946c;
        color: #333;
        width: 250px;
        height: 100vh;
        display: flex;
        flex-direction: column;
        transition: all 0.3s ease;
    }

    .sidebar-collapsed {
        width: 60px;
    }

    .menu-item {
        display: flex;
        align-items: center;
        padding: 1rem;
        cursor: pointer;
        transition: background 0.3s ease;
        gap: 0.5rem;
    }

    .menu-item:hover {
        background-color: #9bbf8d;
    }

    .menu-icon {
        margin-right: 1rem;
        width: 24px;
        height: 24px;
    }

    .menu-text {
        display: inline;
        transition: opacity 0.3s ease;
    }

    .sidebar-collapsed .menu-text {
        opacity: 0;
        visibility: hidden;
    }

    .toggle-btn {
        padding: 0.5rem;
        background: none;
        border: none;
        cursor: pointer;
    }

    .menu {
        flex-grow: 1;
    }

    .logout {
        margin-top: auto;
    }

    .content {
        flex: 1;
        padding: 1rem;
        overflow-y: auto;
        background-color: #f9f9f9;
    }
</style>

<div class="layout">
    <!-- Sidebar -->
    {#if sidebarRoutes.includes($page.url.pathname)}
        <div class="sidebar" class:sidebar-collapsed={!isOpen}>
            <button class="toggle-btn" on:click={toggleSidebar}>
                ☰
            </button>

            <div class="menu">
                <div class="menu-item">
                    <GridSolid class="menu-icon text-gray-800 dark:text-white" />
                    <a href="/dashboard" class="menu-text">Dashboard</a>
                </div>
                <div class="menu-item">
                    <ClipboardListSolid class="menu-icon text-gray-800 dark:text-white" />
                    <a href="/products" class="menu-text">Products</a>
                </div>
                <div class="menu-item">
                    <FileChartBarOutline class="menu-icon text-gray-800 dark:text-white" />
                    <a href="/reports" class="menu-text">Reports</a>
                </div>
            </div>

            <div class="menu-item logout">
                <svg class="menu-icon text-gray-800 dark:text-white" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" viewBox="0 0 24 24">
                    <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 12H4m12 0-4 4m4-4-4-4m3-4h2a3 3 0 0 1 3 3v10a3 3 0 0 1-3 3h-2"/>
                </svg>
                <a href="/" class="menu-text">Log out</a>
            </div>
        </div>
    {/if}

    <!-- Page Content -->
    <div class="content">
        <slot></slot>
    </div>
</div>
