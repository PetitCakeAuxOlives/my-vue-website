<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container-fluid">
            <RouterLink class="navbar-brand" to="/">
                <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="35" height="35" />
            </RouterLink>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                <li class="nav-item">
                <RouterLink class="nav-link" aria-current="page" to="/">Home</RouterLink>
                </li>
                <li class="nav-item">
                <RouterLink class="nav-link" to="/portfolio">Portolio</RouterLink>
                </li>
                <li class="nav-item">
                <RouterLink class="nav-link" to="/contact">Contact</RouterLink>
                </li>
            </ul>
            </div>
        </div>
    </nav>
</template>