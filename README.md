# cli-meter

```coffee
meter = require 'cli-meter'
```

Creating a meter

```coffee
# 100 steps by default
p = new Meter()

# optional total steps
p = new Meter(total: 500)

# optional starting value
p = new Meter(total: 500, value: 120)

# optional display length in the terminal
p = new Meter(total: 500, length: 30)
```

You can then manipulate it with

```coffee
p.step(1)    # increment by 1
p.step(-3)   # decrement by 3
p.set(70)    # jump to 70
```

And finally display it

```coffee
console.log "Processing #{p}"
# Processing  [==============      ]

console.log "#{p} #{p.value} dB"
# [==============      ] 30 dB

console.log "#{p} #{p.value} / #{p.total}"
# [==============      ] 230 / 500
```

## Animations

If you use `console.log`, the meter will be printed to a different line each time:

```coffee
# [============        ] 6 / 10
# [================    ] 8 / 10
```

If you have a `TTY` stream like `process.stdout`, you can show animations instead:

```coffee
setInterval (->

  process.stdout.write "Meter 1 #{p1}\n"
  process.stdout.write "Meter 2 #{p2}\n"
  process.stdout.write "Meter 3 #{p3}\n"

  process.stdout.moveCursor 0, -3

), 100
```

![example](https://raw.github.com/TabDigital/cli-meter/master/example.gif)
