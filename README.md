this is just a part of my main website at [this link](https://moos4.github.io) and [this repo](https://github.com/moos4/moos4.github.io/)

## want to add stuff to the rogue-like?
1. make the code for it using this base:
``` 
const ALL_SPELLS = [
    { id: "fireball", name: "🔥 FIREBALL", cost: 6, baseDmg: 18, color: "rgba(255,68,0,0.4)" },
    { id: "ice", name: "❄️ ICE LANCE", cost: 5, baseDmg: 14, color: "rgba(0,200,255,0.4)" },
    { id: "drain", name: "🌿 DRAIN SOUL", cost: 8, baseDmg: 12, heals: 10, color: "rgba(50,255,50,0.4)" },
    { id: "void", name: "🌌 VOID CRUSH", cost: 12, baseDmg: 35, color: "rgba(150,0,255,0.4)" }
];

const EQUIPMENT_REGISTRY = {
    weapons: [
        { name: "STEEL SWORD", baseAtk: 4 },
        { name: "WARHAMMER", baseAtk: 6 },
        { name: "BATTLE AXE", baseAtk: 8 },
        { name: "OBSIDIAN BLADE", baseAtk: 12 },
        { name: "VOID SCYTHE", baseAtk: 15 }
    ],
    armors: [
        { name: "CHAINMAIL", baseDef: 3 },
        { name: "IRON PLATE", baseDef: 5 },
        { name: "DRAGON SCALE", baseDef: 8 },
        { name: "SHADOW CLOAK", baseDef: 12 },
        { name: "AEGIS ARMOR", baseDef: 15 }
    ]
};

const ROOM_POOL = [
    {
        name: "Shattered Armory", chance: 25, color: 0xaa5533,
        action: function() {
            if (Math.random() < 0.6) battleEnemy("IRON GOLEM");
            else grantEquipment();
        }
    },
    {
        name: "Fae Glade Ruins", chance: 20, color: 0x33ff99,
        action: function() {
            if (Math.random() < 0.5) healPlayer(20, "YOU RESTED IN THE FAE GLADE");
            else battleEnemy("PLAGUE STALKER");
        }
    },
    {
        name: "Cursed Burial Grounds", chance: 25, color: 0xff3333,
        action: function() { battleEnemy("SABER WOLF"); }
    },
    {
        name: "Strange Bazaar", chance: 20, color: 0xffaa00,
        action: function() { openShop(); }
    },
    {
        name: "Sunken Library", chance: 15, color: 0xe066ff,
        action: function() {
            if (Math.random() < 0.3) battleEnemy("VOID WRAITH");
            else grantSpellScroll();
        }
    }
];
/*
funcs:
battleEnemy("name")
healPlayer(amount: int, "text")
grantEquipment()
openShop()
grantSpellScroll()
*/
const ENEMY_REGISTRY = {
    "SABER WOLF": {
        model: "wolf", color: 0xff3333,
        hp: (lvl) => 15 + (lvl * 4), atk: (lvl) => 4 + Math.floor(lvl * 1.5), expValue: 6,
        actions: [{ type: "attack", text: "THE WOLF BITES!", mod: 1.0 }]
    }
};

const geometries = {
    name: new THREE.IcosahedronGeometry(1.8, 1) //a three js geometry ALSO DO THIS IF YOU USE AN OBJ, used for fallback
};

loadCustomGeometry("name", "assets/path");
```
2. then put that code in an issue (if you add new enemies and want new geometries, look [here.](https://threejs.org/docs/#BoxGeometry))
3. I'll review it and might add it in
4. SUCCESS
