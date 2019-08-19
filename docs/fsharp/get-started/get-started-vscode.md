---
title: 開始使用F# Visual Studio Code
description: 瞭解如何搭配 Visual Studio Code F#和 Ionide 外掛程式套件使用。
ms.date: 12/23/2018
ms.openlocfilehash: baaa87207122cfe314972aee5dfaf8a41de2c394
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629975"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>開始使用F# Visual Studio Code

您可以使用F# [Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)來撰寫[Visual Studio Code](https://code.visualstudio.com) , 利用 IntelliSense 和基本程式碼重構取得絕佳的跨平臺、輕量的整合式開發環境 (IDE) 體驗。 若要深入瞭解外掛程式, 請造訪[Ionide.io](http://ionide.io) 。

若要開始, 請確定您已[ F#正確安裝和 Ionide 外掛程式](install-fsharp.md#install-f-with-visual-studio-code)。

> [!NOTE]
> Ionide 會產生 .NET Framework F#專案, 而不是 dotnet core, 這可能會有跨平臺的相容性問題。 如果您是在**Linux**或**OSX**上執行, 較簡單的入門方式就是使用[命令列工具](get-started-command-line.md)。

## <a name="creating-your-first-project-with-ionide"></a>使用 Ionide 建立您的第一個專案

若要建立新F#的專案, 請在新的資料夾中開啟 Visual Studio Code (您可以將它命名為任何您喜歡的名稱)。

接下來, 開啟命令選擇區 (**View > 命令**選擇區), 然後輸入下列內容:

```
> F# new project
```

這是由[偽造](https://github.com/fsharp-editing/Forge)專案提供技術支援。

> [!NOTE]
> 如果您沒有看到範本選項, 請在命令選擇區中執行下列命令, 以嘗試重新`>F#: Refresh Project Templates`整理範本:。

選取 F#:新增專案, 按**Enter 鍵**。 這會帶您前往下一個步驟, 也就是選取專案範本。

挑選範本, 然後按**Enter 鍵。** `classlib`

接下來, 選擇要在其中建立專案的目錄。 如果您將它保留空白, 則會使用目前的目錄。

最後, 在最後一個步驟中命名您的專案。 F#針對專案名稱使用[Pascal 大小寫](http://c2.com/cgi/wiki?PascalCase)。 本文會使用`ClassLibraryDemo`做為名稱。 輸入您想要用於專案的名稱之後, 按**Enter 鍵**。

如果您已遵循上一個步驟, 您應該會在左邊看到 [Visual Studio Code] 工作區, 以顯示下列內容:

1. F#專案本身, 位於`ClassLibraryDemo`資料夾底下。
2. 透過新增封裝[`Paket`](https://fsprojects.github.io/Paket/)的正確目錄結構。
3. 使用[`FAKE`](https://fsharp.github.io/FAKE/)的跨平臺組建腳本。
4. 可以為您提取封裝及解析相依性的可執行檔。`paket.exe`
5. 如果`.gitignore`您想要將此專案加入至 Git 型原始檔控制, 則為檔案。

## <a name="writing-some-code"></a>撰寫一些程式碼

開啟 [ *ClassLibraryDemo* ] 資料夾。  您應該會看到下列檔案:

1. `ClassLibraryDemo.fs`, 這F#是已定義類別的實作為檔案。
2. `ClassLibraryDemo.fsproj`, 這F#是用來建立此專案的專案檔。
3. `Script.fsx`, 這F#是載入原始程式檔的腳本檔案。
4. `paket.references`, 這是指定專案相依性的 Paket 檔案。

開啟`Script.fsx`, 並在其結尾處新增下列程式碼:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

此函式會將單字轉換成[Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)格式。 下一個步驟是使用F#互動式 (fsi.exe) 進行評估。

反白顯示整個函式 (應為11行長)。 反白顯示後, 按住**Alt**鍵並按**Enter**。 您會注意到下面的視窗快顯, 它應該會顯示如下的內容:

![具有 Ionide F#的互動式輸出範例](./media/getting-started-vscode/vscode-fsi.png)

這有三件事:

1. 它已開始 FSI.EXE 程式。
2. 它會傳送您在 FSI.EXE 流程上反白顯示的程式碼。
3. FSI.EXE 流程會評估您傳送的程式碼。

由於您傳送的內容是[函式](../language-reference/functions/index.md), 因此您現在可以使用 fsi.exe 來呼叫該函式! 在 [互動式] 視窗中, 輸入下列內容:

```fsharp
toPigLatin "banana";;
```

您應該會看到下列結果:

```fsharp
val it : string = "ananabay"
```

現在, 讓我們以母音做為第一個字母來嘗試。 輸入下列程式碼：

```fsharp
toPigLatin "apple";;
```

您應該會看到下列結果:

```fsharp
val it : string = "appleyay"
```

函式看起來如預期般運作。 恭喜您, 您只是在F# Visual Studio Code 中撰寫了第一個函式, 並使用 fsi.exe 進行評估!

> [!NOTE]
> 您可能已經注意到, FSI.EXE 中的行會以`;;`終止。 這是因為 FSI.EXE 可讓您輸入多行。 結尾`;;`的可讓 fsi.exe 知道程式碼完成的時間。

## <a name="explaining-the-code"></a>說明程式碼

如果您不確定程式碼實際執行的作業, 以下是逐步解說。

如您所見, `toPigLatin`是採用單字做為其輸入的函式, 並將它轉換成該單字的 Pig-拉丁標記法。 此動作的規則如下所示:

如果單字中的第一個字元是以母音開頭, 請將 "好耶" 新增至單字的結尾。 如果不是以母音開頭, 請將該第一個字元移至單字的結尾, 並在其中加上 "ay"。

在 FSI.EXE 中, 您可能已注意到下列事項:

```fsharp
val toPigLatin : word:string -> string
```

這表示`toPigLatin`會`string`將當做輸入 (稱為`word`) 的函式, 並傳回另`string`一個。 這稱為函式的[型](https://fsharpforfunandprofit.com/posts/function-signatures/)別簽章, 這是瞭解F# F#程式碼的關鍵。 如果您將滑鼠停留在 Visual Studio Code 的函式上, 也會注意到這一點。

在函式的主體中, 您會注意到兩個不同的部分:

1. 稱為`isVowel`的內部函式, 藉由透過[模式比對](../language-reference/pattern-matching.md)檢查指定的字元 (`c`) 是否符合其中一種提供的模式, 來判斷其是否為母音:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. 一個[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)運算式, 可檢查第一個字元是否為母音, 並根據第一個字元是否為母音, 依據輸入字元來構造傳回值:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

因此, 的`toPigLatin`流程如下:

檢查輸入字的第一個字元是否為母音。 如果是, 請將 "好耶" 附加至單字的結尾。 否則, 請將該第一個字元移到單字的結尾, 並在其中加上 "ay"。

有一件最後要注意的事項: 從函式傳回的明確指示, 與其他許多語言不同。 這是因為F#是以運算式為基礎, 而函數主體中的最後一個運算式是傳回值。 因為`if..then..else`本身就是運算式, 所以會根據輸入`then`值傳回區塊的主體`else`或區塊主體。

## <a name="moving-your-script-code-into-the-implementation-file"></a>將您的腳本程式碼移至執行檔

本文中的先前章節示範了撰寫F#程式碼的常見第一個步驟: 撰寫初始函式, 並使用 fsi.exe 以互動方式執行它。 這就是所謂的複寫驅動開發, 其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)複寫代表「讀取-評估-列印迴圈」。 這是實驗功能的絕佳方式, 直到您有一些工作可以運作為止。

以複寫為導向的開發的下一個步驟是將工作程式碼F#移至執行檔案。 然後編譯器會將它編譯F#成可執行檔元件。

若要開始, `ClassLibraryDemo.fs`請開啟。  您會發現有一些程式碼已經在那裡。 請繼續並刪除類別定義, 但請務必將宣告保留[`namespace`](../language-reference/namespaces.md)在頂端。

接下來, 建立名[`module`](../language-reference/modules.md) `PigLatin`為的新, `toPigLatin`並將函式複製到其中, 如下所示:

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

接下來, 再次`Script.fsx`開啟檔案, 並刪除整個`toPigLatin`函式, 但請務必在檔案中保留下列兩行:

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

選取這兩行文字, 然後按 Alt + Enter 鍵, 在 FSI.EXE 中執行這些行。 這些會將 Pig 拉丁程式庫的內容載入 fsi.exe 程式和`open` `ClassLibraryDemo`命名空間, 讓您可以存取該功能。

接下來, 在 [fsi.exe] 視窗中, 使用您`PigLatin`稍早定義的模組來呼叫函式:

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

成功！ 您會得到與之前相同的結果, 但現在已F#從執行檔載入。 此處的主要差異在於, F#原始程式檔會編譯成可以在任何地方執行的元件, 而不只是在 fsi.exe 中。

## <a name="summary"></a>總結

在本文中, 您已瞭解:

1. 如何使用 Ionide 設定 Visual Studio Code。
2. 如何使用 Ionide 建立您F#的第一個專案。
3. 如何使用F#腳本, 在 Ionide 中撰寫F#您的第一個函式, 然後在 fsi.exe 中加以執行。
4. 如何將您的腳本程式碼F#遷移至來源, 然後從 fsi.exe 呼叫該程式碼。

您現在已可使用 Visual Studio Code 和 Ionide F#來撰寫更多程式碼。

## <a name="troubleshooting"></a>疑難排解

以下幾種方式可讓您針對可能遇到的某些問題進行疑難排解:

1. 若要取得 Ionide 的程式碼編輯功能, F#您的檔案必須儲存至磁片, 以及在 Visual Studio Code 工作區中開啟的資料夾內。
2. 如果您已對系統進行變更, 或已安裝 Ionide 的必要條件 Visual Studio Code 開啟, 請重新開機 Visual Studio Code。
3. 檢查您是否可以從命令F#行使用F#編譯器和互動式, 而不需要完整路徑。 若要這麼做, 您`fsc`可以在F#編譯器的命令列中輸入, `fsi`或`fsharpi`分別針對 Windows F#上的視覺效果工具和 Mac/Linux 上的 Mono。
4. 如果您的專案目錄中有不正確字元, Ionide 可能無法使用。  如果是這種情況, 請重新命名您的專案目錄。
5. 如果沒有可用的 Ionide 命令, 請檢查您的[Visual Studio Code keybindings](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts) , 以查看是否不小心覆寫它們。
6. 如果您的電腦上的 Ionide 已中斷, 而上述未修正您的問題, 請嘗試`ionide-fsharp`移除您電腦上的目錄, 然後重新安裝外掛程式套件。

Ionide 是由F#社區成員所建立和維護的開放原始碼專案。 請在[Ionide-VSCode 回報問題, 並隨意參與:Fsharp.core GitHub 存放](https://github.com/ionide/ionide-vscode-fsharp)庫。

如果您有回報的問題, 請遵循[指示來取得報告問題時使用的記錄](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。

您也可以在[Ionide Gitter 頻道](https://gitter.im/ionide/ionide-project)中, 向 Ionide 開發F#人員和社區尋求進一步的協助。

## <a name="next-steps"></a>後續步驟

若要深入瞭解F#語言的詳細資訊, 請參閱[的F#導覽](../tour.md)。
