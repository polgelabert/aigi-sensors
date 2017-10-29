

# AIGI

# T1: Intro

Aeroport Intel·ligent: Aeroport dotat de mecanismes intel·ligent amb l'objectiu de millorar:

* Gestio operacions (Eficiencia, Sost)
* Experiència usuaris

Mecanismes intel·ligents:

* Materials, procediments construcció

* Gestió

* Ús intensiu TIC

  ​

#### Àmbits aeroport  inteli·ligent

Infraestructura de comunicacions (cablejada, XSF)

Eficiència operacional:

* Equipatges
* Controls seguretat
* Gestió empleats
* Energia i medi ambient
* Experiència pax

####  

####TIC en Aeroports Intel·ligent

4 components importants:

* Obtenció dades
* Transport dades
* Emmagatzematge (Big Data)
* Resultats













# WSN (Wireless Sensor Network)





## 4.2 802.15.4 (WPAN Task 4)

Requeriments: baix consum, simple, eficient, suport cicles treball

Tipologia de Nodes:

* FFD: Full Function Device: Node/Coordinador/PAN Coord
* RFD: Reduced Function Device: Node

Tipologia xarxa:

* Estrella
* Malla (P2P)

Capa física:

| f       | CH   | kbps |
| :------ | ---- | ---- |
| 896 MHz | 1    | 20   |
| 915 MHz | 10   | 40   |
| 2.4 GHz | 16   | 250  |

PPDU (Physical Protocol Data Unit) = Trama -> 0-127 bytes (Trama + petita que Eth (1500b) -> - SW,HW + simple + eficient + processat)

Capa MAC: 

* Gestiona l'accés al medi:
  * Beacons: Sincronització, No hi ha retard, Estructura Supertrama (superframe), CDSMA/CA
  * Sense: Hi ha retard, CSMA/CA
* Fiabilitat: Opcional (Akn)
* Associació: Procediment x accedir a la xarxa
* Seguretat: Sí
* Superframe: 15ms-245s. B-CAP-CFP-Idle Period
* Connexió a internet: Sí











## 4.4 6LoWPAN (IPv6 Low Power WPAN)

Mecanismes:

* Autoconfigurador d'adreces
* Compressió capçalera
* Format Trama
* Fragmentació
* Optimització Neighbor Discovery

Autoconfigurador d'adreces:	     64bytes + 64bytes

* Prefix xarxa: Global/Local
* Interface ID: MAC 802.15.4 (Llarga/curta)

Mides missatge:     -> Compressió capçalera i Fragmentació.

+ IpV6: 1280 bytes
+ 802.15.4: 127 bytes





## 4.5 RPL (Ripple)

Neix de la necessitat d'utilitzar un protocol d'encaminament route-over basat en IP.

**IPv6 Routing Protocol for Low Power and Lossy Networks**

Tipologia DAG (graf acíclic) optimitzat per:

* MP2P
* P2MP
* P2P (Subòptim)

Hi ha una Arrel i cada salt s'incrementa el Rank

Els nodes envien periòdicament missatges DIO (Dodag Info Object)  ( ="Hello")

Incorporació d'un node: (quan sap la info, sap qui són els seus veins i designa Default Parent)

* Espera rebre DIO, o
* Envia un DIS (Dodag Info Solicitation)

Objective Function (OF) -> Mitjantçan mètrica i restriccions, permet triar a un node el seu Default Parent.

Rutes:

* Upward: Node envia info al Def. Parent
* Downward: Nodes envien DAO (Dodag Advertisement Object) al Def. Parent (akn opt) fins l'arrel, que:
  * Storing Mode: Els nodes intermitjos guarden taula d'encaminament (Destí, Next Hop)
  * Non Storing Mode: Només l'arrel té guarda la taula. En la capçelera hi han els nodes intermitjos.













## 4.6 CoAP (Constrained Application Protocol)

HTTP ->> inadecuat x restriccions de xarxa:

* Missatges massa llargs
* Massa BW, memòria, energia sensors, no suporta sleep nodes.

CoAP es basa en **UDP**:

* Model REST (Servidor- client)
* 2 subcapes:
  * Petició - Resposta: GET, POST, PUT, DELETE
  * Missatges: CON, NON, AKN, RST

Format missatges:

* Capçalera entre 4bytes i 32 bytes (max )
* Missatge de 16bytes

Tipus de resposta:

* Piggybacked: Akn + Data -> = missatge
* Separada: Akn i Data -> different missatge

Caché que guarda peticions (així no ha de demanar-la més)

Proxy: Agent substitutiu que actua en nom d'una altra persona/entitat. Pot fer de Servidor o Client

Oberve: Si un node es vol subscriure a un servidor que notifiqui canvis del seu recurs -> GET (Observe)

