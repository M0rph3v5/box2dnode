[![build status](https://secure.travis-ci.org/M0rph3v5/box2dnode.png)](http://travis-ci.org/M0rph3v5/box2dnode)
# Box2DNode

@author Benjamin de Jager <m0rph3v5@gmail.com>

A port of the latest box2djs library into a node module.

## How to install

```js

npm install box2dnode

```

## How to use

A simple example below, you can check the documentation of box2d itself to do other stuff http://www.box2d.org/

```js

var b2d = require("box2dnode");

var world = new b2d.b2World(
		new b2d.b2Vec2(0, -10), // gravity
		true 				// dosleep
	);
	
var bodyDef = new b2d.b2BodyDef;
bodyDef.type = b2d.b2Body.b2_dynamicBody;
bodyDef.position.Set(0.0, 4.0);

var body = world.CreateBody(bodyDef);

var dynamicBox = new b2d.b2PolygonShape;
dynamicBox.SetAsBox(1.0, 1.0);

var fixtureDef = new b2d.b2FixtureDef;
fixtureDef.shape = dynamicBox;
fixtureDef.density = 1.0;
fixtureDef.friction = 0.3;

body.CreateFixture(fixtureDef);

function update() {
	world.Step(1/30, 10, 10);
	console.log(body.GetPosition());
}
setInterval(update, 1000/60);

```