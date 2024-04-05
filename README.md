# Metro
 Jednoduchý plugin pro metro v Minecraftu

## Použití (How to use)

#### 1. Umístěte nástěnnou cedulku nad koleje a upravte ji, jak je uvedeno níže.

Formát

```
[Metro]
(string) <-- Název linky
(number+[N|S|W|E]) <-- Index stanice ve směru linky další stanice
(string) <-- Název stanice
```

Příklad

```
[Metro]
Linka1
1S
Hlavní nádraží
```

> [!NOTE]
> **To znamená:**
> 
> Stanice leží na lince `Linka1` .
> 
> Jedná se o 2. stanici na lince `Linka1` (počítáno od 0).
> 
> Do další stanice jede vozík na jih.
> 
> Tato stanice se jmenuje `Hlavní nádraží`.

#### 2. Chcete-li vybrat stanice, klikněte pravým tlačítkem na značku s itemem v ruce.

#### 3. Klikněte pravým tlačítkem na cedulku prázdnou rukou nebo se shiftem, abyste vytvořili vozík.

#### 4. Vstupte do vozíku (automaticky se rozjede) a užijte si výlet.

#### 5. Když vystoupíte z vozíku, bude automaticky odstraněn.

#### 6. Chcete-li nastavit linku smyčky (loop), použijte příkaz.

Použijte `/metro loop [NazevLinky]` pro kontrolu, zda je linka ve smyčce.

Použijte `/metro loop [NazevLinky] [true|false]` pro přepnutí linky na smyčku / přímou linku.

#### 7. Chcete-li změnit výchozí rychlost linky metra, použijte příkaz.

Automaticky zrychluje generovaný vozík, když jede po dlouhém souvislém úseku poháněných kolejí (Powered Rails).

Použijte `/metro speed [NazevLinky]` pro zobrazení aktuální rychlosti linky metra.

Použijte `/metro speed [NazevLinky] [DesetinneCislo]` změnit rychlost linky metra.

Výchozí rychlost poháněných kolejí: `0.4`.

Doporučená maximální rychlost: Ne více než `2.0`.

### Nová funkce: Router (vyšší verze 1.4)

Umístěte nástěnnou cedulku pod kolej

```
_____*___
#########
####]####
```

> [!NOTE]
> `_` je poháněná kolej, `*` je kolej používaná pro router, `]` je nástěnná cedulka, `#` jsou jakékoliv bloky, tvar kolejí se změní, když přijede vozík.

> [!WARNING]
> Použije se pouze nástěnná cedulka, která je ve směru, kam vozík přijíždí.

Poté jí upravte, jak je uvedeno níže.

```
[Metro:router]
(string) <-- pravidlo
(string) <-- pravidlo
(string) <-- pravidlo
```

Můžete přidat až 3 pravidla.

Příklad pravidel:

```
0-3,6,9SW
4,5N
SE
```

> [!NOTE]
> **To znamená:**
> 
> - Když dorazí vozík, jehož cílem je stanice 0, 1, 2, 3, 6, 9, tvar kolejnice se změní na `SW` (tvar, který se připojuje k jižní a západní koleji).
> 
> - Když dorazí vozík, jehož cílem je stanice 4, 5, tvar kolejnice se změní na `N` (tvar, který se připojuje k severu a jihu) (protože `N` se rovná `S`, můžete pokud chcete, použijte `S`).
> 
> - Když dorazí vozík, jehož cíl není uveden výše, tvar kolejnice se změní na `SE` (tvar, který se připojuje k jižní a východní koleji).

Pokud nenastavíte výchozí pravidlo (jako `SE`, žádné číslo před směrem), kolejnice se nezmění.

Podporovány jsou také `AE` (vzestupně na východ - ASCEND), `AS`, `AW`, `AN`, `DE` (sestupně na východ - DESCEND), `DS`, `DW`, `DN`.

> [!WARNING]
> Použijte prosím různé koleje ve stanici metra (v blízkosti), abyste zabránili tomu, aby vozík jel příliš rychle a nezastavil na stanici. Akcelerace bude ignorovat router.

## Oprávnění (Permissions)

### metro.reload

- Znovu načíst konfiguraci pluginu.

- Povolit/zakázat režim ladění.
  
Výchozí: OP

### metro.speed

- Změnit rychlost linky metra.

Výchozí: OP

### metro.create

- Vytvořit nový router.

- Vytvořit novou stanici / linku metra.

- Odstranit stanici / linku metra.

Výchozí: OP

### metro.use

- Použít stanici metra.

Výchozí: Všichni hráči
