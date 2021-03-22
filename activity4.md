# Feed the Panda

## Step 1 @showdialog

It's feeding time! Everyone's favorite panda is hungry, so let's 
write some code to feed them some tasty bamboo.

## Step 2

First, you'll need to grab some bamboo.
Drag out an `||controller:on A button pressed||` block, and place a 
`||variables:set mySprite to||` block inside it. Make sure to change the 
kind to **Food**, then click on the grey 
square and draw the most delicious piece of bamboo you can.

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    let mySprite = sprites.create(img`
        . . . . . . . . . 6 7 . . . . . 
        . . 7 . . . . . . 6 7 . . . . . 
        . . 7 7 . . . . . 6 6 . . . . . 
        . . 7 7 . . 6 . . 8 8 . . . . . 
        . . 7 7 . . 6 . . 6 7 7 . . . . 
        . . 6 7 6 . 6 . . 6 7 7 . . . . 
        . . 6 6 7 . 6 . . 6 7 7 6 7 7 . 
        7 7 8 8 7 6 6 . . 6 7 7 7 7 . . 
        . . 7 7 7 6 . 6 . 6 6 7 6 . . . 
        . . . 8 6 6 . 6 . 8 7 8 8 . . . 
        . . . 6 6 6 . 6 . 6 7 7 6 . . . 
        . . . 6 6 7 . . 6 . 7 7 . 7 . . 
        . . . 6 6 6 6 6 6 . 7 6 7 . . . 
        . . . . 8 8 8 . . . 6 6 . . . . 
        . . . . 6 7 6 . 7 7 6 6 . . . . 
        . . . . 6 6 6 . . 7 6 . . . . . 
        `, SpriteKind.Food)
})
```

## Step 3

Now, throw it into the panda enclosure! From the `||scene:Scene||`
drawer, pull out a ``||scene: place mySprite on top of random||``
block and select the brown dirt tile. This will **place** the 
bamboo sprite on a **random** patch of dirt.

```blocks
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    let mySprite = sprites.create(img`
        . . . . . . . . . 6 7 . . . . . 
        . . 7 . . . . . . 6 7 . . . . . 
        . . 7 7 . . . . . 6 6 . . . . . 
        . . 7 7 . . 6 . . 8 8 . . . . . 
        . . 7 7 . . 6 . . 6 7 7 . . . . 
        . . 6 7 6 . 6 . . 6 7 7 . . . . 
        . . 6 6 7 . 6 . . 6 7 7 6 7 7 . 
        7 7 8 8 7 6 6 . . 6 7 7 7 7 . . 
        . . 7 7 7 6 . 6 . 6 6 7 6 . . . 
        . . . 8 6 6 . 6 . 8 7 8 8 . . . 
        . . . 6 6 6 . 6 . 6 7 7 6 . . . 
        . . . 6 6 7 . . 6 . 7 7 . 7 . . 
        . . . 6 6 6 6 6 6 . 7 6 7 . . . 
        . . . . 8 8 8 . . . 6 6 . . . . 
        . . . . 6 7 6 . 7 7 6 6 . . . . 
        . . . . 6 6 6 . . 7 6 . . . . . 
        `, SpriteKind.Food)
    tiles.placeOnRandomTile(mySprite, sprites.castle.tilePath5)
})
```

## Step 4

Munch time! Grab a ``||sprites:on sprite overlaps||`` block and drag 
it into the workspace. Change the first dropdown to **Animal** and the 
second to **Food**. We want to run this code when the panda (Animal) 
overlaps your bamboo (Food).

```blocks
namespace SpriteKind {
    export const Animal = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Animal, SpriteKind.Food, function (sprite, otherSprite) {
})
```

## Step 5

Next, grab a ``||sprites:destroy mySprite||`` block from the `||sprites:Sprites||`
drawer and put it in the overlaps. The panda destroys the food it eats!
To tell the **destroy** block that you want it to affect the overlapping food, 
click on the ``||variables:otherSprite||`` variable from the top of the 
**overlaps** container and drag it down to replace the 
``||variables:mySprite||`` argument in ``||sprites:destroy [mySprite] ⊕||``.

```blocks
namespace SpriteKind {
    export const Animal = SpriteKind.create()
}
sprites.onOverlap(SpriteKind.Animal, SpriteKind.Food, function (sprite, otherSprite) {
    otherSprite.destroy()
})
```

## Step 6

All right, the panda's getting fed! But they're not very good at finding 
the food... let's help them out! From the `||sprites:Sprites||` 
drawer, drag a `||sprites:set myEnemy follow mySprite||` block into your
`||controller:on A button pressed||` container. Change
the first variable to `||variables:panda||`. Use the spacebar to 
drop some bamboo in and watch that panda go!

```blocks
let panda:Sprite = null;
controller.A.onEvent(ControllerButtonEvent.Pressed, function () {
    let mySprite = sprites.create(img`
        . . . . . . . . . 6 7 . . . . . 
        . . 7 . . . . . . 6 7 . . . . . 
        . . 7 7 . . . . . 6 6 . . . . . 
        . . 7 7 . . 6 . . 8 8 . . . . . 
        . . 7 7 . . 6 . . 6 7 7 . . . . 
        . . 6 7 6 . 6 . . 6 7 7 . . . . 
        . . 6 6 7 . 6 . . 6 7 7 6 7 7 . 
        7 7 8 8 7 6 6 . . 6 7 7 7 7 . . 
        . . 7 7 7 6 . 6 . 6 6 7 6 . . . 
        . . . 8 6 6 . 6 . 8 7 8 8 . . . 
        . . . 6 6 6 . 6 . 6 7 7 6 . . . 
        . . . 6 6 7 . . 6 . 7 7 . 7 . . 
        . . . 6 6 6 6 6 6 . 7 6 7 . . . 
        . . . . 8 8 8 . . . 6 6 . . . . 
        . . . . 6 7 6 . 7 7 6 6 . . . . 
        . . . . 6 6 6 . . 7 6 . . . . . 
        `, SpriteKind.Food)
    tiles.placeOnRandomTile(mySprite, sprites.castle.tilePath5)
    panda.follow(mySprite)
})
```



```template
namespace SpriteKind {
    export const Animal = SpriteKind.create()
}
tiles.setTilemap(tilemap`level1`)
let panda = sprites.create(img`
    . . . . . . . 1 1 1 1 1 . . . . 
    . f f f . . f f f 1 1 1 1 1 . . 
    f f f 1 1 1 f f f 1 1 1 1 1 1 . 
    f 1 1 1 1 1 1 1 f 1 1 1 1 1 1 1 
    . 1 f f 1 1 f f 1 f 1 1 1 1 1 1 
    . 1 f f 1 1 f f 1 f 1 1 1 1 1 1 
    . 1 1 1 1 1 1 1 1 f f 1 1 1 1 1 
    . . 1 1 1 1 1 1 1 f f 1 1 1 1 1 
    . . f f 1 1 1 f f f f 1 1 1 1 1 
    . . f f f . f f f f f 1 1 1 f f 
    . . f f f . f f f f f 1 1 1 f f 
    . . f f f . . f f f f 1 1 f f f 
    . . f f f . . . f f f . . f f f 
    . . f f f . . . f f f . f f f . 
    . . . f f . . . f f . . f f f . 
    . . . f f . . . f f . . f f . . 
    `, SpriteKind.Animal)
panda.setVelocity(randint(50, 70), randint(50, 70))
panda.setBounceOnWall(true)
panda.z = 10


```

```assetjson
{
  "README.md": " ",
  "assets.json": "",
  "images.g.jres": "{\n    \"image1\": \"hwQQABAAAAAA/wAAAAAAAPAfEQEAAAAA8B//Ef///wDwEf8R/////wARERHx////ABEREQEAAADwH/8R8Q8AAPEf/xH//wAA8f8REf////8REf///////xEREf////8AERERERERAAAQERERERHw/xARERER8f//ABEREfH//w8AEBER8f8PAA==\",\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myImages\"\n    }\n}",
  "images.g.ts": "// Auto-generated code. Do not edit.\nnamespace myImages {\n\n    helpers._registerFactory(\"image\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"image1\":return img`\n. . . . . . . 1 1 1 1 1 . . . . \n. f f f . . f f f 1 1 1 1 1 . . \nf f f 1 1 1 f f f 1 1 1 1 1 1 . \nf 1 1 1 1 1 1 1 f 1 1 1 1 1 1 1 \n. 1 f f 1 1 f f 1 f 1 1 1 1 1 1 \n. 1 f f 1 1 f f 1 f 1 1 1 1 1 1 \n. 1 1 1 1 1 1 1 1 f f 1 1 1 1 1 \n. . 1 1 1 1 1 1 1 f f 1 1 1 1 1 \n. . f f 1 1 1 f f f f 1 1 1 1 1 \n. . f f f . f f f f f 1 1 1 f f \n. . f f f . f f f f f 1 1 1 f f \n. . f f f . . f f f f 1 1 f f f \n. . f f f . . . f f f . . f f f \n. . f f f . . . f f f . f f f . \n. . . f f . . . f f . . f f f . \n. . . f f . . . f f . . f f . . \n`;\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"animation\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n",
  "main.blocks": "<xml xmlns=\"https://developers.google.com/blockly/xml\"><variables><variable type=\"KIND_SpriteKind\" id=\"*(U`8Cz%UdX%QVrRLAj]\">Player</variable><variable type=\"KIND_SpriteKind\" id=\",p#pZ[t5Tx3AJuLMboP?\">Projectile</variable><variable type=\"KIND_SpriteKind\" id=\"YMZp[xD?jgxk5yDV=q;C\">Food</variable><variable type=\"KIND_SpriteKind\" id=\"M;=(qFqSV|s///LTH|kZ\">Enemy</variable><variable type=\"KIND_SpriteKind\" id=\"s%O)x$i~/?,4ZPs%k;E5\">Animal</variable><variable id=\"|2r#YO`9Pls^yzC3lc4/\">panda</variable><variable id=\"A)F#HAC#}PGF8r].R!k@\">bamboo</variable><variable id=\"sd/oyN~_[Y/M*O1?~z[U\">mySprite</variable><variable id=\"lvyeJH`H_zT4C_`*RWL`\">myEnemy</variable></variables><block type=\"pxt-on-start\" x=\"0\" y=\"0\"><statement name=\"HANDLER\"><block type=\"tilemap_editor\"><field name=\"tilemap\">tilemap`level1`</field><data>{\"commentRefs\":[],\"fieldData\":{\"tilemap\":\"level1\"}}</data><next><block type=\"variables_set\"><field name=\"VAR\" id=\"|2r#YO`9Pls^yzC3lc4/\">panda</field><value name=\"VALUE\"><shadow xmlns=\"http://www.w3.org/1999/xhtml\" type=\"math_number\"><field name=\"NUM\">0</field></shadow><block type=\"spritescreate\"><value name=\"img\"><shadow type=\"screen_image_picker\"><field name=\"img\">img`\n. . . . . . . 1 1 1 1 1 . . . . \n. f f f . . f f f 1 1 1 1 1 . . \nf f f 1 1 1 f f f 1 1 1 1 1 1 . \nf 1 1 1 1 1 1 1 f 1 1 1 1 1 1 1 \n. 1 f f 1 1 f f 1 f 1 1 1 1 1 1 \n. 1 f f 1 1 f f 1 f 1 1 1 1 1 1 \n. 1 1 1 1 1 1 1 1 f f 1 1 1 1 1 \n. . 1 1 1 1 1 1 1 f f 1 1 1 1 1 \n. . f f 1 1 1 f f f f 1 1 1 1 1 \n. . f f f . f f f f f 1 1 1 f f \n. . f f f . f f f f f 1 1 1 f f \n. . f f f . . f f f f 1 1 f f f \n. . f f f . . . f f f . . f f f \n. . f f f . . . f f f . f f f . \n. . . f f . . . f f . . f f f . \n. . . f f . . . f f . . f f . . \n`</field><data>{\"commentRefs\":[],\"fieldData\":{\"img\":\"myImages.image1\"}}</data></shadow></value><value name=\"kind\"><shadow type=\"spritekind\"><field name=\"MEMBER\">Animal</field></shadow></value></block></value><next><block type=\"spritesetvel\"><value name=\"sprite\"><block type=\"variables_get\"><field name=\"VAR\" id=\"|2r#YO`9Pls^yzC3lc4/\">panda</field></block></value><value name=\"vx\"><shadow type=\"spriteSpeedPicker\"><field name=\"speed\">50</field></shadow><block type=\"device_random\"><value name=\"min\"><shadow type=\"math_number\"><field name=\"NUM\">50</field></shadow></value><value name=\"limit\"><shadow type=\"math_number\"><field name=\"NUM\">70</field></shadow></value></block></value><value name=\"vy\"><shadow type=\"spriteSpeedPicker\"><field name=\"speed\">50</field></shadow><block type=\"device_random\"><value name=\"min\"><shadow type=\"math_number\"><field name=\"NUM\">50</field></shadow></value><value name=\"limit\"><shadow type=\"math_number\"><field name=\"NUM\">70</field></shadow></value></block></value><next><block type=\"spritesetsetbounceonwall\"><value name=\"sprite\"><block type=\"variables_get\"><field name=\"VAR\" id=\"|2r#YO`9Pls^yzC3lc4/\">panda</field></block></value><value name=\"on\"><shadow type=\"toggleOnOff\"><field name=\"on\">true</field></shadow></value><next><block type=\"Sprite_blockCombine_set\"><field name=\"property\">Sprite.z</field><value name=\"mySprite\"><block type=\"variables_get\"><field name=\"VAR\" id=\"|2r#YO`9Pls^yzC3lc4/\">panda</field></block></value><value name=\"value\"><shadow type=\"math_number\"><field name=\"NUM\">10</field></shadow></value></block></next></block></next></block></next></block></next></block></statement></block></xml>",
  "main.ts": "namespace SpriteKind {\n    export const Animal = SpriteKind.create()\n}\ntiles.setTilemap(tilemap`level1`)\nlet panda = sprites.create(img`\n    . . . . . . . 1 1 1 1 1 . . . . \n    . f f f . . f f f 1 1 1 1 1 . . \n    f f f 1 1 1 f f f 1 1 1 1 1 1 . \n    f 1 1 1 1 1 1 1 f 1 1 1 1 1 1 1 \n    . 1 f f 1 1 f f 1 f 1 1 1 1 1 1 \n    . 1 f f 1 1 f f 1 f 1 1 1 1 1 1 \n    . 1 1 1 1 1 1 1 1 f f 1 1 1 1 1 \n    . . 1 1 1 1 1 1 1 f f 1 1 1 1 1 \n    . . f f 1 1 1 f f f f 1 1 1 1 1 \n    . . f f f . f f f f f 1 1 1 f f \n    . . f f f . f f f f f 1 1 1 f f \n    . . f f f . . f f f f 1 1 f f f \n    . . f f f . . . f f f . . f f f \n    . . f f f . . . f f f . f f f . \n    . . . f f . . . f f . . f f f . \n    . . . f f . . . f f . . f f . . \n    `, SpriteKind.Animal)\npanda.setVelocity(randint(50, 70), randint(50, 70))\npanda.setBounceOnWall(true)\npanda.z = 10\n",
  "pxt.json": "{\n    \"name\": \"Feed the Panda\",\n    \"description\": \"\",\n    \"dependencies\": {\n        \"device\": \"*\"\n    },\n    \"files\": [\n        \"main.blocks\",\n        \"main.ts\",\n        \"README.md\",\n        \"assets.json\",\n        \"tilemap.g.jres\",\n        \"tilemap.g.ts\",\n        \"images.g.jres\",\n        \"images.g.ts\"\n    ],\n    \"targetVersions\": {\n        \"branch\": \"v1.3.49\",\n        \"tag\": \"v1.3.49\",\n        \"commits\": \"https://github.com/microsoft/pxt-arcade/commits/cc243b20c0547dd26f27296be900f62d5c04211b\",\n        \"target\": \"1.3.49\",\n        \"pxt\": \"6.8.37\"\n    },\n    \"preferredEditor\": \"blocksprj\"\n}\n",
  "tilemap.g.jres": "{\n    \"transparency16\": {\n        \"data\": \"hwQQABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"level1\": {\n        \"id\": \"level1\",\n        \"mimeType\": \"application/mkcd-tilemap\",\n        \"data\": \"MTAwYTAwMDgwMDAxMDIwMjAyMDIwMjAyMDIwMjAzMDcwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA4MDcwOTA5MDkwOTA5MDkwOTA5MDgwNzA5MDkwOTA5MDkwOTA5MDkwODA3MDkwOTA5MDkwOTA5MDkwOTA4MDUwNjA2MDYwNjA2MDYwNjA2MDQwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMA==\",\n        \"tileset\": [\n            \"myTiles.transparency16\",\n            \"sprites.castle.tilePath1\",\n            \"sprites.castle.tilePath2\",\n            \"sprites.castle.tilePath3\",\n            \"sprites.castle.tilePath9\",\n            \"sprites.castle.tilePath7\",\n            \"sprites.castle.tilePath8\",\n            \"sprites.castle.tilePath4\",\n            \"sprites.castle.tilePath6\",\n            \"sprites.castle.tilePath5\"\n        ],\n        \"displayName\": \"level1\"\n    },\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myTiles\"\n    }\n}",
  "tilemap.g.ts": "// Auto-generated code. Do not edit.\nnamespace myTiles {\n    //% fixedInstance jres blockIdentity=images._tile\n    export const transparency16 = image.ofBuffer(hex``);\n\n    helpers._registerFactory(\"tilemap\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"level1\":\n            case \"level1\":return tiles.createTilemap(hex`0a0008000102020202020202020307090909090909090908070909090909090909080709090909090909090807090909090909090908070909090909090909080709090909090909090805060606060606060604`, img`\n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n`, [myTiles.transparency16,sprites.castle.tilePath1,sprites.castle.tilePath2,sprites.castle.tilePath3,sprites.castle.tilePath9,sprites.castle.tilePath7,sprites.castle.tilePath8,sprites.castle.tilePath4,sprites.castle.tilePath6,sprites.castle.tilePath5], TileScale.Sixteen);\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"tile\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"transparency16\":return transparency16;\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n"
}
```
