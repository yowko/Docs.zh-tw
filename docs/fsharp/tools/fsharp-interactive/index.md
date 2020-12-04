---
title: F# 互動 (dotnet) 參考
description: '瞭解如何使用 F# 互動 (dotnet fsi) ，以互動方式在主控台執行 F # 程式碼，或執行 F # 腳本。'
ms.date: 11/29/2020
f1_keywords:
- VS.ToolsOptionsPages.F#_Tools.F#_Interactive
ms.openlocfilehash: 71ec5d1b050b02ecbdb98adce814fce011cdbca0
ms.sourcegitcommit: c6de55556add9f92af17e0f8d1da8f356a19a03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96549393"
---
# <a name="interactive-programming-with-f"></a>使用 F 的互動式程式設計\#

F# 互動 (dotnet fsi) 用來以互動方式在主控台執行 F # 程式碼，或執行 F # 腳本。 換句話說，F# Interactive 會執行 F# 語言的 REPL (讀取、評估、列印迴圈)。

若要從主控台執行 F# 互動，請執行 `dotnet fsi` 。 您將可以 `dotnet fsi` 在任何 .NET SDK 中找到。

如需可用命令列選項的相關資訊，請參閱 [F# 互動選項](../../language-reference/fsharp-interactive-options.md)。

## <a name="executing-code-directly-in-f-interactive"></a>直接在 F# 互動中執行程式碼

因為 F# 互動是 (讀取-評估-列印迴圈) 的複寫功能，所以您可以在其中以互動方式執行程式碼。 以下是從命令列執行之後的互動式會話範例 `dotnet fsi` ：

```console
Microsoft (R) F# Interactive version 11.0.0.0 for F# 5.0
Copyright (c) Microsoft Corporation. All Rights Reserved.

For help type #help;;

> let square x = x *  x;;
val square : x:int -> int

> square 12;;
val it : int = 144

> printfn "Hello, FSI!"
- ;;
Hello, FSI!
val it : unit = ()
```

您會看到兩個主要專案：

1. 所有程式碼都必須以雙分號結束， (`;;` 要評估) 
2. 程式碼會進行評估並儲存在 `it` 值中。 您可以 `it` 互動方式參考。

F# 互動也支援多行輸入。 您只需要以雙分號 (的) 來終止提交 `;;` 。 請考慮下列已貼入 F# 互動的程式碼片段，並加以評估：

```console
> let getOddSquares xs =
-     xs
-     |> List.filter (fun x -> x % 2 <> 0)
-     |> List.map (fun x -> x * x)
-
- printfn "%A" (getOddSquares [1..10]);;
[1; 9; 25; 49; 81]
val getOddSquares : xs:int list -> int list
val it : unit = ()

>
```

程式碼的格式會保留下來，且 (`;;`) 終止輸入的雙重分號。 F# 互動接著評估程式碼並印出結果！

## <a name="scripting-with-f"></a>使用 F 編寫腳本\#

在 F# 互動中以互動方式評估程式碼可能是很棒的學習工具，但是您很快就會發現，在一般編輯器中撰寫程式碼並不是那麼有效率。 若要支援一般程式碼編輯，您可以撰寫 F # 腳本。

腳本會使用 .fsx 副檔名 **。** 您可以直接執行 **dotnet fsi** 並指定 f # 原始程式碼的指令檔名，而 f # interactive 會即時讀取程式碼並執行它，而不是編譯原始程式碼，然後稍後再執行已編譯的元件。 例如，請考慮下列稱為的腳本 `Script.fsx` ：

```fsharp
let getOddSquares xs =
    xs
    |> List.filter (fun x -> x % 2 <> 0)
    |> List.map (fun x -> x * x)

printfn "%A" (getOddSquares [1..10])
```

當您在電腦上建立這個檔案時，您可以使用來執行它， `dotnet fsi` 並直接在終端機視窗中查看輸出：

```console
dotnet fsi Script.fsx
[1; 9; 25; 49; 81]
```

F # 腳本在 [Visual Studio](../../get-started/get-started-visual-studio.md)、 [Visual Studio Code](../../get-started/get-started-vscode.md)和 [Visual Studio for Mac](../../get-started/get-started-with-visual-studio-for-mac.md)原生支援。

## <a name="referencing-packages-in-f-interactive"></a>在 F# 互動中參考封裝

> [!NOTE]
> 封裝管理系統可延伸，請進一步閱讀 [其他擴充](https://github.com/dotnet/fsharp/tree/main/src/fsharp/Microsoft.DotNet.DependencyManager)功能。

F# 互動支援使用 `#r "nuget:"` 語法和選擇性版本參考 NuGet 套件：

```fsharp
#r "nuget: Newtonsoft.Json"
open Newtonsoft.Json

let data = {| Name = "Don Syme"; Occupation = "F# Creator" |}
JsonConvert.SerializeObject(data)
```

如果未指定版本，則會採用最高可用的非預覽套件。 若要參考特定版本，請透過逗點引入版本。 在參考套件的預覽版本時，這會很方便。 例如，請考慮使用 [DiffSharp](https://diffsharp.github.io/)預覽版本的這個腳本：

```fsharp
#r "nuget: DiffSharp-lite, 1.0.0-preview-328097867"
open DiffSharp

// A 1D tensor
let t1 = dsharp.tensor [ 0.0 .. 0.2 .. 1.0 ]

// A 2x2 tensor
let t2 = dsharp.tensor [ [ 0; 1 ]; [ 2; 2 ] ]

// Define a scalar-to-scalar function
let f (x: Tensor) = sin (sqrt x)

printfn "%A" (f (dsharp.tensor 1.2))
```

### <a name="specifying-a-package-source"></a>指定套件來源

您也可以使用命令來指定套件來源 `#i` 。 下列範例會指定遠端和本機來源：

```fsharp
#i "nuget:https://my-remote-package-source/index.json
#i @"path-to-my-local-source"
```

這會告訴解析引擎也要考慮將遠端和/或本機來源新增至腳本。

您可以在腳本中指定任意數量的封裝參考。

> [!NOTE]
>  (使用架構參考的腳本目前有一項限制，例如 `Microsoft.NET.Sdk.Web` 或  `Microsoft.NET.Sdk.WindowsDesktop`) 。 無法使用 Saturn、Giraffe、WinForms 等套件。 這是在問題 [#9417](https://github.com/dotnet/fsharp/issues/9417)中追蹤。

深入瞭解 [套件管理擴充性和其他擴充](https://github.com/dotnet/fsharp/tree/main/src/fsharp/Microsoft.DotNet.DependencyManager)功能。

## <a name="referencing-assemblies-on-disk-with-f-interactive"></a>使用 F # interactive 參考磁片上的元件

或者，如果您在磁片上有一個元件，而且想要在腳本中參考該元件，則可以使用 `#r` 語法來指定元件。 在編譯為的專案中，請考慮下列程式碼 `MyAssembly.dll` ：

```fsharp
// MyAssembly.fs
module MyAssembly
let myFunction x y = x + 2 * y
```

其中一個已編譯，您可以在名為的檔案中參考它，如下所示 `Script.fsx` ：

```fsharp
#r "path/to/MyAssembly.dll"

printfn "%A" (MyAssembly.myFunction 10 40)
```

輸出如下所示：

```console
dotnet fsi Script.fsx
90
```

您可以在腳本中指定任意數量的元件參考。

## <a name="loading-other-scripts"></a>載入其他腳本

編寫腳本時，針對不同工作使用不同的腳本通常會很有説明。 有時候您可能會想要在另一個腳本中重複使用程式碼。 您可以簡單載入並使用來評估其內容，而不會將其內容複寫到您的檔案中 `#load` 。

請考慮下列 `Script1.fsx` 事項：

```fsharp
let square x = x * x
```

以及使用中的檔案 `Script2.fsx` ：

```fsharp
#load "Script1.fsx"
open Script1

printfn "%d" (square 12)
```

請注意，宣告 `open Script1` 是必要的。 這是因為 F # 腳本中的結構會編譯成最上層模組，也就是它所在的指令檔名。

您可以評估 `Script2.fsx` 如下：

```console
dotnet fsi Script2.fsx
144
```

您可以 `#load` 在腳本中指定所需的指示詞數目。

## <a name="using-the-fsi-object-in-f-code"></a>使用 `fsi` F # 程式碼中的物件

F # 腳本可存取 `fsi` 代表 F# 互動會話的自訂物件。 它可讓您自訂輸出格式等專案。 它也是您可以存取命令列引數的方式。

下列範例顯示如何取得和使用命令列引數：

```fsharp
let args = fsi.CommandLineArgs

for arg in args do
    printfn "%s" arg
```

進行評估時，會列印所有引數。 第一個引數一律是所評估腳本的名稱：

```dotnet
dotnet fsi Script1.fsx hello world from fsi
Script1.fsx
hello
world
from
fsi
```

您也可以使用 `System.Environment.GetCommandLineArgs()` 來存取相同的引數。

## <a name="f-interactive-directive-reference"></a>F# 互動指示詞參考

`#r`先前看到的和指示詞 `#load` 只能在 F# 互動中使用。 只有 F# 互動有幾個指示詞可用：

|指示詞|說明|
|---------|-----------|
|`#r "nuget:..."`|從 NuGet 參考封裝|
|`#r "assembly-name.dll"`|參考磁片上的元件|
|`#load "file-name.fsx"`|讀取原始程式檔、進行編譯，並加以執行。|
|`#help`|顯示可用指示詞的詳細資訊。|
|`#I`|指定加上引號的組件搜尋路徑。|
|`#quit`|終止 F# Interactive 工作階段。|
|`#time "on"` 或 `#time "off"`|它本身會 `#time` 切換是否顯示效能資訊。 當它是時 `"on"` ，F# 互動會針對所解釋和執行的每個程式碼區段，測量即時、CPU 時間和垃圾收集資訊。|

當您在 F# Interactive 中指定檔案或路徑時，應該要有一個字串常值。 因此，檔案和路徑必須以引號括住，並遵循一般的逸出字元。 您可以使用 `@` 字元來使 F# 互動將包含路徑的字串解讀為逐字字串。 這會導致 F# Interactive 會忽略所有逸出字元。

## <a name="interactive-and-compiled-preprocessor-directives"></a>互動式和編譯的預處理器指示詞

當您在 F# 互動中編譯器代碼時，無論是以互動方式執行或是執行腳本，都會定義符號 **Interactive** 。 當您在編譯器中編譯器代碼時，會定義已 **編譯** 的符號。 因此，如果程式碼在編譯和互動模式中必須不同，您可以使用這些預處理器指示詞進行條件式編譯，以決定要使用的是哪一個。 例如︰

```fsharp
#if INTERACTIVE
// Some code that executes only in FSI
// ...
#endif
```

## <a name="using-f-interactive-in-visual-studio"></a>在 Visual Studio 中使用 F# 互動

若要透過 Visual Studio 執行 F# Interactive，您可以按一下標示為 **F# Interactive** 的合適工具列按鈕，或使用按鍵 **Ctrl+Alt+F**。 如此會開啟互動式視窗，也就是執行 F# Interactive 工作階段的工具視窗。 您也可以選取要在互動式視窗中執行的一些程式碼，然後按按鍵組合 **Alt + Enter**。 F# Interactive 會隨即在標示為 **F# Interactive** 的工具視窗中啟動。 當您使用這個按鍵組合時，請確定編輯器視窗具有焦點。

不論是使用主控台還是否 Visual Studio，命令提示字元都會出現，表示解譯器在等待您輸入。 您可以如同在程式碼檔案中一樣輸入程式碼。 若要編譯並執行程式碼，請輸入兩個分號 (**;;**) 以終止一或數行的輸入。

F# Interactive 會嘗試編譯程式碼，如果成功的話，它會執行程式碼，並列印它所編譯的類型與值的簽章。 如果發生錯誤，解譯器就會列印錯誤訊息。

在同一個工作階段中輸入的程式碼，可以存取先前輸入的所有建構，因此您可以建置程式。 若有需要，可利用 [工具] 視窗中的延伸緩衝區，視需要將程式碼複製到檔案。

在 Visual Studio 中執行 F# Interactive 時，會與專案分開執行，因此，舉例來說，除非您將函式的程式碼複製到 [互動] 視窗，否則無法使用在 F# Interactive 中專案內所定義的建構。

您可以調整設定， (選項) 來控制 F# 互動命令列引數。 在 [工具] 功能表上，選取 [選項...]，然後展開 [F# 工具]。 您只能變更 F# Interactive 選項和 [64 位元 F# Interactive] 這兩項設定，而且只有在 64 位元電腦上執行 F# Interactive 時才相關。 這項設定會決定您是否要執行專用的64位版本的 **fsi.exe** 或 **fsianycpu.exe**，其使用電腦架構來判斷是否以32位或64位進程的形式執行。

## <a name="related-articles"></a>相關文章

|標題|說明|
|-----|-----------|
|[F# Interactive 選項](../../language-reference/fsharp-interactive-options.md)|描述 F# 互動、fsi.exe 的命令列語法和選項。|
