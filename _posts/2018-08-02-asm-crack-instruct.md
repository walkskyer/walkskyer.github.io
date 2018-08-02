---
layout: post
title:  "软件破解常用汇编指令"
categories: collection
tags:  asm
---

## 软件破解常用汇编指令

    cmp    a,b      //  比较a与b
    mov    a,b      //  把b值送给a值，使a=b
    ret             //  返回主程序
    nop             //  无作用
    call            //  调用子程序，子程序以ret结尾
    je或jz          //  相等则跳（机器码是74或84）
    jne或jnz        //  不相等则跳（机器码是75或85）
    jmp             //  无条件跳（机器码是EB）
    jb              //  若小于则跳
    ja              //  若大于则跳
    jg              //  若大于则跳
    jge             //  若大于等于则跳
    jl              //  若小于则跳
    pop xxx         //  xxx出栈
    push xxx        //  xxx压栈

## ★★破解经典句式★★

    1.(最常用)
        mov  eax [      ]  方括号中填数字或代表数值的已定义的名称
        mov  edx [      ]
        call 00??????       关键call
        test eax eax
        jz(jnz)或  jne(je)  关键跳转
    2 (最常用)
        mov  eax [      ]
        mov  edx [      ]
        call 00??????    关键call
        jne(je) 关键跳转
    3
        mov eax [  ]
        mov edx [  ]
        cmp eax,edx
        jnz(jz)
    4
        lea edi [    ]
        lea esi [    ]
        repz cmpsd
        jz(jnz)
    5
        mov  eax [      ]
        mov  edx [      ]
        call 00??????
        setz (setnz) al (bl,cl...)
    6
        mov  eax [      ]
        mov  edx [      ]
        call 00??????
        test eax eax
        setz (setnz) bl,cl...
    7
        call 00??????  ***
        push eax (ebx,ecx...)
        ......
        ......
        call 00??????
        pop eax (ebx,ecx...)
        test eax eax
        jz(jnz)