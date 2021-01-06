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
# <a name="debugging-stackoverflow-errors"></a><span data-ttu-id="53ce1-103">StackOverflow 錯誤的調試</span><span class="sxs-lookup"><span data-stu-id="53ce1-103">Debugging StackOverflow errors</span></span>

<span data-ttu-id="53ce1-104">當 <xref:System.StackOverflowException> 執行堆疊因為包含太多的嵌套方法呼叫而溢位時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="53ce1-104">A <xref:System.StackOverflowException> is thrown when when the execution stack overflows because it contains too many nested method calls.</span></span>  

<span data-ttu-id="53ce1-105">例如，假設您有一個應用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="53ce1-105">For example, suppose you have an app as follows:</span></span>

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

<span data-ttu-id="53ce1-106">Main 方法會持續呼叫本身，直到沒有其他堆疊空間為止。</span><span class="sxs-lookup"><span data-stu-id="53ce1-106">The Main method will continuously call itself until there is no more stack space.</span></span>  <span data-ttu-id="53ce1-107">一旦沒有堆疊空間，就無法繼續執行，因此會擲回 <xref:System.StackOverflowException> 。</span><span class="sxs-lookup"><span data-stu-id="53ce1-107">Once there is no more stack space, execution cannot continue and so it will throw a <xref:System.StackOverflowException>.</span></span>  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> <span data-ttu-id="53ce1-108">在 .NET 5 和更新版本上，呼叫堆疊會輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="53ce1-108">On .NET 5 and later, the callstack is output to the console.</span></span>

> [!NOTE]
> <span data-ttu-id="53ce1-109">本文說明如何使用 lldb 來對堆疊溢位進行 debug。</span><span class="sxs-lookup"><span data-stu-id="53ce1-109">This article describes how to debug a stack overflow with lldb.</span></span> <span data-ttu-id="53ce1-110">如果您是在 Windows 上執行，我們建議使用 [Visual Studio](/visualstudio/debugger/what-is-debugging) 或 [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)來對應用程式進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="53ce1-110">If you are running on Windows, we suggest debugging the app with [Visual Studio](/visualstudio/debugger/what-is-debugging) or [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging).</span></span>  

## <a name="example"></a><span data-ttu-id="53ce1-111">範例</span><span class="sxs-lookup"><span data-stu-id="53ce1-111">Example</span></span>

1. <span data-ttu-id="53ce1-112">執行應用程式，並將其設定為在損毀時收集傾印</span><span class="sxs-lookup"><span data-stu-id="53ce1-112">Run the app with it configured to collect a dump on crash</span></span>

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. <span data-ttu-id="53ce1-113">使用 dotnet 安裝 SOS 擴充 [功能-sos](dotnet-sos.md)</span><span class="sxs-lookup"><span data-stu-id="53ce1-113">Install the SOS extension using [dotnet-sos](dotnet-sos.md)</span></span>

    ````
    dotnet-sos install
    ````

3. <span data-ttu-id="53ce1-114">在 lldb 中調試傾印以查看失敗的堆疊</span><span class="sxs-lookup"><span data-stu-id="53ce1-114">Debug the dump in lldb to see the failing stack</span></span>

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

4. <span data-ttu-id="53ce1-115">上方的框架 `0x00007f59b40900cc` 會重複數次。</span><span class="sxs-lookup"><span data-stu-id="53ce1-115">The top frame `0x00007f59b40900cc` is repeated several times.</span></span> <span data-ttu-id="53ce1-116">使用[SOS](sos-debugging-extension.md) `ip2md` 命令找出位於位址的方法 `0x00007f59b40900cc`</span><span class="sxs-lookup"><span data-stu-id="53ce1-116">Use the [SOS](sos-debugging-extension.md) `ip2md` command to figure out what method is located at the `0x00007f59b40900cc` address</span></span>

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

5. <span data-ttu-id="53ce1-117">請查看指定的方法 temp。Program. Main (System.string [] ) 和來源 "/temp/Program.cs @ 9"，查看您是否可以找出發生錯誤的原因。</span><span class="sxs-lookup"><span data-stu-id="53ce1-117">Go look at the indicated method temp.Program.Main(System.String[]) and source "/temp/Program.cs @ 9" to see if you can figure out what you did wrong.</span></span> <span data-ttu-id="53ce1-118">如果仍然不清楚，您可以在程式碼的該區域中加入記錄。</span><span class="sxs-lookup"><span data-stu-id="53ce1-118">If it still wasn't clear you could add logging in that area of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="53ce1-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ce1-119">See Also</span></span>

* [<span data-ttu-id="53ce1-120">.NET 中傾印的簡介</span><span class="sxs-lookup"><span data-stu-id="53ce1-120">An introduction to dumps in .NET</span></span>](dumps.md)
* [<span data-ttu-id="53ce1-121">對 Linux 傾印進行偵錯</span><span class="sxs-lookup"><span data-stu-id="53ce1-121">Debug Linux dumps</span></span>](debug-linux-dumps.md)
* [<span data-ttu-id="53ce1-122">適用于 .NET 的 SOS 偵錯工具擴充功能</span><span class="sxs-lookup"><span data-stu-id="53ce1-122">SOS Debugging Extension for .NET</span></span>](sos-debugging-extension.md)
