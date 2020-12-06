---
title: 開始在 Visual Studio Code 中使用 F#
description: '瞭解如何使用 F # 搭配 Visual Studio Code 和 Ionide 外掛程式套件。'
ms.date: 12/23/2018
ms.openlocfilehash: 11fb0d443fb7c2b3f270d45bfeaa91102ba28efd
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739798"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>開始在 Visual Studio Code 中使用 F#

您可以使用[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)來撰寫[Visual Studio Code](https://code.visualstudio.com)的 F #，以取得絕佳的跨平臺、輕量的整合式開發環境， (使用 IntelliSense 和程式碼重構的 IDE) 體驗。 造訪 [Ionide.io](https://ionide.io) 以深入瞭解外掛程式。

若要開始，請確定您已 [正確安裝 F # 和 Ionide 外掛程式](install-fsharp.md#install-f-with-visual-studio-code)。

## <a name="create-your-first-project-with-ionide"></a>使用 Ionide 建立您的第一個專案

若要建立新的 F # 專案，請開啟命令列，並使用 .NET Core CLI 建立新的專案：

```dotnetcli
dotnet new console -lang "F#" -o FirstIonideProject
```

完成之後，請將目錄變更為專案，並開啟 Visual Studio Code：

```console
cd FirstIonideProject
code .
```

專案載入 Visual Studio Code 之後，您應該會在視窗的左側看到 F # 方案總管窗格開啟。 這表示 Ionide 已成功載入您剛才建立的專案。 您可以在此時間點之前在編輯器中撰寫程式碼，但是一旦發生這種情況，所有專案都已完成載入。

## <a name="configure-f-interactive"></a>設定 F # interactive

首先，請確定 .NET Core 腳本是您的預設腳本環境：

1. 開啟 [Visual Studio Code 設定] ([程式 **代碼**  >  **偏好**  >  **設定**]) 。
1. 搜尋「 **F # 腳本**」一詞。
1. 按一下顯示 [ **fsharp.core：使用 SDK 腳本**] 的核取方塊。

這目前是必要的，因為 .NET Framework 型腳本中的某些舊版行為不適用於 .NET Core 腳本，而 Ionide 目前致力於提供回溯相容性。 未來，.NET Core 腳本會成為預設值。

### <a name="write-your-first-script"></a>撰寫您的第一個指令碼

當您將 Visual Studio Code 設定為使用 .NET Core 腳本之後，請流覽至 Visual Studio Code 中的 Explorer 視圖，然後建立新的檔案。 將它命名為 *MyFirstScript. .fsx*。

現在，在其中新增下列程式碼：

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

此函式會將單字轉換成 [Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)的形式。 下一步是使用 F# 互動 (FSI) 來進行評估。

醒目提示整個函數 (應為11行長) 。 反白顯示之後，請按住 **Alt** 鍵，然後按 **Enter** 鍵。 您會注意到畫面底部會出現一個終端機視窗，看起來應該像這樣：

![使用 Ionide F# 互動輸出的範例](./media/getting-started-vscode/vscode-fsi.png)

這有三個專案：

1. 它已開始 FSI 程式。
2. 它會將您在 FSI 程式上反白顯示的程式碼傳送給您。
3. FSI 進程會評估您傳送的程式碼。

因為您送出的是函 [式，所以](../language-reference/functions/index.md)您現在可以使用 FSI 來呼叫該函式！ 在互動式視窗中，輸入下列內容：

```fsharp
toPigLatin "banana";;
```

您應該會看到下列結果：

```fsharp
val it : string = "ananabay"
```

現在，讓我們以母音做為第一個字母來嘗試。 輸入以下資訊：

```fsharp
toPigLatin "apple";;
```

您應該會看到下列結果：

```fsharp
val it : string = "appleyay"
```

函數看起來像預期般運作。 恭喜，您只是在 Visual Studio Code 撰寫了第一個 F # 函式，並使用 FSI 進行評估！

> [!NOTE]
> 您可能已經注意到，FSI 中的行會以終止 `;;` 。 這是因為 FSI 可讓您輸入多行。 `;;`最後讓 FSI 知道程式碼完成的時間。

## <a name="explaining-the-code"></a>說明程式碼

如果您不確定程式碼實際執行的工作，以下是逐步解說。

如您所見，它 `toPigLatin` 是接受單字作為其輸入的函式，並將它轉換成該單字的 Pig-Latin 標記法。 其規則如下所示：

如果單字中的第一個字元開頭為母音，請將 "好耶" 新增至單字的結尾。 如果它不是以母音開頭，請將第一個字元移至單字的結尾，並將 "ay" 新增至其中。

您可能已注意到 FSI 中的下列事項：

```fsharp
val toPigLatin : word:string -> string
```

這是一種函式 `toPigLatin` ，它會採用 `string` 做為輸入的 (`word` ，稱為) ，並傳回另一個 `string` 。 這就是所謂的函式 [類型](https://fsharpforfunandprofit.com/posts/function-signatures/)簽章，這是 f # 的基本部分，這是瞭解 F # 程式碼的關鍵。 如果您將滑鼠停留在 Visual Studio Code 的函式上，也會注意到這一點。

在函式主體中，您會看到兩個不同的部分：

1. 稱為的內部函式， `isVowel` 它 `c` 會藉由檢查是否符合透過 [模式](../language-reference/pattern-matching.md)比對所提供的其中一個模式，來判斷指定的字元 () 是否為母音：

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [`if..then..else`](../language-reference/conditional-expressions-if-then-else.md)檢查第一個字元是否為母音的運算式，並根據第一個字元是否為母音來根據輸入字元來檢查傳回值：

   [!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

因此的流程 `toPigLatin` 如下：

檢查輸入單字的第一個字元是否為母音。 如果是，請將 "好耶" 附加至單字的結尾。 否則，請將第一個字元移至單字的結尾，並將 "ay" 新增至該字元。

有一項最後要注意的事項：在 F # 中，沒有從函式傳回的明確指示。 這是因為 F # 是以運算式為基礎，而且在函式主體中評估的最後一個運算式會決定該函數的傳回值。 因為 `if..then..else` 本身是運算式，所以區塊主體或區塊主體的評估會 `then` `else` 決定函數所傳回的值 `toPigLatin` 。

## <a name="turn-the-console-app-into-a-pig-latin-generator"></a>將主控台應用程式轉換成 Pig 的拉丁產生器

本文的前幾節示範了撰寫 F # 程式碼的常見第一個步驟：撰寫初始函式，並以互動方式使用 FSI 來執行它。 這就是所謂的複寫導向開發，其中的 [複寫代表「](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop) 讀取-評估-列印迴圈」。 這是實驗功能的絕佳方法，直到您有一些工作。

複寫導向開發的下一步，是將工作程式碼移到 F # 實作為檔案。 然後，F # 編譯器會將它編譯成可執行檔元件。

若要開始，請開啟您稍早使用 .NET Core CLI 建立的 *程式. fs* 檔案。 您會發現其中已有一些程式碼。

接著，建立名為的新， [`module`](../language-reference/modules.md) `PigLatin` 並將您稍早建立的函式複製 `toPigLatin` 到其中，如下所示：

[!code-fsharp[ToPigLatin](~/samples/snippets/fsharp/getting-started/pig-latin.fs#L3-L14)]

此模組應該在函式 `main` 和宣告下方 `open System` 。 在 F # 中，宣告的順序很重要，因此您必須先定義函式，才能在檔案中呼叫該函式。

現在，在函式中 `main` ，呼叫引數上的 Pig 拉丁產生器函式：

```fsharp
[<EntryPoint>]
let main argv =
    for name in argv do
        let newName = PigLatin.toPigLatin name
        printfn %"{name} in Pig Latin is: {newName}"

    0
```

現在您可以從命令列執行您的主控台應用程式：

```dotnetcli
dotnet run apple banana
```

您會看到它與腳本檔案輸出的結果相同，但是這次是執行中的程式！

## <a name="troubleshooting-ionide"></a>針對 Ionide 進行疑難排解

以下是一些您可以針對一些可能遇到的問題進行疑難排解的方法：

1. 若要取得 Ionide 的程式碼編輯功能，您的 F # 檔案必須儲存到磁片，並放在 Visual Studio Code 工作區中開啟的資料夾內。
1. 如果您已對系統進行變更，或已安裝 Visual Studio Code 開啟的 Ionide 必要條件，請重新開機 Visual Studio Code。
1. 如果您的專案目錄中有不正確字元，Ionide 可能無法運作。  如果發生這種情況，請重新命名您的專案目錄。
1. 如果沒有任何 Ionide 命令可運作，請檢查您的 [Visual Studio Code 機碼](https://code.visualstudio.com/docs/getstarted/keybindings#_advanced-customization) 系結，以查看是否意外覆寫這些命令。
1. 如果您的電腦上的 Ionide 已中斷，且上述各項都未修正您的問題，請嘗試移除 `ionide-fsharp` 電腦上的目錄，然後重新安裝外掛程式套件。
1. 如果專案無法載入 (F # 方案總管將會顯示此) ，請在該專案上按一下滑鼠右鍵，然後按一下 [ **查看詳細資料** ] 以取得更多診斷資訊。

Ionide 是一種開放原始碼專案，由 F # 群體的成員所建立和維護。 請在 [ionide-vscode-Fsharp.core GitHub 存放庫](https://github.com/ionide/ionide-vscode-fsharp)中回報問題，並歡迎您參與。

您也可以在 [Ionide Gitter 頻道](https://gitter.im/ionide/ionide-project)中向 Ionide 開發人員和 F # 團體要求進一步的協助。

## <a name="next-steps"></a>後續步驟

若要深入瞭解 F # 和語言的功能，請參閱 [f # 導覽](../tour.md)。
