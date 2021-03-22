# First Exhibit

## Step 1

This exhibit is looking a little empty. From 
``||sprites:Sprites||``, drag the ``||variables:set mySprite to||`` 
block into ``||loops:on start|``. Click on the grey box in 
``||variables:set mySprite to||`` and draw your **favorite animal** to 
see at the zoo.

```blocks
tiles.setTilemap(tilemap`level1`)
let mySprite = sprites.create(img`
    . . . . . . 5 5 5 . . . . . . . 
    . . . . 5 5 5 5 5 5 5 . . . . . 
    . . . 5 5 4 4 5 5 5 5 . . . . . 
    . . 5 5 5 5 5 5 5 5 5 . . . . . 
    . 5 5 5 4 4 4 4 5 5 5 5 . . . . 
    . 5 5 4 f 4 4 4 4 5 4 5 . . . . 
    . 5 5 4 4 4 f 4 4 5 4 5 4 4 4 . 
    . 5 3 4 4 4 4 4 4 5 5 5 4 4 4 . 
    . 5 4 4 4 4 4 4 5 5 5 5 4 4 4 4 
    . 5 5 5 5 5 5 5 5 5 5 5 4 4 4 4 
    . . . 5 5 5 5 5 5 5 5 4 4 4 4 4 
    . . . . 5 5 5 5 5 5 4 4 4 4 4 4 
    . . . . . . 4 4 4 4 4 4 4 4 4 4 
    . . . . . 4 4 4 4 4 4 4 4 4 4 . 
    . . . . . 4 . . . . 4 4 4 . 4 . 
    . . . . 4 4 . . . . 4 4 . . . 4 
    `, SpriteKind.Player)
```

## Step 2 

Have your animal walk around the exhibit! Find the
``||sprites:set ||`` ``||variables:[mySprite]||`` ``||sprites: velocity to vx [50] vy [50]||`` block in the ``||sprites:Sprites||`` category
and drag it into the ``||loops:on start||`` container. Your animal friend
should start moving! Try changing the numbers next to **vx** and **vy**
and see what happens.

```blocks
tiles.setTilemap(tilemap`level1`)
let mySprite = sprites.create(img`
    . . . . . . 5 5 5 . . . . . . . 
    . . . . 5 5 5 5 5 5 5 . . . . . 
    . . . 5 5 4 4 5 5 5 5 . . . . . 
    . . 5 5 5 5 5 5 5 5 5 . . . . . 
    . 5 5 5 4 4 4 4 5 5 5 5 . . . . 
    . 5 5 4 f 4 4 4 4 5 4 5 . . . . 
    . 5 5 4 4 4 f 4 4 5 4 5 4 4 4 . 
    . 5 3 4 4 4 4 4 4 5 5 5 4 4 4 . 
    . 5 4 4 4 4 4 4 5 5 5 5 4 4 4 4 
    . 5 5 5 5 5 5 5 5 5 5 5 4 4 4 4 
    . . . 5 5 5 5 5 5 5 5 4 4 4 4 4 
    . . . . 5 5 5 5 5 5 4 4 4 4 4 4 
    . . . . . . 4 4 4 4 4 4 4 4 4 4 
    . . . . . 4 4 4 4 4 4 4 4 4 4 . 
    . . . . . 4 . . . . 4 4 4 . 4 . 
    . . . . 4 4 . . . . 4 4 . . . 4 
    `, SpriteKind.Player)
mySprite.setVelocity(50, 50)
```

## Step 3

Right now the movement isn't super interesting. Let's add some randomness.
``||Math:pick random [0] to [10]||`` block from the ``||Math:Math||`` category.
Put one of these into the **vx** slot and one into **vy**. Change the numbers 
around to see different kinds of movement!

```blocks
tiles.setTilemap(tilemap`level1`)
let mySprite = sprites.create(img`
    . . . . . . 5 5 5 . . . . . . . 
    . . . . 5 5 5 5 5 5 5 . . . . . 
    . . . 5 5 4 4 5 5 5 5 . . . . . 
    . . 5 5 5 5 5 5 5 5 5 . . . . . 
    . 5 5 5 4 4 4 4 5 5 5 5 . . . . 
    . 5 5 4 f 4 4 4 4 5 4 5 . . . . 
    . 5 5 4 4 4 f 4 4 5 4 5 4 4 4 . 
    . 5 3 4 4 4 4 4 4 5 5 5 4 4 4 . 
    . 5 4 4 4 4 4 4 5 5 5 5 4 4 4 4 
    . 5 5 5 5 5 5 5 5 5 5 5 4 4 4 4 
    . . . 5 5 5 5 5 5 5 5 4 4 4 4 4 
    . . . . 5 5 5 5 5 5 4 4 4 4 4 4 
    . . . . . . 4 4 4 4 4 4 4 4 4 4 
    . . . . . 4 4 4 4 4 4 4 4 4 4 . 
    . . . . . 4 . . . . 4 4 4 . 4 . 
    . . . . 4 4 . . . . 4 4 . . . 4 
    `, SpriteKind.Player)
mySprite.setVelocity(randint(-50, 50), randint(-50, 50))
```

## Step 4 

Finally, when the animal hits the edge of the screen, it just stops moving. 
You can fix that by taking the ``||sprites:set [mySprite] bounce on wall <on>||`` 
block and snapping it in at the end of the program.

```blocks
tiles.setTilemap(tilemap`level1`)
let mySprite = sprites.create(img`
    . . . . . . 5 5 5 . . . . . . . 
    . . . . 5 5 5 5 5 5 5 . . . . . 
    . . . 5 5 4 4 5 5 5 5 . . . . . 
    . . 5 5 5 5 5 5 5 5 5 . . . . . 
    . 5 5 5 4 4 4 4 5 5 5 5 . . . . 
    . 5 5 4 f 4 4 4 4 5 4 5 . . . . 
    . 5 5 4 4 4 f 4 4 5 4 5 4 4 4 . 
    . 5 3 4 4 4 4 4 4 5 5 5 4 4 4 . 
    . 5 4 4 4 4 4 4 5 5 5 5 4 4 4 4 
    . 5 5 5 5 5 5 5 5 5 5 5 4 4 4 4 
    . . . 5 5 5 5 5 5 5 5 4 4 4 4 4 
    . . . . 5 5 5 5 5 5 4 4 4 4 4 4 
    . . . . . . 4 4 4 4 4 4 4 4 4 4 
    . . . . . 4 4 4 4 4 4 4 4 4 4 . 
    . . . . . 4 . . . . 4 4 4 . 4 . 
    . . . . 4 4 . . . . 4 4 . . . 4 
    `, SpriteKind.Player)
mySprite.setVelocity(randint(-50, 50), randint(-50, 50))
mySprite.setBounceOnWall(true)
```

## Step 5 @showdialog

This exhibit looks awesome! The other kids at the zoo are going to 
love it-- what's that sound?

## Step 6 @showdialog

An alarm? What's going on-- Hold on, we're getting a report from the penguin department-- the
penguins did *what*? 

## Step 7
Oh no! You better get over there!


```template
tiles.setTilemap(tilemap`level1`)
```

```assetjson
{
  "README.md": " ",
  "assets.json": "",
  "images.g.jres": "{\n    \"image2\": \"hwQQABAAAAAAAAAAAAAAAAAAVVVVAAAAAFBVNVQAAAAAVUVEVAUAAFBV9ERUVQBAUFRERFRVQERVVERPVFVEAFVVRERUVUQAVVVFRFVVRABQVVVVVVVEAFBVRVRVRUREAABVVVVEREQAAABEREREBAAAAEREREQAAAAARERERAQAAAAAREQEQA==\",\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myImages\"\n    }\n}",
  "images.g.ts": "// Auto-generated code. Do not edit.\nnamespace myImages {\n\n    helpers._registerFactory(\"image\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"image2\":return img`\n. . . . . . 5 5 5 . . . . . . . \n. . . . 5 5 5 5 5 5 5 . . . . . \n. . . 5 5 4 4 5 5 5 5 . . . . . \n. . 5 5 5 5 5 5 5 5 5 . . . . . \n. 5 5 5 4 4 4 4 5 5 5 5 . . . . \n. 5 5 4 f 4 4 4 4 5 4 5 . . . . \n. 5 5 4 4 4 f 4 4 5 4 5 4 4 4 . \n. 5 3 4 4 4 4 4 4 5 5 5 4 4 4 . \n. 5 4 4 4 4 4 4 5 5 5 5 4 4 4 4 \n. 5 5 5 5 5 5 5 5 5 5 5 4 4 4 4 \n. . . 5 5 5 5 5 5 5 5 4 4 4 4 4 \n. . . . 5 5 5 5 5 5 4 4 4 4 4 4 \n. . . . . . 4 4 4 4 4 4 4 4 4 4 \n. . . . . 4 4 4 4 4 4 4 4 4 4 . \n. . . . . 4 . . . . 4 4 4 . 4 . \n. . . . 4 4 . . . . 4 4 . . . 4 \n`;\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"animation\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n",
  "main.blocks": "<xml xmlns=\"https://developers.google.com/blockly/xml\"><variables><variable id=\"4!;/PBS(jMdyHdu4kZ.G\">mySprite</variable><variable type=\"KIND_SpriteKind\" id=\"guc7.Pf5T:yd+8BOpiY=\">Player</variable><variable type=\"KIND_SpriteKind\" id=\"$vtC,!IJt!Bx|DPTpDA0\">Projectile</variable><variable type=\"KIND_SpriteKind\" id=\"GgHE@)-Zs3kJU|;8JivO\">Food</variable><variable type=\"KIND_SpriteKind\" id=\"N^CH|}rD/yQ80AqdS})J\">Enemy</variable></variables><block type=\"pxt-on-start\" x=\"0\" y=\"0\"><statement name=\"HANDLER\"><block type=\"tilemap_editor\"><field name=\"tilemap\">tilemap`level1`</field><data>{\"commentRefs\":[],\"fieldData\":{\"tilemap\":\"level1\"}}</data><next><block type=\"variables_set\"><field name=\"VAR\" id=\"4!;/PBS(jMdyHdu4kZ.G\">mySprite</field><value name=\"VALUE\"><shadow xmlns=\"http://www.w3.org/1999/xhtml\" type=\"math_number\"><field name=\"NUM\">0</field></shadow><block type=\"spritescreate\"><value name=\"img\"><shadow type=\"screen_image_picker\"><field name=\"img\">img`\n. . . . . . 5 5 5 . . . . . . . \n. . . . 5 5 5 5 5 5 5 . . . . . \n. . . 5 5 4 4 5 5 5 5 . . . . . \n. . 5 5 5 5 5 5 5 5 5 . . . . . \n. 5 5 5 4 4 4 4 5 5 5 5 . . . . \n. 5 5 4 f 4 4 4 4 5 4 5 . . . . \n. 5 5 4 4 4 f 4 4 5 4 5 4 4 4 . \n. 5 3 4 4 4 4 4 4 5 5 5 4 4 4 . \n. 5 4 4 4 4 4 4 5 5 5 5 4 4 4 4 \n. 5 5 5 5 5 5 5 5 5 5 5 4 4 4 4 \n. . . 5 5 5 5 5 5 5 5 4 4 4 4 4 \n. . . . 5 5 5 5 5 5 4 4 4 4 4 4 \n. . . . . . 4 4 4 4 4 4 4 4 4 4 \n. . . . . 4 4 4 4 4 4 4 4 4 4 . \n. . . . . 4 . . . . 4 4 4 . 4 . \n. . . . 4 4 . . . . 4 4 . . . 4 \n`</field><data>{\"commentRefs\":[],\"fieldData\":{\"img\":\"myImages.image2\"}}</data></shadow></value><value name=\"kind\"><shadow type=\"spritekind\"><field name=\"MEMBER\">Player</field></shadow></value></block></value><next><block type=\"spritesetvel\"><value name=\"sprite\"><block type=\"variables_get\"><field name=\"VAR\" id=\"4!;/PBS(jMdyHdu4kZ.G\">mySprite</field></block></value><value name=\"vx\"><shadow type=\"spriteSpeedPicker\"><field name=\"speed\">50</field></shadow><block type=\"device_random\"><value name=\"min\"><shadow type=\"math_number\"><field name=\"NUM\">-50</field></shadow></value><value name=\"limit\"><shadow type=\"math_number\"><field name=\"NUM\">50</field></shadow></value></block></value><value name=\"vy\"><shadow type=\"spriteSpeedPicker\"><field name=\"speed\">50</field></shadow><block type=\"device_random\"><value name=\"min\"><shadow type=\"math_number\"><field name=\"NUM\">-50</field></shadow></value><value name=\"limit\"><shadow type=\"math_number\"><field name=\"NUM\">50</field></shadow></value></block></value><next><block type=\"spritesetsetflag\"><field name=\"flag\">SpriteFlag.BounceOnWall</field><value name=\"sprite\"><block type=\"variables_get\"><field name=\"VAR\" id=\"4!;/PBS(jMdyHdu4kZ.G\">mySprite</field></block></value><value name=\"on\"><shadow type=\"toggleOnOff\"><field name=\"on\">true</field></shadow></value></block></next></block></next></block></next></block></statement></block></xml>",
  "main.ts": "tiles.setTilemap(tilemap`level1`)\nlet mySprite = sprites.create(img`\n    . . . . . . 5 5 5 . . . . . . . \n    . . . . 5 5 5 5 5 5 5 . . . . . \n    . . . 5 5 4 4 5 5 5 5 . . . . . \n    . . 5 5 5 5 5 5 5 5 5 . . . . . \n    . 5 5 5 4 4 4 4 5 5 5 5 . . . . \n    . 5 5 4 f 4 4 4 4 5 4 5 . . . . \n    . 5 5 4 4 4 f 4 4 5 4 5 4 4 4 . \n    . 5 3 4 4 4 4 4 4 5 5 5 4 4 4 . \n    . 5 4 4 4 4 4 4 5 5 5 5 4 4 4 4 \n    . 5 5 5 5 5 5 5 5 5 5 5 4 4 4 4 \n    . . . 5 5 5 5 5 5 5 5 4 4 4 4 4 \n    . . . . 5 5 5 5 5 5 4 4 4 4 4 4 \n    . . . . . . 4 4 4 4 4 4 4 4 4 4 \n    . . . . . 4 4 4 4 4 4 4 4 4 4 . \n    . . . . . 4 . . . . 4 4 4 . 4 . \n    . . . . 4 4 . . . . 4 4 . . . 4 \n    `, SpriteKind.Player)\nmySprite.setVelocity(randint(-50, 50), randint(-50, 50))\nmySprite.setFlag(SpriteFlag.BounceOnWall, true)\n",
  "pxt.json": "{\n    \"name\": \"zoo-exhibit\",\n    \"description\": \"\",\n    \"dependencies\": {\n        \"device\": \"*\"\n    },\n    \"files\": [\n        \"main.blocks\",\n        \"main.ts\",\n        \"README.md\",\n        \"assets.json\",\n        \"tilemap.g.jres\",\n        \"tilemap.g.ts\",\n        \"images.g.jres\",\n        \"images.g.ts\"\n    ],\n    \"targetVersions\": {\n        \"branch\": \"v1.3.36\",\n        \"tag\": \"v1.3.36\",\n        \"commits\": \"https://github.com/microsoft/pxt-arcade/commits/53389e906336460d06f337a21664ec615586f762\",\n        \"target\": \"1.3.36\",\n        \"pxt\": \"6.8.26\"\n    },\n    \"preferredEditor\": \"blocksprj\"\n}\n",
  "tilemap.g.jres": "{\n    \"transparency16\": {\n        \"data\": \"hwQQABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"tile1\": {\n        \"data\": \"hwQQABAAAABmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmd2hmZndoZnZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZodmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZnaHZmZmZmZmZmZmZnZmZmZmZmZmZmZmZmZmZmZmZg==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"tile\"\n    },\n    \"tile4\": {\n        \"data\": \"hwQQABAAAABmZmZmZmZ23WZmZmZmZnbdZmZmZmZmZtd2h2Zmdod21mdmZmZmZmbWZmZmZmZmdtdmZmZmZmZmdmZmZmZmZnbddmhmZmZmdt1mZmZmZmbW3WZmZmZmZnbWZmZmZmZmZtdmZndoZmZm3WZmZmZmZnfXZmZmZmZmZnZmZmZmZmZm1w==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"tile7\"\n    },\n    \"tile5\": {\n        \"data\": \"hwQQABAAAADd3d3dfd3d3d3X3Xdt133Xd3Z9dmdnfXZmZmZmZmZmZmZ2h2ZmdodmZmdmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmdmhmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZndoZmZmZmZmZmZmZmdmZmZmZmZmZg==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"tile8\"\n    },\n    \"tile6\": {\n        \"data\": \"hwQQABAAAAB9ZmZmZmZmZmdmZmZmZmZmfWdoZmZ3aGbddmZmZmZmZn1mZmZmZmZmbWdmZmZmZmbdbWZmZmZmZt1nZmZmZmZm3WdmZmZmZmZnZmZmZmZmZn1nZmZmZmZmbWZ2h2ZmZmZtZ2ZmZmZ2Ztdnd2Z3dmd23XfdZ93XfXfd3d193d3d3Q==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"tile7\": {\n        \"data\": \"hwQQABAAAADd3d3dfd3d3d3X3Xdt133dd3Z9dmdnZtdmZmZmZmZ21mdmZmZmZmbWZmZmZmZmdtdmZmZmZmZmdmZmZmZmZnbddmhmZmZmdt1mZmZmZmbW3WZmZmZmZnbWZmZmZmZmZtdmZndoZmZm3WZmZmZmZnfXZmZmZmZmZnZmZmZmZmZm1w==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"tile8\": {\n        \"data\": \"hwQQABAAAADd3d19Z2ZmZt3X3WdmZmZmd3Z9ZmZmZmZmZmZmZmZmZmZ2h2ZmdodmZmdmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmdmhmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZndoZmZmZmZmZmZmZmdmZmZmZmZmZg==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"tile2\": {\n        \"data\": \"hwQQABAAAABmZmZmZmZmZmZmZmZmZmZmZndoZmZ3aGZ2ZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmaHZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZ2h2ZmZmZmZmZmdmZmZtdnd2fXZ3Zn3Xfdfd19133d3d3d3d3d3Q==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"tile0\"\n    },\n    \"tile9\": {\n        \"data\": \"hwQQABAAAABmZmZmZmZmZmZmZmZmZmZmZndoZmZ3aGZ2ZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmaHZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZmZ2h2ZmZmZmZmZmZmZmZtdnd2ZmZmZm3XfdZ2ZmZmbd3d13ZmZmZg==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true\n    },\n    \"tile3\": {\n        \"data\": \"hwQQABAAAADd3d3dZ2ZmZt3d3X1mZmZm3d3b3Xd2d2gd0d3dbWdmZh3R3d1nZmZm3d3d3XZmZmbd3d3d3WZmZt3d3d19dmZm3d3d3X1mZmbd3bt9ZmZmZt3du913ZmZm3d3d3WZmZmbd3d3ddmZmdr3d3d1nZmZm3d3d3X1mZmbd3d3dfWZmZg==\",\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"tilemapTile\": true,\n        \"displayName\": \"tile10\"\n    },\n    \"level2\": {\n        \"id\": \"level2\",\n        \"mimeType\": \"application/mkcd-tilemap\",\n        \"data\": \"MTAxMDAwMTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMA==\",\n        \"tileset\": [\n            \"myTiles.transparency16\"\n        ],\n        \"displayName\": \"level2\"\n    },\n    \"level3\": {\n        \"id\": \"level3\",\n        \"mimeType\": \"application/mkcd-tilemap\",\n        \"data\": \"MTAxMDAwMTAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMA==\",\n        \"tileset\": [\n            \"myTiles.transparency16\",\n            \"myTiles.tile1\",\n            \"myTiles.tile2\",\n            \"myTiles.tile3\",\n            \"myTiles.tile4\",\n            \"myTiles.tile5\",\n            \"myTiles.tile6\",\n            \"myTiles.tile7\"\n        ],\n        \"displayName\": \"level3\"\n    },\n    \"level1\": {\n        \"id\": \"level1\",\n        \"mimeType\": \"application/mkcd-tilemap\",\n        \"data\": \"MTAwYTAwMDgwMDA2MDQwNDA0MDQwNDA0MDQwNDA2MDIwMTAxMDEwMTAxMDEwMTAxMDUwMjAxMDEwMTAxMDEwMTAxMDEwNTAyMDEwMTAxMDEwMTAxMDEwMTA1MDIwMTAxMDEwMTAxMDEwMTAxMDUwMjAxMDEwMTAxMDEwMTAxMDEwNTA5MDMwMzAzMDMwMzAzMDMwMzA4MDYwNzA3MDcwNzA3MDcwNzA3MDYwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMA==\",\n        \"tileset\": [\n            \"myTiles.transparency16\",\n            \"sprites.castle.tilePath5\",\n            \"myTiles.tile2\",\n            \"myTiles.tile3\",\n            \"myTiles.tile4\",\n            \"myTiles.tile5\",\n            \"sprites.castle.tileDarkGrass1\",\n            \"myTiles.tile1\",\n            \"myTiles.tile8\",\n            \"myTiles.tile9\"\n        ],\n        \"displayName\": \"level1\"\n    },\n    \"*\": {\n        \"mimeType\": \"image/x-mkcd-f4\",\n        \"dataEncoding\": \"base64\",\n        \"namespace\": \"myTiles\"\n    }\n}",
  "tilemap.g.ts": "// Auto-generated code. Do not edit.\nnamespace myTiles {\n    //% fixedInstance jres blockIdentity=images._tile\n    export const transparency16 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile1 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile4 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile5 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile6 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile7 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile8 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile2 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile9 = image.ofBuffer(hex``);\n    //% fixedInstance jres blockIdentity=images._tile\n    export const tile3 = image.ofBuffer(hex``);\n\n    helpers._registerFactory(\"tilemap\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"level2\":\n            case \"level2\":return tiles.createTilemap(hex`1000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000`, img`\n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n`, [myTiles.transparency16], TileScale.Sixteen);\n            case \"level3\":\n            case \"level3\":return tiles.createTilemap(hex`1000100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000`, img`\n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n. . . . . . . . . . . . . . . . \n`, [myTiles.transparency16,myTiles.tile1,myTiles.tile2,myTiles.tile3,myTiles.tile4,myTiles.tile5,myTiles.tile6,myTiles.tile7], TileScale.Sixteen);\n            case \"level1\":\n            case \"level1\":return tiles.createTilemap(hex`0a0008000604040404040404040602010101010101010105020101010101010101050201010101010101010502010101010101010105020101010101010101050903030303030303030806070707070707070706`, img`\n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n. . . . . . . . . . \n`, [myTiles.transparency16,sprites.castle.tilePath5,myTiles.tile2,myTiles.tile3,myTiles.tile4,myTiles.tile5,sprites.castle.tileDarkGrass1,myTiles.tile1,myTiles.tile8,myTiles.tile9], TileScale.Sixteen);\n        }\n        return null;\n    })\n\n    helpers._registerFactory(\"tile\", function(name: string) {\n        switch(helpers.stringTrim(name)) {\n            case \"transparency16\":return transparency16;\n            case \"tile\":\n            case \"tile1\":return tile1;\n            case \"tile7\":\n            case \"tile4\":return tile4;\n            case \"tile8\":\n            case \"tile5\":return tile5;\n            case \"tile6\":return tile6;\n            case \"tile7\":return tile7;\n            case \"tile8\":return tile8;\n            case \"tile0\":\n            case \"tile2\":return tile2;\n            case \"tile9\":return tile9;\n            case \"tile10\":\n            case \"tile3\":return tile3;\n        }\n        return null;\n    })\n\n}\n// Auto-generated code. Do not edit.\n"
}
```
