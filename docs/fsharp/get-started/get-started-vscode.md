---
title: 開始在 Visual Studio Code 中使用 F#
description: 瞭解如何搭配 Visual Studio Code F#和 Ionide 外掛程式套件使用。
ms.date: 12/23/2018
ms.openlocfilehash: 2aa62bb1afc220348f884865e55c4d7de4359b7f
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980349"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>開始在 Visual Studio Code 中使用 F#

您可以使用F# [Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)來撰寫[Visual Studio Code](https://code.visualstudio.com) ，利用 IntelliSense 和程式碼重構取得絕佳的跨平臺、輕量的整合式開發環境（IDE）體驗。 若要深入瞭解外掛程式，請造訪[Ionide.io](http://ionide.io) 。

若要開始，請確定您已[ F#正確安裝和 Ionide 外掛程式](install-fsharp.md#install-f-with-visual-studio-code)。

## <a name="create-your-first-project-with-ionide"></a>使用 Ionide 建立您的第一個專案

若要建立新F#的專案，請開啟命令列，並使用 .NET Core CLI 建立新的專案：

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

完成後，請將目錄變更為專案，並開啟 Visual Studio Code：

```console
cd FirstIonideProject
code .
```

在 Visual Studio Code 上載入專案之後，您應該會在F#視窗左側看到 [方案總管] 窗格開啟。 這表示 Ionide 已成功載入您剛建立的專案。 在此時間點之前，您可以在編輯器中撰寫程式碼，但一旦發生這種情況，所有專案都已完成載入。

## <a name="configure-f-interactive"></a>設定F#互動式

首先，請確定 .NET Core 腳本是您的預設腳本環境：

1. 開啟 [Visual Studio Code 設定] \ （程式**代碼** > **喜好** **設定 > 設定**）。
1. 搜尋「  **F#腳本**」一詞。
1. 按一下顯示 [ **fsharp.core：使用 SDK 腳本**] 的核取方塊。

這目前是必要的，因為 .NET Framework 型腳本中的一些舊版行為不適用於 .NET Core 腳本，而 Ionide 目前致力於回溯相容性。 未來，.NET Core 腳本會成為預設值。

### <a name="write-your-first-script"></a>撰寫您的第一個腳本

設定 Visual Studio Code 以使用 .NET Core 腳本之後，請流覽至 Visual Studio Code 中的 Explorer 視圖，並建立新的檔案。 將它命名為*MyFirstScript. run.fsx*。

現在，在其中新增下列程式碼：

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

此函式會將單字轉換成[Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)格式。 下一個步驟是使用F#互動式（fsi.exe）進行評估。

反白顯示整個函式（應為11行長）。 反白顯示後，按住**Alt**鍵並按**Enter**。 您會發現畫面底部會出現一個終端機視窗，看起來應該如下所示：

![具有 Ionide F#的互動式輸出範例](./media/getting-started-vscode/vscode-fsi.png)

這有三件事：

1. 它已開始 FSI.EXE 程式。
2. 它會傳送您在 FSI.EXE 流程上反白顯示的程式碼。
3. FSI.EXE 流程會評估您傳送的程式碼。

由於您傳送的內容是[函式](../language-reference/functions/index.md), 因此您現在可以使用 fsi.exe 來呼叫該函式! 在 [互動式] 視窗中，輸入下列內容：

```fsharp
toPigLatin "banana";;
```

您應該會看到下列結果：

```fsharp
val it : string = "ananabay"
```

現在，讓我們以母音做為第一個字母來嘗試。 輸入下列程式碼：

```fsharp
toPigLatin "apple";;
```

您應該會看到下列結果：

```fsharp
val it : string = "appleyay"
```

函式看起來如預期般運作。 恭喜您，您只是在F# Visual Studio Code 中撰寫了第一個函式，並使用 fsi.exe 進行評估！

> [!NOTE]
> 您可能已經注意到，FSI.EXE 中的行會以 `;;`終止。 這是因為 FSI.EXE 可讓您輸入多行。 結尾的 `;;` 可讓 FSI.EXE 知道程式碼完成的時間。

## <a name="explaining-the-code"></a>說明程式碼

如果您不確定程式碼實際執行的作業，以下是逐步解說。

如您所見，`toPigLatin` 是採用單字作為其輸入的函式，並將它轉換成該單字的 Pig-拉丁標記法。 此動作的規則如下所示：

如果單字中的第一個字元是以母音開頭，請將 "好耶" 新增至單字的結尾。 如果不是以母音開頭，請將該第一個字元移至單字的結尾，並在其中加上 "ay"。

在 FSI.EXE 中，您可能已注意到下列事項：

```fsharp
val toPigLatin : word:string -> string
```

這表示 `toPigLatin` 是接受 `string` 做為輸入（稱為 `word`）的函式，並會傳回另一個 `string`。 這稱為函式的[型](https://fsharpforfunandprofit.com/posts/function-signatures/)別簽章，這是瞭解F# F#程式碼的關鍵。 如果您將滑鼠停留在 Visual Studio Code 的函式上，也會注意到這一點。

在函式的主體中，您會注意到兩個不同的部分：

1. 稱為`isVowel`的內部函式, 藉由透過[模式比對](../language-reference/pattern-matching.md)檢查指定的字元 (`c`) 是否符合其中一種提供的模式, 來判斷其是否為母音:

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. 一個[`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)運算式，可檢查第一個字元是否為母音，並根據第一個字元是否為母音，從輸入字元來建立傳回值：

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

因此，`toPigLatin` 的流程如下：

檢查輸入字的第一個字元是否為母音。 如果是，請將 "好耶" 附加至單字的結尾。 否則，請將該第一個字元移到單字的結尾，並在其中加上 "ay"。

有一個最後要注意的事項：在中F#，沒有明確的指示可從函式傳回。 這是因為F#是以運算式為基礎，而在函式主體中評估的最後一個運算式會決定該函數的傳回值。 因為 `if..then..else` 本身就是運算式，所以 `then` 區塊主體的評估或 `else` 區塊的主體會決定 `toPigLatin` 函數所傳回的值。

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>將主控台應用程式轉換成 Pig 的拉丁產生器

本文中的先前章節示範了撰寫F#程式碼的常見第一個步驟：撰寫初始函式，並使用 fsi.exe 以互動方式執行它。 這就是所謂的複寫驅動開發, 其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)複寫代表「讀取-評估-列印迴圈」。 這是實驗功能的絕佳方式，直到您有一些工作可以運作為止。

以複寫為導向的開發的下一個步驟是將工作程式碼F#移至執行檔案。 然後編譯器會將它編譯F#成可執行檔元件。

若要開始，請開啟您先前使用 .NET Core CLI 建立的*程式. fs*檔案。 您會發現有一些程式碼已經在那裡。

接下來，建立稱為 `PigLatin` 的新[`module`](../language-reference/modules.md) ，並將您稍早建立的 `toPigLatin` 函式複製到其中，如下所示：

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

此模組應高於 `main` 函式和 `open System` 宣告底下。 宣告的順序很重要F#，因此您必須先定義函式，才能在檔案中呼叫它。

現在，在 `main` 函式中，對引數呼叫您的 Pig 拉丁產生器函式：

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn "%s in Pig Latin is: %s" name newName

    0
```

現在您可以從命令列執行主控台應用程式：

```dotnetcli
dotnet run apple banana
```

您會發現它會輸出與腳本檔案相同的結果，但這次是執行中的程式！

## <a name="troubleshooting-ionide"></a>疑難排解 Ionide

以下幾種方式可讓您針對可能遇到的某些問題進行疑難排解：

1. 若要取得 Ionide 的程式碼編輯功能， F#您的檔案必須儲存至磁片，以及在 Visual Studio Code 工作區中開啟的資料夾內。
1. 如果您已對系統進行變更，或已安裝 Ionide 的必要條件 Visual Studio Code 開啟，請重新開機 Visual Studio Code。
1. 如果您的專案目錄中有不正確字元，Ionide 可能無法使用。  如果是這種情況，請重新命名您的專案目錄。
1. 如果沒有可用的 Ionide 命令，請檢查您[Visual Studio Code 的金鑰](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization)系結，以查看您是否意外覆寫它們。
1. 如果您的電腦上的 Ionide 已中斷，而上述未修正您的問題，請嘗試移除電腦上的 `ionide-fsharp` 目錄，然後重新安裝外掛程式套件。
1. 如果無法載入專案（ F#方案總管將會顯示這種情況），請以滑鼠右鍵按一下該專案，然後按一下 [**查看詳細資料**] 以取得更多診斷資訊。

Ionide 是由F#社區成員所建立和維護的開放原始碼專案。 請在[ionide-vscode-Fsharp.core GitHub 存放庫](https://github.com/ionide/ionide-vscode-fsharp)（英文）中回報問題並歡迎您參與。

您也可以在[Ionide Gitter 頻道](https://gitter.im/ionide/ionide-project)中，向 Ionide 開發F#人員和社區尋求進一步的協助。

## <a name="next-steps"></a>後續步驟

若要深入瞭解F#語言的詳細資訊，請參閱[的F#導覽](../tour.md)。
