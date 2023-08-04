# clang-plugin-testAlone

>  clang+llvm15 plugin quick experiment


##  build and run

###  clang+llvm15 download
[download llvm page](https://github.com/llvm/llvm-project/releases?page=2)
```bash
mkdir /llvm_release_home/ && cd /llvm_release_home/
wget https://github.com/llvm/llvm-project/releases/download/llvmorg-15.0.0/clang+llvm-15.0.0-x86_64-linux-gnu-rhel-8.4.tar.xz
xz -d clang+llvm-15.0.0-x86_64-linux-gnu-rhel-8.4.tar.xz
tar -xvf  clang+llvm-15.0.0-x86_64-linux-gnu-rhel-8.4.tar

file /llvm_release_home/clang+llvm-15.0.0-x86_64-linux-gnu-rhel-8.4/bin/clang-15 
#/llvm_release_home/clang+llvm-15.0.0-x86_64-linux-gnu-rhel-8.4/bin/clang-15: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, not stripped, too many notes (256)

```

### build
```bash
mkdir /pubx/ && cd /pubx/

git clone https://github.com/prgrmz07/clang-plugin-testAlone.git
cd clang-plugin-testAlone
#pwd==/pubx/clang-plugin-testAlone/

mkdir build && cd build
#pwd==/pubx/clang-plugin-testAlone/build/
cmake ..
make

file  /pubx/clang-plugin-testAlone/bin/TestAlone 
#/pubx/clang-plugin-testAlone/bin/TestAlone : ELF 64-bit LSB pie executable, x86-64, version 1 (GNU/Linux), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=f66e023ccac00e1acce9c12e0c6fb278130527a8, for GNU/Linux 3.2.0, with debug_info, not stripped

```

### run
```bash

 /pubx/clang-plugin-testAlone/bin/TestAlone 
"""
/pubx/clang-brc/test_in/test_main.cpp:10:19: warning: implicit conversion from 'double' to 'int' changes value from 0.001 to 0
int MyClass::ZERO=0.001;
             ~~~~ ^~~~~
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:10:24
访问到语句: FloatingLiteral: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:10:24
访问到语句: CompoundStmt: 【{
  float fff = a + b / 10  + MyClass::ZERO     ;  char chr   = ( char ) ( 0.9 * a / b + fff * 100 )   ;
  MY_VAR_DECL_STMT
  int x,y,z;
  MY_VAR_PLUS_STMT
  return a + b;
】,结尾是否分号:0
访问到语句: DeclStmt: 【float fff = a + b / 10  + MyClass::ZERO     】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: ImplicitCastExpr: 【a + b / 10  + MyClass::】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: BinaryOperator: 【a + b / 10  + MyClass::】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: BinaryOperator: 【a + b / 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: BinaryOperator: 【b / 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: IntegerLiteral: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: ImplicitCastExpr: 【MyClass::】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: DeclRefExpr: 【MyClass::】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:47
访问到语句: DeclStmt: 【char chr   = ( char ) ( 0.9 * a / b + fff * 100 )   】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: CStyleCastExpr: 【( char ) ( 0.9 * a / b + fff * 100 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【( 0.9 * a / b + fff * 100 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ParenExpr: 【( 0.9 * a / b + fff * 100 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: BinaryOperator: 【0.9 * a / b + fff * 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: BinaryOperator: 【0.9 * a / 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: BinaryOperator: 【0.9 * 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: FloatingLiteral: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【fff * 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: BinaryOperator: 【fff * 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: IntegerLiteral: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:12:102
访问到语句: DeclStmt: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:14:12
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:14:12
访问到语句: IntegerLiteral: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:14:12
访问到语句: DeclStmt: 【int x,y,z】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:14:12
访问到语句: CompoundAssignOperator: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: IntegerLiteral: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: ReturnStmt: 【return a + 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: BinaryOperator: 【a + 】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: ImplicitCastExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
访问到语句: DeclRefExpr: 【】,结尾是否分号:1,结尾分号位置: /pubx/clang-brc/test_in/test_main.cpp:16:15
1 warning generated.
"""

```
