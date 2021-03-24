# Quail Hatching

## Step 1

It's quail hatching season! The quail are laying eggs left 
and right; let's catch them and put them back into the 
quail coop. 

First, check out the code in the workspace. You can move your 
quail-catching glove with the buttons. Use the **arrow keys** or 
**joystick** to try it out in the simulator.

## Step 2

Let's catch some birds! 

Drag an ``||sprites:on [sprite] of kind [Player] overlaps [othersprite] of kind [Player]||`` 
container into the workspace. Change the second argument to 
``||sprites:Quail||``.

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Quail, function (sprite, otherSprite) {
})
```

## Step 3
Now, when you grab the quail, it should start following you. 

From the ``||sprites:Sprites||`` drawer, drag a 
``||sprites:set [myEnemy] follow [mySprite] ⊕||`` block into the bottom
of the **overlaps** container.

Click on the ``||variables:otherSprite||`` variable from the top of the 
**overlaps** container and drag it down to replace the 
``||variables:mySprite||`` argument.

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
}
let mySprite: Sprite = null;
sprites.onOverlap(SpriteKind.Player, SpriteKind.Quail, function (sprite, otherSprite) {
    otherSprite.follow(mySprite, 70)
})
```

## Step 4
The quail are still laying eggs, even when you've caught them! That's a 
little troublesome. 

From the ``||sprites:Sprites||`` drawer, drag a ``||sprites: set [mySprite] kind to [Player]||``
to the bottom of the **overlaps** container. Drag another
``||variables:otherSprite||`` variable from the top of the 
**overlaps** container to replace the ``||variables:mySprite||`` 
argument, and change the kind to **Caught**.
Only sprites that are of kind **Quail** can lay eggs!

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
Finally, we need to put the quail back into the coop.

This time, go into the ``||scene:Scene||`` category and drag out a 
``||scene:on [sprite] of kind [Player] overlaps [ ] at [location]||`` container.
Change **Player** to **Caught**, and change the empty tile to the **coop** tile.

```blocks
namespace SpriteKind {
    export const Quail = SpriteKind.create()
    export const Caught = SpriteKind.create()
}
scene.onOverlapTile(SpriteKind.Caught, assets.tile`myTile`, function (sprite, location) {

})
```


## Step 6
Next, grab a ``||sprites:destroy [mySprite] ⊕||`` block and put it in the 
overlaps container. 

Click on the ``||variables:sprite||`` variable from the top of the 
**overlaps** container and drag it down to replace the 
``||variables:mySprite||`` argument.

Drag some quail over to the coop and see what happens!

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
Almost done--now you just have to deal with the pesky leftover quail eggs.

Right-click on your ``||sprites:on [sprite] of kind [Player] overlaps [othersprite] of kind [Quail]||`` 
container and select **Duplicate**. Then change the second 
argument from **Quail** to **Egg**.

Use the simulator to see how fast you can clear out the quail!

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