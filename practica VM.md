# UF1. Exercici 2.1. Crear màquines virtuals

## Introducció

Les màquines virtuals simularan un maquinari que ens permetrà instal.lar-hi sistemes operatius convidats (guest).

## Continguts

Farem ús del virt-manager per tal de crear i gestionar maquinari de màquines virtuals amb l'hipervisor de codi obert KVM/qemu:

Requisits:
- CentOs/Fedora: dnf install @Virtualization -y
- Debian/Ubuntu: apt install qemu-kvm libvirt-clients qemu-utils libvirt-daemon-system virt-viewer virt-manager -y

Comproveu que el servei libvirtd està funcionant: systemctl status libvirtd i si no l'engegueu.

## Entrega

1. **Crea una màquina amb el virt-manager que ens permeti instal.lar-hi el Fedora 27 a partir del servidor de xarxa PXE. Inícia-la i instala-hi el sistema operatiu Fedora 27. Fes servir un disc dur virtual qcow2 de 10GB. Què has seleccionat a cada apartat?**
- 1/4 Com volem instal.lar el sistema operatiu?

	- Amb una ISO


- 2/4 Quin emmagatzematge has fet servir? Detalla'n el procés de creació.

	- Una imatge qcow 2 creada amb
	```
	# qemu-img create -f qcow2 fedorahdd.qcow2 10G
	```


- 2/4 Quin tipus de sistema operatiu i versió has seleccionat?
	```
	- OS Type: Linux
	- Version: Fedora 27
	```

- 3/4 Quanta memòria i fils de processador has seleccionat? Indica també el total físic que té la teva màquina

	```
	- RAM: 1024
	- CPUs: 2

	```
	- La màquina te 4096 MB de RAM i 2 fils de processador

- 4/4 Quin és el nom que li has posat a la màquina?

	- Fedora 27



2. **Una vegada instal.lat ves al maquinari de la màquina virtual dins el virt-manager i indica:**
- Quina interfície de disc dur fa servir?

	- VirtIO

- Quin model de tarja de xarxa fa servir?

	- VirtIO

- Quina tarja de vídeo té?

	- QXL

- Quina pantalla (display) té?

	- Spice Server

- Quin processador s'ha seleccionat?

	- Nehalem-IBRS



3. **Sense aturar la màquina virtual afegiu-hi una segona tarja (model virtio) de xarxa des del maquinari. Feu que aquesta xarxa sigui la d'amfitrió.**
- Comproveu dins la màquina virtual Fedora si ha aparegut (sense reiniciar-la) la tarja virtual. Podeu fer servir la comanda **ip address show**.


- Indiqueu quines xarxes teniu, la seva adreça ip i identifiqueu cadascuna segons sigui NAT o d'amfitrió.

	- ens2 (NAT): 192.168.5.151
	- ens10 (Routed): 192.168.6.206

4. **Proveu ara (sense aturar la màquina virtual) de canviar la memòria RAM. Mireu dins la màquina (top/htop) si ha canviat. Quines conclusions en treieu?**
	- Si ha cambiat, trec la conclusió de que Fedora está pensat per maquines virtuals o servidors per no haber de pararlos

5. **Mireu al maquinari de la màquina virtual quines opcions d'arrencada disposa i indiqueu-los aquí.**


6. **Amb la màquina arrencada feu ús de la línia d'ordres i amb l'ordre virsh indiqueu les ordres per tal de:**
- Suspendre la màquina virtual (pausar):

- Resumir una màquina virtual pausada (continuar executant):

- Enviar senyal d'apagada a la màquina virtual:

- Forçar l'aturada de la màquina virtual:

- Llistar totes les màquines virtuals que tenim definides:

- Editar la configuració XML de la màquina virtual:

- Iniciar la màquina virtual:

- Veure la URI de conexió al visor de la màquina virtual:

- Desar la configuració XML de maquinari de la màquina virtual en un fitxer anomentat Fedora.xml

- Eliminar la màquina virtual:

- Crear de nou la màquina virtual a partir del fitxer de maquinari Fedora.xml

7. **Amb la utilitat virt-install podem crear màquines virtuals a partir de repositoris que hi ha a Internet o també a partir de ISO d'instal.lació de sistemes operatius. L'haureu d'instal.lar i crear un disc primer on instal.lar el sistema operatiu que farem servir (Ubuntu 18):
- Creem un disc amb qemu-img: qemu-img create -f qcow2 ./ubuntu18.qcow2 8G
- Descarreguem la imatge ISO d'instal.lació de Ubuntu 18.
- Creem la màquina amb l'ordre: virt-install --name Ubuntu18 --ram 1024 --disk path=./ubuntu18.qcow2,size=8 --vcpus 1 --os-type generic --os-variant generic --network bridge=virbr0 --graphics vnc,port=5999 --console pty,target_type=serial --cdrom ./ubuntu-18.04.1-live-server-amd64.iso


8. **Descarregueu del web http://www.qemu-advent-calendar.org/2016/ el dia 6 on hi ha el MenuetOs (també el teniu en aquest directori). Mirant el fitxer run.sh realitzeu:**
- On es troba el fitxer de disc de la màquina MenuetOS i quin nom té? Indiqueu com el podem obtenir.

- Quina extensió té el fitxer d'imatge de disc?

- Quin format té aquesta imatge de disc?

- De quin tipus de dispositiu d'emmagatzematge es tracta?

- Quin tamany té el fitxer de disc d'emmagatzematge on hi ha instal.lat el sistema operatiu MenuetOS?

- Quin maquinari es farà servir per arrencar aquesta màquina virtual? Indiqueu emmagatzematge, memòria i tarja de so.

- Quina és la comanda qemu-system-x86_64 complerta que haurem d'executar per tal que arrenqui?

9. **Creeu ara aquesta mateixa màquina virtual MenuetOS mitjançant l'entorn gràfic del virt-manager i arrenqueu-la. Indiqueu com l'heu configurat:**
- 1/4 Com volem instal.lar el sistema operatiu?


- 2/4 Quin emmagatzematge has fet servir? Detalla'n el procés de creació.


- 2/4 Quin tipus de sistema operatiu i versió has seleccionat?


- 3/4 Quanta memòria i fils de processador has seleccionat? Indica també el total físic que té la teva màquina


- 4/4 Quin és el nom que li has posat a la màquina?


- Heu hagut de realitzar algun canvi en el maquinari per defecte per tal que pogués arrencar?


10. **Creeu ara una màquina virtual Windows que faci servir per a la interfície de xarxa i de disc dur els controladors virtio. Indiqueu el procés seguits (passos)**
