#### make components as dumb as possible
yes we have dumb and smart components, in-cases where components are smart, please lets not make them "too" smart, be dumb as dumb as possible.
##### why
- for ease of testing and replication
- easier to understand with fewer movable parts involved
##### ways to restrict smartness
- restrict importing anything, pass as props as much as possible, imports should be in page components
- dont use "globals", like "window", or libs that returns global values
