# humanOS-Conky es una configuración de conky para mostrar información sobre el estado del sistema.
![humanOS conky](/art/art1.png)

## Instalación 
Instala el conky y copia el archivo ".conkyrc" en el home de su usuario.
```
sudo apt-get install conky-all
```
Puedes encontrar ayuda aqui [HumanOS](https://humanos.uci.cu/search/instalar+conky)
###  Los procesadores y una barra de cada uno de ellos con su % de uso.
```
${font Ubuntu:style=bold:size=12}Procesadores $hr
${font Ubuntu:style=bold:size=10}
CPU1: ${cpu cpu1}% ${cpubar cpu1 } 
CPU2: ${cpu cpu2}% ${cpubar cpu2 }
CPU3: ${cpu cpu3}% ${cpubar cpu3}
CPU4: ${cpu cpu4}% ${cpubar cpu4}
Temperatura: $alignr ${acpitemp} C
```

### La RAM y una barra con su % de uso.
```
${font Ubuntu:style=bold:size=12}RAM $alignr ${font Ubuntu:style=bold:size=10}$mem / $memmax
${membar}
```
### Las particiones y una barra con su % de uso.
```
${font Ubuntu:style=bold:size=12}Discos $hr
${font Ubuntu:style=bold:size=10}HOME $alignr ${fs_used /home} / ${fs_size /home}
${fs_bar /home}
${font Ubuntu:style=bold:size=10}Datos $alignr ${fs_used /media/user/Datos} / ${fs_size /media/user/Datos}
${fs_bar /media/user/Datos}
```
### El estado de la batería con una barra
```
${font Ubuntu:style=bold:size=12}Batería $hr
${font Ubuntu:style=bold:size=10} ${battery BAT1} $alignr
${battery_bar BAT1}
```
### Los datos de la interfas de red "enp1s0"
```
${if_existing /proc/net/route enp1s0} 
${font  Ubuntu:style=bold:size=12}Red ${hr}
${font Ubuntu:style=bold:size=10}IP : $alignr ${color white}${addr enp1s0}
In: ${color white}${downspeed enp1s0} kb/s $alignr Total Up: ${color white}${totalup enp1s0}
Out: ${color white}${upspeed enp1s0} kb/s $alignr Total Down: ${color white}${totaldown enp1s0}
${endif}
```
### Los datos de la interfas de red wifi "wlp2s0"
```
${if_existing /proc/net/route wlp2s0} 
${font  Ubuntu:style=bold:size=12}WIFI ${hr}
${font Ubuntu:style=bold:size=10}Intensidad WIFI $alignr ${wireless_link_qual wlp2s0}% 
${font Ubuntu:style=bold:size=10}IP : $alignr ${color white}${addr wlp2s0}
In: ${color white}${downspeed wlp2s0} kb/s $alignr Total Up: ${color white}${totalup wlp2s0}
Out: ${color white}${upspeed wlp2s0} kb/s $alignr Total Down: ${color white}${totaldown wlp2s0}
Total Connections: ${color white}${font Ubuntu:style=bold:size=10}${exec arp|grep wlp2s0 |grep -c 'ether'}
${font Ubuntu:style=bold:size=10}      IP'S                             MAC'S
${color white}${font Ubuntu:style=bold:size=10}${exec arp|grep wlp2s0 | grep 'ether'|sed -e 's/ether //' | grep 'C'|sed -e 's/C //'}${alignr}
${endif}
```
### El top 5 de las app que más usan el CPU
```
${font Ubuntu:style=bold:size=12}Uso CPU aplicaciones $hr
${font Ubuntu:style=bold:size=10}
${top name 1}$alignr${top cpu 1}%
${top name 2}$alignr${top cpu 2}%
${top name 3}$alignr${top cpu 3}%
${top name 4}$alignr${top cpu 4}%
${top name 5}$alignr${top cpu 5}%
```
### El top 5 de las app que más usan la RAM
```
${font Ubuntu:style=bold:size=12}Uso RAM aplicaciones $hr
${font Ubuntu:style=bold:size=10}
${top_mem name 1}$alignr${top_mem mem 1}%
${top_mem name 2}$alignr${top_mem mem 2}%
${top_mem name 3}$alignr${top_mem mem 3}%
${top_mem name 4}$alignr${top_mem mem 4}%
${top_mem name 5}$alignr${top_mem mem 5}%
```
