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

const ENEMY_REGISTRY = {
    "SABER WOLF": {
        model: "wolf", color: 0xff3333,
        hp: (lvl) => 15 + (lvl * 4), atk: (lvl) => 4 + Math.floor(lvl * 1.5), expValue: 6,
        actions: [{ type: "attack", text: "THE WOLF BITES!", mod: 1.0 }]
    },
    "IRON GOLEM": {
        model: "golem", color: 0xaa5533,
        hp: (lvl) => 25 + (lvl * 5), atk: (lvl) => 6 + Math.floor(lvl * 1.5), expValue: 12,
        actions: [{ type: "attack", text: "THE GOLEM SMASHES!", mod: 1.2 }]
    },
    "VOID WRAITH": {
        model: "wraith", color: 0x33ffff,
        hp: (lvl) => 18 + (lvl * 3), atk: (lvl) => 5 + Math.floor(lvl * 1.5), expValue: 10,
        actions: [{ type: "attack", text: "THE WRAITH SIPHONS!", mod: 1.0 }, { type: "heal", text: "WRAITH REGENERATES!", val: 8 }]
    },
    "PLAGUE STALKER": {
        model: "wolf", color: 0x75ff33,
        hp: (lvl) => 16 + (lvl * 4), atk: (lvl) => 5 + Math.floor(lvl * 1.5), expValue: 9,
        actions: [{ type: "attack", text: "TOXIC BITE!", mod: 1.1 }]
    }
};

const geometries = {
    room: new THREE.IcosahedronGeometry(1.8, 1),
    wolf: new THREE.TetrahedronGeometry(1.8, 0),
    golem: new THREE.BoxGeometry(2, 2, 2),
    wraith: new THREE.TorusKnotGeometry(1, 0.3, 64, 8),
    chest: new THREE.DodecahedronGeometry(1.3, 0),
    merchant: new THREE.ConeGeometry(1.3, 2.5, 5),
    scroll: new THREE.CylinderGeometry(0.3, 0.3, 1.5, 12)
};
```
2. then put that code in an issue
2,5. if you add new enemies and want new geometries, look [here.](https://threejs.org/docs/#BoxGeometry)
3. I'll revieuw it and might add it in
4. SUCCESS
