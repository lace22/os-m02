- egrep '(vmx|svm)' /proc/cpuinfo --> Ver si la CPU tiene virtualizacion
	- Tiene que salir **vmx** o **smx** 
- dnf install @virtualization

para usar System X como root: xhost +
- **virsh list**: Mostrarà les màquines arrencades. Amb el paràmetre **--all** ens mostrarà totes, també les apagades.
- **virsh start <id | nom>**: Indicant el nºid de màquina o el seu nom la podrem arrencar.
- **virsh destroy <id | nom>**: Per aturar-la
- **virsh undefine <id | nom>**: Amb aquesta comanda eliminarem la màquina (no els discs que tingui)
- **virsh dumpxml <id | nom>**: Ens volcarà per pantalla la definició xml de la màquina. Preneu-vos un moment en mirar per sobre el contingut. Hi veureu definicions de memòria, cpu, àudio... Podem fer-nos una còpia de seguretat de la configuració de maquinari de la màquina virtual si ho reenviem a un fitxer, per exemple afegint **> nom.xml**
- **virsh define <nom.xml>**: Ens crearà una nova màquina virtual amb el maquinari que hi hagi definit al fitxer nom.xml
- **virsh domdisplay <id | nom>**: Ens mostrarà la URI de conexio al visor. Amb l'ordre **virt-viewer <URI>**  que ens ha donat se'ns obrirà el visor a la màquina virtual.
- qemu-img info <disc.qcow2>:
- qemu-img create -f  <disc.qcow2>
- virsh suspend --> Pausar
- virsh resume
- virsh shutdown
- virsh destroy
- virsh list all
- virsh edit
- virsh start
- virsh domdisplay --> ver URL
- virsh undefine
- virsh define
 
