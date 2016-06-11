# system.main

Provides some convenience functions to establish a system based on
sv/system. The idea is that sv/system-based applications should only
have one central system map under sv.system.main/system. This allows
to provide some convenience functions like start, stop and restart
under sv.system.main. Furthermore other sv/system modules can build
upon this convention to provide further convenience.

## Usage

```clojure
(ns my-app.system
  (:require [sv.system.main :refer :all]))

(defn components []
  [{:binds [:ring :handler]
    :start [identity (fn [request]
                       {:status 200
                        :body "Hello"
                        :content-type "text/plain"})]}])

(set-components #'components)

```

Thereby you can use sv.system.main/start to start the system (and the
other convenience functions sv.system.main/stop and
sv.system.main/restart).

## License

Copyright © 2016 Max Weber (SimpleValue)

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.
