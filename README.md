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
        },
        minDepth: 5
        // forceDepth: 10
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
    "IRON GOLEM": {
        model: "golem", color: 0xaa5533,
        hp: (lvl) => 25 + (lvl * 5), atk: (lvl) => 6 + Math.floor(lvl * 1.5), expValue: 12,
        actions: [{ type: "attack", text: "THE GOLEM SMASHES!", mod: 1.2 }],
        drops: function() {grantEquipment();},
        dropChance: 0.5
    },
};

const geometries = {
    name: new THREE.IcosahedronGeometry(1.8, 1) //a three js geometry ALSO DO THIS IF YOU USE AN OBJ, used for fallback
};

loadCustomGeometry("name", "assets/path");

const GAMBLE_GAMES = [
    {
        name: "COIN FLIP",
        action: function(input) {
            var gain = input
            var cum = Math.random()
            console.log(cum);
            if (cum <= 0.5) {
                gain = Math.floor(gain*1.5)
                UI.prompt.innerText = `HEADS, MADE ${gain}`
                UI.actions.innerHTML = `
                    <button id="goAgainBtn" class="btn-atk">GO AGAIN</button>
                    <button id="cashOutBtn" class="btn-pot">CASH OUT (${gain})</button>
                `
                document.getElementById("goAgainBtn").addEventListener("click", () => {
                    GAMBLE_GAMES[0].action(gain)
                });
                document.getElementById("cashOutBtn").addEventListener("click", () => {
                    gold += gain;
                    updateHUD();
                    UI.actions.style.display = "none"; setTimeout(buildChoiceEnvironment, 1000);
                });
            } else {
                gain = 0
                UI.prompt.innerText = `TAILS, LOST EVERYTHING`
                UI.actions.innerHTML = ``
                updateHUD();
                UI.actions.style.display = "none"; setTimeout(buildChoiceEnvironment, 1000);
            }
        },
        min: 2
    }
];

```
2. then put that code in an issue (if you add new enemies and want new geometries, look [here.](https://threejs.org/docs/#BoxGeometry))
3. I'll review it and might add it in
4. SUCCESS
