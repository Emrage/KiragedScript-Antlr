Live example can be found here: https://kiraged-script.herokuapp.com/ (**can take a while to load**)

# CustomScript

School project made using Antlr to generate Java Bytecode from a custom made language.

The file document.pdf(in dutch) contains most of the information to set it up and the syntax of the language.

More examples can be found in /src/main/kiraged

# Example

```javascript
var randomNumber = randomInt(10);

var guessed = false;

while (guessed == false) {
    var guess = askInt();
    if (guess == randomNumber) {
        print(true);
        guessed = true;
    } else {
        print(false);
    }
}
```

## Generated Bytecode

```
.class public Script
.super java/lang/Object

.field public static randomNumber I
.field public static guessed Z
.method static public <clinit>()V
.limit stack 16
new java/util/Random
dup
invokespecial java/util/Random/<init>()V
ldc 10
invokevirtual java/util/Random/nextInt(I)I
putstatic Script/randomNumber I
iconst_0
putstatic Script/guessed Z
return
.end method
.method public static main([Ljava/lang/String;)V
.limit stack 100
.limit locals 100

Label_2048834776_start:
getstatic Script/guessed Z
iconst_0
if_icmpne Label_1605283233_else
iconst_1
goto Label_1605283233_end
Label_1605283233_else:
iconst_0
Label_1605283233_end:
iconst_1
if_icmpne Label_2048834776_end
new java/util/Scanner
dup
getstatic java/lang/System/in Ljava/io/InputStream;
invokespecial java/util/Scanner/<init>(Ljava/io/InputStream;)V
invokevirtual java/util/Scanner/nextInt()I
istore 0
iload 0
getstatic Script/randomNumber I
if_icmpne Label_55331187_else
iconst_1
goto Label_55331187_end
Label_55331187_else:
iconst_0
Label_55331187_end:
iconst_1
if_icmpne Label_868737467_else
getstatic java/lang/System/out Ljava/io/PrintStream;
iconst_1
invokevirtual java/io/PrintStream/println(Z)V
iconst_1
putstatic Script/guessed Z
goto Label_868737467_end
Label_868737467_else:
getstatic java/lang/System/out Ljava/io/PrintStream;
iconst_0
invokevirtual java/io/PrintStream/println(Z)V
Label_868737467_end:
goto Label_2048834776_start
Label_2048834776_end:
  return
.end method
```

## Decompiled Class

```java
//
// Source code recreated from a .class file by IntelliJ IDEA
// (powered by FernFlower decompiler)
//

import java.util.Random;
import java.util.Scanner;

public class Script {
    public static int randomNumber = (new Random()).nextInt(10);
    public static boolean guessed = false;

    public static void main(String[] var0) {
        while(!guessed) {
            int var100 = (new Scanner(System.in)).nextInt();
            if (var100 == randomNumber) {
                System.out.println(true);
                guessed = true;
            } else {
                System.out.println(false);
            }
        }

    }
}

```

## Preview

![Alt Text](https://i.imgur.com/68JhaHB.gif)
