# Quail Hatching

## Step 1

It's quail hatching season! The quail are laying eggs left 
and right; let's help catch them and put them back into the 
quail coop. First, check out the code in the workspace! You 
have a quail-catching glove that you control with the buttons.
Try moving it around the simulator using the arrow keys or 
joystick.

## Step 2

Let's catch some birds! 
- ``||sprites:on [sprite] of kind [Player] overlaps [othersprite] of kind [Player]||``
- Change the last argument from ``||sprites:Player||`` to ``||sprites:Quail||``

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Quail, function (sprite, otherSprite) {
})
```

## Step 3
- ``||sprites: set [myEnemy] follow [mySprite]||``

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Quail, function (sprite, otherSprite) {
    otherSprite.follow(sprite, 70)
})
```

## Step 4
- Still laying eggs! 
- ``||sprites: set [mySprite] kind to [Player]||``
- Change the kind to **Caught**

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
    export const Caught = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Quail, function (sprite, otherSprite) {
    otherSprite.follow(sprite, 70)
    otherSprite.setKind(SpriteKind.Caught)
})
```

## Step 5
- Put quail back in coop
- ``||scene:on [sprite] of kind [Player] overlaps [ ] at [location]||``
- Change **Player** to **Caught**
- Change the empty tile to the *coop*
- Drag some quail over and see what happens!

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
    export const Caught = SpriteKind.create()
}
scene.onOverlapTile(SpriteKind.Caught, assets.tile`myTile`, function (sprite, location) {

})
```


## Step 6
- ``||sprite:destroy [mySprite]||``
- Drag ``||variables:sprite||`` block in

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
    export const Caught = SpriteKind.create()
}
scene.onOverlapTile(SpriteKind.Caught, assets.tile`myTile`, function (sprite, location) {
    sprite.destroy()
})
```

## Step 7
- Should also be able to pick up eggs! 
- Right click on your overlaps block and duplicate
- Change **Quail** to **Egg**

```blocks
namespace SpriteKind {
    export const Egg = SpriteKind.create()
    export const Caught = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Egg, function (sprite, otherSprite) {
    otherSprite.follow(sprite, 70)
    otherSprite.setKind(SpriteKind.Caught)
})
```

```template
tiles.setTilemap(tilemap`level1`)
let mySprite = sprites.create(img`
. . . . . 8 8 . 8 6 . 8 6 . . . 
. . . . 8 6 6 8 6 7 8 6 7 6 . . 
. . . . 8 7 7 8 6 6 8 6 7 6 . . 
. . . . 8 6 6 8 6 6 8 6 6 8 f . 
. . . . 8 7 7 f 7 7 f 7 7 f 7 6 
. . . . f 7 7 f 7 7 f 7 7 f 7 6 
. . 8 8 f 6 6 f 6 6 f 6 6 f 7 6 
. 8 6 6 f 6 6 6 6 6 6 6 6 6 6 8 
. 8 6 6 f 6 6 6 6 6 6 6 6 6 6 8 
. f 6 6 6 6 6 6 6 6 6 6 6 6 6 f 
. f 6 6 6 6 6 6 6 6 6 6 6 6 7 f 
. . f 7 7 7 7 7 7 7 7 7 7 7 7 f 
. . . f 7 7 7 7 7 7 7 7 7 7 f . 
. . . f 8 7 7 7 7 7 7 7 7 6 f . 
. . . . f 8 6 6 6 6 6 6 6 6 8 . 
. . . . . f f f f 8 8 8 8 8 . . 
`, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.z = 15
```

```assetjson
{
  "README.md": " ",
  "assets.json": "",
  "images.g.jres": "{\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myImages\"\n    }\n}",
  "images.g.ts": "// Auto-generated code. Do not edit.\nnamespace myImages {\n\n    helpers._registerFactory(\"image\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"animation\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n",
  "main.blocks": "<xml xmlns=\"https://developers.google.com/blockly/xml\"><variables><variable id=\"L!cB4n[Bh=tH5MB4X7AR\">quail</variable><variable id=\":]K1S=^Y/9o]Qxj@,sa}\">value</variable><variable id=\"jaXL.M23_0@z]e_lq:-C\">quail_egg</variable><variable type=\"KIND_SpriteKind\" id=\"fPMHg^KS.0yOx68`FD8T\">Player</variable><variable type=\"KIND_SpriteKind\" id=\"OB*c;zAa9qM%e+.]FLtj\">Projectile</variable><variable type=\"KIND_SpriteKind\" id=\"t]C,0].{is.)C.gs!LD*\">Food</variable><variable type=\"KIND_SpriteKind\" id=\"0Uq(~g:5~-|dk4,Q#^/r\">Enemy</variable></variables><block type=\"pxt-on-start\" x=\"0\" y=\"0\"><statement name=\"HANDLER\"><block type=\"tilemap_editor\"><field name=\"tilemap\">tilemap`level1`</field><data>{\"commentRefs\":[],\"fieldData\":{\"tilemap\":\"level1\"}}</data></block></statement></block></xml>",
  "main.ts": "tiles.setTilemap(tilemap`level1`)\n",
  "pxt.json": "{\n    \"name\": \"Quail Hatching\",\n    \"description\": \"\",\n    \"dependencies\": {\n        \"device\": \"*\"\n    },\n    \"files\": [\n        \"main.blocks\",\n        \"main.ts\",\n        \"README.md\",\n        \"assets.json\",\n        \"tilemap.g.jres\",\n        \"tilemap.g.ts\",\n        \"images.g.jres\",\n        \"images.g.ts\"\n    ],\n    \"targetVersions\": {\n        \"branch\": \"v1.3.49\",\n        \"tag\": \"v1.3.49\",\n        \"commits\": \"https://github.com/microsoft/pxt-arcade/commits/cc243b20c0547dd26f27296be900f62d5c04211b\",\n        \"target\": \"1.3.49\",\n        \"pxt\": \"6.8.37\"\n    },\n    \"preferredEditor\": \"blocksprj\"\n}\n",
  "tilemap.g.jres": "{\n    \"transparency16\": {\n        \"data\": \"hwQQABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"tile1\": {\n        \"data\": \"hwQQABAAAAC9zMzMzMz//6u7u6vMu7vLvLu7u/qZud+8u7u7+pm537y7u7v6mbnfvLu7u/qZud+8u7u7+pm537y7u7v6mbnfvLu7u/qZsd+8u7u7+hm537y7u7v6kbnfvLu7u/qZsd+8u7u7+hmx37y7u7v6Ebnfq7u7q8y7u8u9zMzMzMz//w==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"myTile\"\n    },\n    \"level1\": {\n        \"id\": \"level1\",\n        \"mimeType\": \"application/mkcd-tilemap\",\n        \"data\": \"MTAwYTAwMDgwMDAxMDIwMjAyMDIwMjAyMDIwMjAzMDcwOTBhMDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA4MDUwNjA2MDYwNjA2MDYwNjA2MDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMA==\",\n        \"tileset\": [\n            \"myTiles.transparency16\",\n            \"sprites.castle.tilePath1\",\n            \"sprites.castle.tilePath2\",\n            \"sprites.castle.tilePath3\",\n            \"sprites.castle.tilePath9\",\n            \"sprites.castle.tilePath7\",\n            \"sprites.castle.tilePath8\",\n            \"sprites.castle.tilePath4\",\n            \"sprites.castle.tilePath6\",\n            \"sprites.castle.tilePath5\",\n            \"myTiles.tile1\"\n        ],\n        \"displayName\": \"level1\"\n    },\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myTiles\"\n    }\n}",
  "tilemap.g.ts": "// Auto-generated code. Do not edit.\nnamespace myTiles {\n    //% fixedInstance jres blockIdentity=images._tile\n    export const transparency16 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile1 = image.ofBuffer(hex``);\n\n    helpers._registerFactory(\"tilemap\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"level1\":\n            case \"level1\":return tiles.createTilemap(hex`0a0008000102020202020202020307090a09090909090908070909090909090909080709090909090909090807090909090909090908070909090909090909080709090909090909090805060606060606060604`, img`\n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n`, [myTiles.transparency16,sprites.castle.tilePath1,sprites.castle.tilePath2,sprites.castle.tilePath3,sprites.castle.tilePath9,sprites.castle.tilePath7,sprites.castle.tilePath8,sprites.castle.tilePath4,sprites.castle.tilePath6,sprites.castle.tilePath5,myTiles.tile1], TileScale.Sixteen);\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"tile\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"transparency16\":return transparency16;\n            case \"myTile\":\n            case \"tile1\":return tile1;\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n"
}
```

```package
zoo-extension-projects-activity5=github:shakao-test/zoo-extension/projects/activity5
```