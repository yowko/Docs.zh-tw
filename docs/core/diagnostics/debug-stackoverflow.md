---
title: StackOverflow 錯誤的調試
description: 瞭解如何診斷 StackOverflow 例外狀況
ms.topic: tutorial
ms.date: 12/22/2020
ms.openlocfilehash: 92edf854ddcc2e778949d74eff1370cf27db25b4
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764925"
---
# <a name="debugging-stackoverflow-errors"></a>StackOverflow 錯誤的調試

當 <xref:System.StackOverflowException> 執行堆疊因為包含太多的嵌套方法呼叫而溢位時，就會擲回。  

例如，假設您有一個應用程式，如下所示：

````
using System;

namespace temp
{
    class Program
    {
        static void Main(string[] args)
        {
            Main(args); // oops this recursion won't stop
        }
    }
}
````

Main 方法會持續呼叫本身，直到沒有其他堆疊空間為止。  一旦沒有堆疊空間，就無法繼續執行，因此會擲回 <xref:System.StackOverflowException> 。  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> 在 .NET 5 和更新版本上，呼叫堆疊會輸出到主控台。

> [!NOTE]
> 本文說明如何使用 lldb 來對堆疊溢位進行 debug。 如果您是在 Windows 上執行，我們建議使用 [Visual Studio](/visualstudio/debugger/what-is-debugging) 或 [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)來對應用程式進行偵錯工具。  

## <a name="example"></a>範例

1. 執行應用程式，並將其設定為在損毀時收集傾印

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. 使用 dotnet 安裝 SOS 擴充 [功能-sos](dotnet-sos.md)

    ````
    dotnet-sos install
    ````

3. 在 lldb 中調試傾印以查看失敗的堆疊

    ````
    lldb --core /temp/coredump.6412
    (lldb) bt
    ...
        frame #261930: 0x00007f59b40900cc
        frame #261931: 0x00007f59b40900cc
        frame #261932: 0x00007f59b40900cc
        frame #261933: 0x00007f59b40900cc
        frame #261934: 0x00007f59b40900cc
        frame #261935: 0x00007f5a2d4a080f libcoreclr.so`CallDescrWorkerInternal at unixasmmacrosamd64.inc:867
        frame #261936: 0x00007f5a2d3cc4c3 libcoreclr.so`MethodDescCallSite::CallTargetWorker(unsigned long const*, unsigned long*, int) at callhelpers.cpp:70
        frame #261937: 0x00007f5a2d3cc468 libcoreclr.so`MethodDescCallSite::CallTargetWorker(this=<unavailable>, pArguments=0x00007ffe8222e7b0, pReturnValue=0x0000000000000000, cbReturnValue=0) at callhelpers.cpp:604
        frame #261938: 0x00007f5a2d4b6182 libcoreclr.so`RunMain(MethodDesc*, short, int*, PtrArray**) [inlined] MethodDescCallSite::Call(this=<unavailable>, pArguments=<unavailable>) at callhelpers.h:468
    ...
    ````

4. 上方的框架 `0x00007f59b40900cc` 會重複數次。 使用[SOS](sos-debugging-extension.md) `ip2md` 命令找出位於位址的方法 `0x00007f59b40900cc`

    ````
    (lldb) ip2md 0x00007f59b40900cc
    MethodDesc:   00007f59b413ffa8
    Method Name:          temp.Program.Main(System.String[])
    Class:                00007f59b4181d40
    MethodTable:          00007f59b4190020
    mdToken:              0000000006000001
    Module:               00007f59b413dbf8
    IsJitted:             yes
    Current CodeAddr:     00007f59b40900a0
    Version History:
      ILCodeVersion:      0000000000000000
      ReJIT ID:           0
      IL Addr:            0000000000000000
         CodeAddr:           00007f59b40900a0  (MinOptJitted)
         NativeCodeVersion:  0000000000000000
    Source file:  /temp/Program.cs @ 9
    ````

5. 請查看指定的方法 temp。Program. Main (System.string [] ) 和來源 "/temp/Program.cs @ 9"，查看您是否可以找出發生錯誤的原因。 如果仍然不清楚，您可以在程式碼的該區域中加入記錄。

## <a name="see-also"></a>另請參閱

* [.NET 中傾印的簡介](dumps.md)
* [對 Linux 傾印進行偵錯](debug-linux-dumps.md)
* [適用于 .NET 的 SOS 偵錯工具擴充功能](sos-debugging-extension.md)
