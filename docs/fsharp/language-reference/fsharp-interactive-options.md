---
title: 互動式選項
description: 瞭解 F# 互動、fsi.exe 所支援的命令列選項。
ms.date: 08/15/2020
ms.openlocfilehash: adc8dc86f14366720e1acbf35115d4e318a76aef
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810527"
---
# <a name="f-interactive-options"></a>F# 互動選項

本文說明 F# 互動所支援的命令列選項 `fsi.exe` 。 F# 互動接受許多與 F # 編譯器相同的命令列選項，但也接受一些額外的選項。

## <a name="use-f-interactive-for-scripting"></a>使用 F# 互動編寫腳本

F# 互動， `dotnet fsi` 可以透過互動方式啟動，也可以從命令列啟動來執行腳本。 命令列語法為

```dotnetcli
dotnet fsi [options] [ script-file [arguments] ]
```

F # 腳本檔案的副檔名為 `.fsx` 。

## <a name="table-of-f-interactive-options"></a>F# 互動選項的表格

下表摘要說明 F# 互動所支援的選項。 您可以在命令列上或透過 Visual Studio IDE 來設定這些選項。 若要在 Visual Studio IDE 中設定這些選項，請開啟 [ **工具** ] 功能表，選取 [ **選項**]，展開 [ **F # 工具** ] 節點，然後選取 [ **F# 互動**]。

清單元素會以分號分隔 F# 互動選項引數， (`;`) 。

|選項|描述|
|------|-----------|
|**--**|用來指示 F# 互動將其餘引數視為 F # 程式或腳本的命令列引數，您可以使用 **Fsi >my.application.commandlineargs**，在程式碼中存取這些引數。|
|**--checked**[ **+**&#124;**-** ]|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--字碼頁： &lt; int&gt;**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--consolecolors**[ **+**&#124;**-** ]|以色彩輸出警告和錯誤訊息。|
|**--crossoptimize**[ **+**&#124;**-** ]|啟用或停用跨模組優化。|
|**--debug**[ **+**&#124;**-** ]<br /><br />**--debug：**[**full**&#124;**pdbonly**&#124;**便攜**&#124;**embedded**]<br /><br />**-g**[ **+**&#124;**-** ]<br /><br />**-g：**[**full**&#124;**pdbonly**&#124;**便攜**&#124;**embedded**]|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--define： &lt; 字串&gt;**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--具決定性**[ **+**&#124;**-** ]|產生具決定性的元件 (包括模組版本 GUID 和時間戳記) 。|
|**--exec**|指示 F # interactive 在載入檔案或執行命令列上指定的腳本檔案後結束。|
|**--fullpaths**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--gui**[ **+**&#124;**-** ]|啟用或停用 Windows Forms 事件迴圈。 預設值為 [已啟用]。|
|**--說明**<br /><br />**-?**|用來顯示命令列語法及每個選項的簡短描述。|
|**--lib： &lt; folder 清單&gt;**<br /><br />**-I： &lt; 資料夾清單&gt;**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--load： &lt; filename&gt;**|在啟動時編譯指定的原始程式碼，並將編譯的 F # 結構載入至會話。|
|**--mlcompatibility**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--noframework**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱 [編譯器選項](compiler-options.md)|
|**--nologo**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--nowarn： &lt; 警告-清單&gt;**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--optimize**[ **+**&#124;**-** ]|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--preferreduilang： &lt; lang&gt;**| 指定慣用的輸出語言文化特性名稱 (例如，es、ja-jp) 。 |
|**--quiet**|隱藏 F# 互動的輸出至 **stdout** 資料流程。|
|**--引號-debug**|指定應針對衍生自 F # 引號常值和反映定義的運算式發出額外的偵錯工具資訊。 偵錯工具資訊會加入至 F # 運算式樹狀結構節點的自訂屬性。 請參閱程式 [代碼引號](code-quotations.md) 和 [CustomAttributes](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-quotations-fsharpexpr.html#CustomAttributes)。|
|**--readline**[ **+**&#124;**-** ]|啟用或停用互動式模式的 tab 鍵自動完成。|
|**--reference： &lt; filename&gt;**<br /><br />**-r： &lt; filename&gt;**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--tailcalls**[ **+**&#124;**-** ]|啟用或停用 tail IL 指令，這會導致堆疊框架重複用於 tail 遞迴函式。 這個選項預設為啟用。|
|**--targetprofile： &lt; 字串&gt;**|指定此元件的目標 framework 設定檔。 有效值為 `mscorlib`、`netcore` 或 `netstandard`。 預設為 `mscorlib`。|
|**--use： &lt; filename&gt;**|告知解譯器在啟動時使用指定的檔案做為初始輸入。|
|**--utf8output**|與 fsc.exe 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--警告： &lt; 警告層級&gt;**|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--warnaserror**[ **+**&#124;**-** ]|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|
|**--warnaserror**[ **+**&#124;**-** ]：** &lt; int-list &gt; **|與 **fsc.exe** 編譯器選項相同。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。|

## <a name="f-interactive-structured-printing"></a>F# 互動結構化列印

F# 互動 (`dotnet fsi`) 會使用延伸版本的 [結構化純文字格式](plaintext-formatting.md) 來報告值。

1. `%A`支援純文字格式的所有功能，而有些則是可自訂的。

2. 如果輸出主控台支援色彩，則會以色彩標示列印。

3. 除非您明確評估該字串，否則會將限制放在顯示的字串長度。

4. 您可以透過物件取得一組使用者可定義的設定 `fsi` 。

針對報告值自訂純文字列印的可用設定如下：

```fsharp
open System.Globalization

fsi.FormatProvider <- CultureInfo("de-DE")  // control the default culture for primitives

fsi.PrintWidth <- 120        // Control the width used for structured printing

fsi.PrintDepth <- 10         // Control the maximum depth of nested printing

fsi.PrintLength <- 10        // Control the length of lists and arrays

fsi.PrintSize <- 100         // Control the maximum overall object count

fsi.ShowProperties <- false  // Control whether properties of .NET objects are shown by default

fsi.ShowIEnumerable <- false // Control whether sequence values are expanded by default

fsi.ShowDeclarationValues <- false // Control whether values are shown for declaration outputs
```

### <a name="customize-with-addprinter-and-addprinttransformer"></a>使用和自訂 `AddPrinter``AddPrintTransformer`

您可以使用和自訂 F# 互動輸出中的列印 `fsi.AddPrinter` `fsi.AddPrintTransformer` 。
第一個函數會提供文字來取代物件的列印。 第二個函式會傳回要改為顯示的代理物件。 例如，請考慮下列 F # 程式碼：

```fsharp
open System

fsi.AddPrinter<DateTime>(fun dt -> dt.ToString("s"))

type DateAndLabel =
    { Date: DateTime
      Label: string  }

let newYearsDay1999 =
    { Date = DateTime(1999, 1, 1)
      Label = "New Year" }
```

如果您在 F# 互動中執行此範例，它會根據格式化選項組進行輸出。 在此情況下，它會影響日期和時間的格式：

```console
type DateAndLabel =
  { Date: DateTime
    Label: string }
val newYearsDay1999 : DateAndLabel = { Date = 1999-01-01T00:00:00
                                       Label = "New Year" }
```

`fsi.AddPrintTransformer` 可以用來提供要列印的代理物件：

```fsharp
type MyList(values: int list) =
    member _.Values = values

fsi.AddPrintTransformer(fun (x:MyList) -> box x.Values)

let x = MyList([1..10])
```

輸出如下：

```console
val x : MyList = [1; 2; 3; 4; 5; 6; 7; 8; 9; 10]
```

如果傳遞的轉換器函式 `fsi.AddPrintTransformer` 傳回 `null` ，則會忽略列印轉換器。
這可以用來以型別開頭，以篩選任何輸入值 `obj` 。  例如：

```fsharp
fsi.AddPrintTransformer(fun (x:obj) ->
    match x with
    | :? string as s when s = "beep" -> box ["quack"; "quack"; "quack"]
    | _ -> null)

let y = "beep"
```

輸出如下：

```console
val y : string = ["quack"; "quack"; "quack"]
```

## <a name="related-topics"></a>相關主題

|標題|描述|
|-----|-----------|
|[編譯器選項](compiler-options.md)|描述 F # 編譯器可用的命令列選項， **fsc.exe**。|
