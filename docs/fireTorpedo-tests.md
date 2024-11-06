## `fireTorpedo`

|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               |  |
|Előfeltételek (kiindulási állapot) |  |
|A teszt lépései                    |  |
|Elvárt kimenet/eredmény            |  |

---

### 1.1 (`input-1.txt`)
|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | a SINGLE firingMode az elsődleges torpedót lövi ki először |
|Előfeltételek (kiindulási állapot) | mindkét tárban van 1-1 torpedó, de az elsődleges tárban lévő hibás |
|A teszt lépései                    | - tárak feltöltése `GT4500,1,1,1,0` <br/> - tüzelés `TORPEDO,SINGLE` <br/> - tüzelés `TORPEDO,SINGLE` |
|Elvárt kimenet/eredmény            | a tüzelés először sikertelen (először az elsődleges tárat próbálja), majd sikeres |

|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | a SINGLE firingMode alternálva lő torpedókat |
|Előfeltételek (kiindulási állapot) | az elsődleges tárban 2 jó torpedó, a másodlagosban 1 hibás torpedó van |
|A teszt lépései                    | - tárak feltöltése `GT4500,2,0,1,1` <br/> - tüzelés `TORPEDO,SINGLE` <br/> - tüzelés `TORPEDO,SINGLE` <br/> - tüzelés `TORPEDO,SINGLE` |
|Elvárt kimenet/eredmény            | a második tüzelésen kívül mindegyik sikeres, mert a második torpedó a másodlagos tárban van és hibás |


### 1.2 (`input-1.txt`)
|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | SINGLE firingMode-nál ha üres a másodlagos tár, az elsődlegesből próbálunk lőni |
|Előfeltételek (kiindulási állapot) | van 2 torpedó az elsődleges tárban |
|A teszt lépései                    | - tárak feltöltése `GT4500,2,0,0,0` <br/> - tüzelés `TORPEDO,SINGLE` <br/> - tüzelés `TORPEDO,SINGLE` <br/> |
|Elvárt kimenet/eredmény            | mindkét torpedó tüzelésre kerül az elsődleges tárból |

### 1.3 (`input-2.txt`)
|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | SINGLE firingMode-nál az üres tárakból nem próbálunk tüzelni |
|Előfeltételek (kiindulási állapot) | csak az elsődleges tárban 2 torpedó van, és még nem történt lövés |
|A teszt lépései                    | - elsődleges tár feltöltése `GT4500,2,0,0,0` <br/> - tüzelés `TORPEDO,SINGLE` <br/> - tüzelés `TORPEDO,SINGLE` |
|Elvárt kimenet/eredmény            | mindkét lövés az elsődleges tárból lett kilőve, így az 0 torpedó marad |

|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | SINGLE firingMode-nál az üres tárakból nem próbálunk tüzelni |
|Előfeltételek (kiindulási állapot) | csak a másodlagos tárban van torpedó, és még nem történt lövés |
|A teszt lépései                    | - elsődleges tár feltöltése `GT4500,0,0,1,0` <br/> - tüzelés `TORPEDO,SINGLE` <br/> |
|Elvárt kimenet/eredmény            | a másodlagos tár kiürül, mert az elsődlegesből nem lehetett tüzelni |


### 1.4 (`input-3.txt`)
|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | SINGLE firingMode-nál az a hibás tüzelésnél nem lövünk a másik tárból |
|Előfeltételek (kiindulási állapot) | mindkét tárban 1-1 torpedó van, de az elsődleges tár mindig meghibásodik, és még nem történt lövés |
|A teszt lépései                    | - tárak feltöltése `GT4500,1,1,1,0` <br/> - tüzelés `TORPEDO,SINGLE` <br/> - tüzelés `TORPEDO,SINGLE` |
|Elvárt kimenet/eredmény            | az első tüzelés hiba miatt sikertelen, de a második nem |

### 2.1 (`input-4.txt`)
|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | ALL firingMode-nál mindkettő tárból tüzelünk |
|Előfeltételek (kiindulási állapot) | mindkét tárban 1-1 torpedó van |
|A teszt lépései                    | - tárak feltöltése `GT4500,1,0,1,0` <br/> - tüzelés `TORPEDO,ALL` |
|Elvárt kimenet/eredmény            | mindkét tár kiürül |

|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | ALL firingMode-nál mindkettő tárból tüzelünk |
|Előfeltételek (kiindulási állapot) | az elsődleges tárban nincs torpedó, a másodlagosban 1 torpedó van |
|A teszt lépései                    | - tárak feltöltése `GT4500,0,0,1,0` <br/> - tüzelés `TORPEDO,ALL` |
|Elvárt kimenet/eredmény            | a másodlagos tár kiürül |

### cov-1 (`input-5.txt`)

|                                   |  |
|:----------------------------------|:-|
|Tesztelt követelmény               | ALL firingMode teljesen üres tárral |
|Előfeltételek (kiindulási állapot) | teljesen üres tárak |
|A teszt lépései                    | - hajó létrehozása `GT4500,0,0,0,0` <br/> - tüzelés `TORPEDO,ALL` |
|Elvárt kimenet/eredmény            | a tüzelés sikertelen |
