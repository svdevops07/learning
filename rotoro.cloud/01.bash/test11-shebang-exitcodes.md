# SHEBANG

```
#!/bin/bash

#!/bin/cat

#!/usr/bin/env bash

#!/usr/bin/env node
```

## Посмотреть интерпретатор
```
ls -la /bin/sh
```
# EXIT CODES

"success"   =   0
"failed"    =   1
"command not found" = 127

```
echo $?
exit 1
```

## Debug
```
bash -x ./script.sh
```

### Example1
```
#!/bin/bash

set -x

for task in {0..15}
do
    run task-num-$task
done

{set +x} 2> /dev/null
```

## Сочетания клавиш
ctrl+l      - очистить экран (clean)

ctrl+s      - остановить вывод на экран

ctrl+q      - возобновить вывод на экран

ctrl+c      - завешить текущую команду

ctrl+z      - отправить команду в background