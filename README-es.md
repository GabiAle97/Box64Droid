![logo](logo.png "logo")

Español
&nbsp;&nbsp;| &nbsp;&nbsp;
<a href="https://github.com/GabiAle97/Box64Droid/blob/main/README.md">English</a>

# Box64Mod
Box64Mod es una modificación de [Box64Droid](https://ilya114.github.io/Box64Droid/) que agrega algunas librerías faltantes y agrega algunas configuraciones adicionales de personalización, así como instaladores de nuevas versiones de Turnip y de Wine. Aún no se pueden jugar a TODOS los juegos en 4K 60FPS, de hecho algunos ni siquiera iniciaran, pero si logra correr algunos juegos AAA como RE2/RE3 Remake.

## Instrucciones de instalación
Instale [Termux](https://github.com/termux/termux-app/releases/download/v0.118.0/termux-app_v0.118.0+github-debug_arm64-v8a.apk) y [Termux-x11](https://github.com/Ilya114/Box64Droid/releases/download/stable/app-arm64-v8a-debug.apk). Luego, en Termux, corra el siguiente comando instalador: `curl -o install https://raw.githubusercontent.com/GabiAle97/Box64Droid/main/scripts/install && chmod +x install && ./install`

Despues de que la instalación complete, tipee `box64droid --start`, y el script lanzará el menú principal.

Este programa es compatible con [Input Bridge](https://github.com/GabiAle97/Box64Droid/releases/download/mod_box/InputBridge_v0.1.9.9.apk), solo se debe instalar y luego ejecutar la aplicación tanto en Android como en Wine.

## Requerimientos de sistema

- Adreno 610+ (Otros procesadores son soportados por VirGL, pero muchos juegos no funcionan)
- Android 12+ (Para no-root y VirGl), Android 10+ (Para root)
- Android 64-bit 
- Entre 2 y 4GB (Root), Entre 4 y 5GB (No-Root) y entre 2 y 3GB (VirGL) de espacio libre para la instalación.
- Si busca más FPS y estabilidad, use la versión root (Necesitará privilegios de Root en el dispositivo)

## Configuración

Se pueden usar variables de entorno, declaradas en 3 archivos distintos: `DXVK_D8VK.conf`, `Box64Droid.conf` y `DXVK_D8VK.conf`. Estos archivos se pueden encontrar en la carpeta /sdcard/Box64Droid/ despues de correr Box64Droid por primera vez.

`Box64Droid.conf` apunta a la configuración de Box86, Box64 y Wine. Puede usar variables de entorno de [Box86](https://github.com/ptitSeb/box86/blob/master/docs/USAGE.md#) y [Box64](https://github.com/ptitSeb/box64/blob/main/docs/USAGE.md). Puede agregar tantas variables como desee.

`DXVK_D8VK_HUD.conf` contiene variables de entorno referentes a [DXVK_HUD](https://github.com/doitsujin/dxvk#hud).

`DXVK_D8VK.conf` contiene variables de entorno referentes a [dxvk](https://github.com/doitsujin/dxvk/blob/master/dxvk.conf).

## Problemas conocidos

- Error al actualizar paquetes de Termux. Borrar los datos de Termux puede ayudar.
- Android 12+ puede matar Termux. Verás el siguiente mensaje: `[Process completed (signal 9) - press Enter]`. Para solucionarlo, conecta el dispositivo a una PC, activa "Depuración por USB" y corre el siguiente comando en una terminal: `adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"`
- El menú "Control" en Wine (en Wine Proton 8.0-2 funciona) queda en blanco. Puede abrir el menú `control` usando la opción "Run".
- Winetricks toma mucho tiempo en abrirse si Proton está instalado (Solo en la versión no-root)

Si hay algún otro inconveniente, puedes reportarlo en:

- [Discord](https://discord.gg/a2Xmz8VP)
- [GitHub Issues](https://github.com/GabiAle97/Box64Droid/issues)

Novedades sobre el proyecto en [YouTube](https://www.youtube.com/channel/UC3hKKXC1EbYnAj6ooWxfrjA).

## Instrucciones para montar SD-card o unidad externa (Versión Root)

Si quiere montar una SD-card o una unidad externa de almacenamiento, debe añadir el punto de montaje manualmente. Para la SD-card vaya a /storage y liste las carpetas (`sudo ls`) (Por ejemplo: `8D3E-2B7K`). Para unidades externas vaya a /mnt/media_rw y liste las carpetas (Por ejemplo: `C3G3H6B8A56212H7`). Corra el comando `nano $PREFIX/bin/box64droid` y añada el comando de montaje antes de la linea `sudo chroot login ...`: `sudo mount --bind /mnt/media_rw/C3G3H6B8A56212H7 $ROOTFSPATH/needfolder` en caso de montar una unidad externa o `sudo mount --bind /sdcard/8D3E-2B7K $ROOTFSPATH/needfolder` para montar una SD-card (Notese que en los comandos estos usando las carpetas que pusimos antes como ejemplo, alli debe reemplazar por sus respectivas carpetas). Necesita crear la carpeta `needfolder` en la carpeta ~/ubuntu corriendo `sudo mkdir foldername` 

## Notas

Algunos errores e inestabilidades pueden pasar al usar Box86 y Box64 en el entorno proot (no-root), por lo que no se recomienda usar Box86 y Box64 en proot como entorno de debug/testing.

## Aplicaciones usadas por Box64Droid y Box64Mod
- [Termux-app](https://github.com/termux/termux-app) - GPLv3 license
- [Box64 by ptitseb](https://github.com/ptitSeb/box64) - MIT license
- [Box86 by ptitseb](https://github.com/ptitSeb/box86) - MIT license
- [Wine Stable, Staging and Staging-tkg GPL-2.1 license](https://wiki.winehq.org/Licensing) (builded by [Kron4ek](https://github.com/Kron4ek) by MIT License), [Wine Proton by Valve](https://github.com/ValveSoftware/Proton) (own license), [Wine GE](https://github.com/GloriousEggroll/wine-ge-custom) (using in Lutris)
- [Mesa](https://docs.mesa3d.org/license.html) - MIT, Khronos, SGI Free Software License B and Boost (permissive) licenses
- [Termux-x11](https://github.com/termux/termux-x11) - GPL-3.0 license
- [DXVK](https://github.com/doitsujin/dxvk) - Zlib license
- [Proot-distro](https://github.com/termux/proot-distro) - GPL-3.0 license
- [Forked Mesa to work Turnip on Adreno 730 and 740](https://gitlab.freedesktop.org/Danil/mesa/-/tree/turnip/feature/a7xx-basic-support)
- [D8VK](https://github.com/AlpyneDreams/d8vk) - Zlib license
- [DXVK-Async](https://github.com/Sporif/dxvk-async) 
- [DXVK-GPLAsync](https://gitlab.com/Ph42oN/dxvk-gplasync)
- [WineD3D for Windows](https://fdossena.com/?p=wined3d/index.frag) - GPL-2.0+ license
- [Winetricks](https://wiki.winehq.org/Winetricks)
- [vkd3d-proton](https://github.com/HansKristian-Work/vkd3d-proton) - LGPL v2.1 license
- [Box64Droid](https://github.com/Ilya114/Box64Droid) - GPL-3.0 license
- [Termux-Box](https://github.com/olegos2/termux-box) - GPL-3.0 license

## Gracias a:
- [Herick75](https://github.com/Herick75) - Por los parches de Turnip que hacen posible compilarlo
- [Inguna87](https://github.com/inguna87) - Por empezar con los fixes de Chroot en MIUI y Oxygen
- [Alfhashut](https://github.com/alfhashut) - Por ayudar con VirGL
- [Mr.Purple](https://github.com/MrPurple666) - Por ayudar a compilar algunas librerías de Turnip y por ayudar en las actualizaciones de systema y box86/64
