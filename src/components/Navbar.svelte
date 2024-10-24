<script>
    import logo from '$lib/assets/s-high-resolution-logo-transparent.png'

    let menus = [
        {name: "About", link: "#about"},
        {name: "Work", link: "#work"},
        {name: "Contact", link: "#contact"}
    ];
    let active = "";
    let menuToggle = false;

    function toggleMenu(){
        menuToggle = !menuToggle;
    }

    function navMenuToggle(name){
        menuToggle = !menuToggle;
        active = name;
    }
</script>

<div class="sm:px-16 px6 w-full flex items-center py-5 fixed top-0 z-20 bg-black">
    <div class="w-full flex justify-between items-center max-w-7xl mx-auto">
        <a href="/" class="flex items-center gap-2">
            <img src="{logo}" alt="logo" class="w-9 h-9 object-contain"/>
            <p class="text-white text-[18px] font-bold cursor-pointer flex">Syidik &nbsp; <span class="sm:block hidden">Permadi</span></p>
        </a>
        <ul class="list-none hidden sm:flex flex-row gap-10">
            {#each menus as menu, index}
                <li class="{active === menu.name ? 'text-white' : 'text-gray-400'} hover:text-white text-[18px] font-medium cursor-pointer">
                    <a href="/{menu.link}" on:click={()=>(active=menu.name)}>{menu.name}</a>
                </li>
            {/each}
        </ul>
        <div class="sm:hidden flex flex-1 justify-end items-center">
            <button on:click={toggleMenu}>
                <i class="fa-solid {!menuToggle ? 'fa-bars' : 'fa-x'}"></i>
            </button>
            <div class="{!menuToggle ? 'hidden' : 'flex'} p-6 bg-slate-800 absolute top-20 right-0 mx-4 my-2 min-w-[140px] z-10 rounded-xl">
                <ul class="list-none flex justify-end items-start flex-col gap-4">
                    {#each menus as menu, index}
                        <li class="{active === menu.name ? 'text-white' : 'text-gray-400'} font-poppins font-medium cursor-pointer text-[16px]">
                            <a href="/{menu.link}" on:click={()=>{active=menu.name;  menuToggle = !menuToggle;}}>{menu.name}</a>
                        </li>
                    {/each}
                </ul>
            </div>
        </div>
    </div>
</div>