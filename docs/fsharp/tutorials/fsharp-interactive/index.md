---
title: F# Interactive (fsi.exe) 參考
description: '了解如何 F # Interactive (fsi.exe) 用來以互動方式在主控台執行 F # 程式碼或執行 F # 指令碼。'
ms.date: 05/16/2016
ms.openlocfilehash: b16ebcfe361ef50c7c7ba8510f01f6704e62ce3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="interactive-programming-with-f"></a>F# 互動式程式設計 #

> [!NOTE]
本文目前僅描述 Windows 的體驗。  將會加以重新撰寫。

> [!NOTE]
API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

F# Interactive (fsi.exe) 在主控台中，以互動方式用於執行 F# 程式碼，或執行 F# 指令碼。 換句話說，F# Interactive 會執行 F# 語言的 REPL (讀取、評估、列印迴圈)。

若要從主控台執行 F# Interactive，請執行 fsi.exe。  您可以獲悉 fsi.exe 在"c:\Program 檔案 (x86) \Microsoft SDKs\F#\<版本 > \Framework\<版本 >\"。 如需可用命令列選項的資訊，請參閱 [F# Interactive 選項](../../language-reference/fsharp-interactive-options.md)。

若要透過 Visual Studio 執行 F# Interactive，您可以按一下標示為 **F# Interactive** 的合適工具列按鈕，或使用按鍵 **Ctrl+Alt+F**。 如此會開啟互動式視窗，也就是執行 F# Interactive 工作階段的工具視窗。 您也可以選取要在互動式視窗中執行的部分程式碼，然後點擊按鍵組合 **ALT+ENTER**。 F# Interactive 會隨即在標示為 **F# Interactive** 的工具視窗中啟動。 當您使用這個按鍵組合時，請確定編輯器視窗具有焦點。

不論是使用主控台還是否 Visual Studio，命令提示字元都會出現，表示解譯器在等待您輸入。 您可以如同在程式碼檔案中一樣輸入程式碼。 若要編譯並執行程式碼，請輸入兩個分號 (**;;**) 以終止一或數行的輸入。

F# Interactive 會嘗試編譯程式碼，如果成功的話，它會執行程式碼，並列印它所編譯的類型與值的簽章。 如果發生錯誤，解譯器就會列印錯誤訊息。

在同一個工作階段中輸入的程式碼，可以存取先前輸入的所有建構，因此您可以建置程式。 若有需要，可利用 [工具] 視窗中的延伸緩衝區，視需要將程式碼複製到檔案。

在 Visual Studio 中執行 F# Interactive 時，會與專案分開執行，因此，舉例來說，除非您將函式的程式碼複製到 [互動] 視窗，否則無法使用在 F# Interactive 中專案內所定義的建構。

若您開啟了參考某些程式庫的專案，則可以透過方案總管參考 F# Interactive 中的這些程式庫。 若要參考 F# Interactive 中的程式庫，請展開 [參考] 節點，開啟程式庫的捷徑功能表，然後選擇 [傳送至 F# Interactive]。

您可以調整設定來控制 F# Interactive 命令列引數 (選項)。 在 [工具] 功能表上，選取 [選項...]，然後展開 [F# 工具]。 您只能變更 F# Interactive 選項和 [64 位元 F# Interactive] 這兩項設定，而且只有在 64 位元電腦上執行 F# Interactive 時才相關。 這項設定會判斷您要執行專用的 64 位元版 fsi.exe 或 fsianycpu.exe，它會使用電腦架構判斷要以 32 位元或 64 位元處理序執行。


## <a name="scripting-with-f"></a>F# 指令碼作業 #
指令碼使用副檔名 **.fsx** 或 **.fsscript**。 您只要執行 **fsi.exe**，並指定 F# 原始程式碼的指令碼檔名，F# Interactive 就會即時讀取程式碼並執行程式碼，而不是編譯原始程式碼，然後稍後再執行已編譯的組件。


## <a name="differences-between-the-interactive-scripting-and-compiled-environments"></a>Interactive、指令碼與編譯環境之間的差異
當您編譯 F# Interactive 中的程式碼時，無論是以互動方式執行或是執行指令碼，都會定義符號 **INTERACTIVE**。 當您在編譯器中編譯程式碼時，會定義符號 **COMPILED**。 因此，如果已編譯模式和互動式模式中的程式碼必須不同，可以使用條件式編譯的前置處理器指示詞，決定要使用哪一種模式。

當您要在 F# Interactive 中執行在執行編譯器時無法使用的指令碼時，有一些指示詞可用。 下表摘要說明使用 F# Interactive 時可用的指示詞。

|指示詞|描述|
|---------|-----------|
|**#help**|顯示可用指示詞的詳細資訊。|
|**#I**|指定加上引號的組件搜尋路徑。|
|**#load**|讀取原始程式檔、進行編譯，並加以執行。|
|**#quit**|終止 F# Interactive 工作階段。|
|**#r**|參考組件。|
|**#time ["on"&#124;"off"]**|**#time** 會自行切換是否顯示效能資訊。 當它啟用時，F# Interactive 會測量所解譯及執行的每個程式碼區段之即時、CPU 時間及記憶體回收資訊。|

當您在 F# Interactive 中指定檔案或路徑時，應該要有一個字串常值。 因此，檔案和路徑必須以引號括住，並遵循一般的逸出字元。 此外，您可以使用 @ 字元，讓 F# Interactive 能將包含路徑的字串，解譯為逐字字串。 這會導致 F# Interactive 會忽略所有逸出字元。

已編譯模式和互動式模式之間，其中一項差異是存取命令列引數的方式。 在編譯模式中是使用 **System.Environment.GetCommandLineArgs**。 而在指令碼中則是使用 **fsi.CommandLineArgs**。

下列程式碼說明如何建立可讀取指令碼中命令列引數的函式，同時也會示範如何從指令碼參考另一個組件。 第一個程式碼檔案 **MyAssembly.fs** 是要參考之組件的程式碼。 請使用命令列 **fsc -a MyAssembly.fs** 編譯這個檔案，然後使用下列命令列以指令碼形式執行第二個檔案：**fsi --exec file1.fsx** test

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

```fsharp
// file1.fsx
#r "MyAssembly.dll"

printfn "Command line arguments: "

for arg in fsi.CommandLineArgs do
    printfn "%s" arg

printfn "%A" (MyAssembly.myFunction 10 40)
```

其輸出如下：

```
Command line arguments: 
file1.fsx
test
90
```

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----|-----------|
|[F# Interactive 選項](../../language-reference/fsharp-interactive-options.md)|描述命令列語法和選項 F # Interactive fsi.exe。|
|[F# Interactive 程式庫參考](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-interactive-library-reference)|說明在 F# Interactive 中執行程式碼時，所提供的程式庫功能。|
