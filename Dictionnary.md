# Fruit properties
const COLOR := { RED = "red", YELLOW = "yellow", YELLOW_ORANGE = "yellow orange" }
const SHAPE := { ROUND = "round", CURVED = "curved" }
const TEXTURE := { HARD = "hard", SOFT = "soft" }

# Fruits
const fruits: Dictionary = {
    APPLE = {
        COLOR = COLOR.RED,
        SHAPE = SHAPE.ROUND,
        TEXTURE = TEXTURE.HARD
    },
    BANANA = {
        COLOR = COLOR.YELLOW,
        SHAPE = SHAPE.CURVED,
        TEXTURE = TEXTURE.SOFT
    },
    PEACH = {
        COLOR = COLOR.YELLOW_ORANGE,
        SHAPE = SHAPE.ROUND,
        TEXTURE = TEXTURE.SOFT
    }
}

func _ready() -> void:
    # Find color of a particular fruit
    # Very efficient dictionary lookup.
    prints("Color of banana is:", fruits.BANANA.COLOR)

    # Find all 'round' fruits
    # Inefficient as it needs to scan a complete array of fruits.
    for fruit in fruits:
        var property = fruits[fruit]
        if property.SHAPE == SHAPE.ROUND:
            prints(fruit, property.COLOR, property.SHAPE, property.TEXTURE)

# ----- Output -----
# Color of banana is: yellow
# APPLE red round hard
# PEACH yellow orange round soft
