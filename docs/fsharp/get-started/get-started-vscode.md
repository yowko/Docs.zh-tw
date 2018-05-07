---
title: '開始使用 F # 在 Visual Studio 程式碼'
description: '了解如何使用 F # 與 Visual Studio 程式碼和 Ionide 外掛程式套件。'
ms.date: 02/28/2018
ms.openlocfilehash: 71cc0abfd8420794485d38e91efd9819379e3f55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="get-started-with-f-in-visual-studio-code"></a>開始使用 F # 在 Visual Studio 程式碼

您可以撰寫 F # [Visual Studio Code](https://code.visualstudio.com)與[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)，若要取得跨平台的輕量型 (Integrade 開發 Enivronment) IDE 體驗 IntelliSense 和基本的程式碼重構。  請瀏覽[Ionide.io](http://ionide.io)若要深入了解外掛程式套件。

## <a name="prerequisites"></a>必要條件

您必須擁有[安裝 git](https://git-scm.com/download)並可使用您的路徑，請使用專案中的範本 Ionide。  您可以確認它已正確安裝輸入`git --version`在命令提示字元並按**Enter**。

### <a name="macostabmacos"></a>[macOS](#tab/macos)

使用 Ionide [Mono](http://www.mono-project.com)。  安裝 Mono macOS 上最簡單的方式是透過 Homebrew。  只要您的終端機中輸入下列命令：

```
brew install mono
```

您也必須安裝[.NET Core SDK](https://www.microsoft.com/net/download)。

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

在 Linux 上 Ionide 也會使用[Mono](https://www.mono-project.com)。 如果您是在 Debian 或 Ubuntu 上，您可以使用下列項目：

```
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

您也必須安裝[.NET Core SDK](https://www.microsoft.com/net/download)。

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

如果您在 Windows 上，您必須[使用 F # 支援安裝 Visual Studio](get-started-visual-studio.md#installing-f)。 這會安裝所有必要的元件，來撰寫、 編譯及執行 F # 程式碼。

您也必須安裝[.NET Core SDK](https://www.microsoft.com/net/download/)。

---

## <a name="installing-visual-studio-code-and-the-ionide-plugin"></a>安裝 Visual Studio 程式碼和 Ionide 外掛程式

您可以安裝 Visual Studio 程式碼從[code.visualstudio.com](https://code.visualstudio.com)網站。 在這之後，有兩種方式可尋找 Ionide 外掛程式：

1. 使用命令選擇區 (Ctrl + Shift + P ⌘ + Shift + P macOS，Ctrl + Shift + P on Linux 上的 Windows 上)，並輸入下列命令：

    ```
    >ext install Ionide
    ```

2. 按一下 擴充功能圖示並搜尋"Ionide 」:

    ![](media/getting-started-vscode/vscode-ext.png)

只有 Visual Studio 程式碼中的 F # 支援所需的外掛程式[Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)。 不過，您也可以安裝[Ionide FAKE](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE)並取得[偽造](https://fsharp.github.io/FAKE/)支援和[Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket)取得[Paket](https://fsprojects.github.io/Paket/)支援。 假造而且 Paket 其他 F # 社群工具，以建置專案，並且分別管理的相依性。

## <a name="creating-your-first-project-with-ionide"></a>使用 Ionide 建立第一個專案

若要建立新的 F # 專案，請在新的資料夾 （您可以將檔案命名任何您喜歡） 中開啟 Visual Studio 程式碼。

![](media/getting-started-vscode/vscode-open-dir.png)

接下來，開啟命令選擇區 (Ctrl + Shift + P ⌘ + Shift + P macOS，Ctrl + Shift + P on Linux 上的 Windows 上)，並輸入下列命令：

```
>f#: New Project
```

這由[FORGE](https://github.com/fsharp-editing/Forge)專案。  您應該會看到類似下面的內容：

![](media/getting-started-vscode/vscode-new-proj.png)

> [!NOTE]
如果您沒有看到上述項目，再試一次命令選擇區中執行下列命令，以重新整理範本： `>F#: Refresh Project Templates`。

選取 「 F #:: 新專案 」，請按**Enter**，這會帶您前往此步驟：

![](media/getting-started-vscode/vscode-proj-type.png)

這樣會選取特定類型的專案範本。  有相當幾個選項，例如[FsLab](https://fslab.org)用於資料科學的範本或[Suave](https://suave.io) Web 程式設計的範本。  本文使用`classlib`範本，因此反白顯示，並叫用**Enter**。  然後，您會到達下一個步驟：

![](media/getting-started-vscode/vscode-new-dir.png)

這可讓您想要的話，在不同的目錄中，建立專案。  保留空白目前。  它會在目前的目錄建立專案。  一旦您按下**Enter**，您會到達下一個步驟：

![](media/getting-started-vscode/vscode-proj-name.png)

這可讓您命名您的專案。  F # 使用[Pascal 案例](http://c2.com/cgi/wiki?PascalCase)專案名稱。  本文使用`ClassLibraryDemo`做為名稱。  一旦您輸入您想要為您的專案的名稱，叫用**Enter**。

如果您遵循上述步驟的步驟，您應該取得 Visual Studio 程式碼工作區左邊看起來像這樣：

![](media/getting-started-vscode/vscode-new-proj-explorer.png)

此範本會產生幾件事，您會發現很有用：

1. F # 專案本身，在底下`ClassLibraryDemo`資料夾。
2. 新增套件透過正確的目錄結構[ `Paket` ](https://fsprojects.github.io/Paket/)。
3. 跨平台建置指令碼[ `FAKE` ](https://fsharp.github.io/FAKE/)。
4. `paket.exe`可執行檔可以擷取封裝，並讓您解析的相依性。
5. A`.gitignore`檔案，如果您想要將這個專案加入 Git 架構的原始檔控制。

## <a name="writing-some-code"></a>撰寫一些程式碼

開啟*ClassLibraryDemo*資料夾。  您應該會看到下列檔案：

1. `ClassLibraryDemo.fs`定義的類別具有的 F # 實作檔案。
2. `CassLibraryDemo.fsproj`F # 專案檔用來建置此專案。
3. `Script.fsx`為 F # 指令碼檔案，檔案載入原始程式檔。
4. `paket.references`指定專案相依性的 Paket 檔案。

開啟`Script.fsx`，並在結尾處加入下列程式碼：

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

此函式會將文字轉換成一種[Pig 拉丁](https://en.wikipedia.org/wiki/Pig_Latin)。  下一步是評估使用 F # Interactive (FSI)。

反白顯示整個函式 （應為 11 行長度）。  一旦會反白顯示，保存**Alt**金鑰並點擊**Enter**。  您會發現下面顯視窗，它應該會顯示結果類似這樣：

![](media/getting-started-vscode/vscode-fsi.png)

這並未三件事：

1. 它會啟動 FSI 程序。
2. 它透過 FSI 程序傳送您反白顯示的程式碼。
3. FSI 程序會評估您透過傳送的程式碼。

因為您透過傳送[函式](../language-reference/functions/index.md)，您現在可以呼叫該函式與 FSI ！  在互動式視窗中，輸入下列命令：

```fsharp
toPigLatin "banana";;
```

您應該會看到下列結果：

```fsharp
val it : string = "ananabay"
```

現在，讓我們再一次與第一個字母母音。 輸入下列程式碼：

```fsharp
toPigLatin "apple";;
```

您應該會看到下列結果：

```fsharp
val it : string = "appleyay"
```

此函式會出現無法如預期般運作。  恭喜您，只需要在 Visual Studio 程式碼撰寫您的第一個 F # 函式，並評估與 FSI ！

>[!NOTE]
您可能已經注意到，在以結束 FSI 中的線條`;;`。  這是因為 FSI 可讓您輸入多行。  `;;`結尾可讓 FSI 知道完成程式碼。

## <a name="explaining-the-code"></a>說明程式碼

如果您不確定程式實際上做什麼的程式碼，以下是逐步。

如您所見，`toPigLatin`是函式會取得做為輸入的文字，並將它轉換成該單字的 Pig 拉丁表示法。  這個規則如下所示：

在 word 中的第一個字元開頭母音，"鐘樓"加入文字的結尾。  如果它不會以某個母音開頭，將該第一個字元移至文字的結尾，加入 「 可能 」。

您可能已注意到 FSI 中的下列：

```
val toPigLatin : word:string -> string
```

這指出`toPigLatin`是函式會接受`string`做為輸入 (稱為`word`)，並傳回另一個`string`。  這稱為[函式的類型簽章](https://fsharpforfunandprofit.com/posts/function-signatures/)，F # 是要了解 F # 程式碼索引鍵的基本部分。  您也會發現這如果您將滑鼠停留在 Visual Studio 程式碼中的函式。

在函式的主體中，您會發現兩個不同的部分：

1. 內部的函式，呼叫`isVowel`，決定如果指定的字元 (`c`) 會編碼母音方法是檢查它是否符合其中一個提供的模式透過[模式比對](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)的檢查，如果第一個字元是母音，而且建構超出輸入的字元傳回值為基礎的運算式 if 的第一個字元已母音或未驗證：

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

流程`toPigLatin`因此：

檢查輸入的字組的第一個字元是否為某個母音。  如果是，請將"鐘樓"附加至文字的結尾。  否則，將該第一個字元移至文字的結尾，加入 「 可能 」。

沒有最後一注意到關於此： 沒有任何明確指令來從與許多其他語言有不同的函式傳回。  這是因為 F # 是以運算式為基礎，並在函式主體中的最後一個運算式是傳回的值。  因為`if..then..else`本身是運算式的主體`then`區塊或內文`else`區塊將會傳回輸入值而定。

## <a name="moving-your-script-code-into-the-implementation-file"></a>將您的指令碼移到實作檔

這篇文章中的先前各節示範常見的第一個步驟，在撰寫 F # 程式碼： 撰寫初始的函式，然後使用 FSI 以互動方式執行。  這稱為 REPL 導向的開發，其中 REPL 代表 「 讀取評估列印迴圈 」。  它是實驗功能，直到您有工作的好方法。

REPL 導向的開發工作的下一個步驟是將使用中程式碼移至 F # 實作檔。  它可以再編譯 F # 編譯器為可執行的組件。

若要開始，請開啟`ClassLibraryDemo.fs`。  您會發現，某些程式碼已在有。  請繼續並刪除類別定義中，但請務必保留[ `namespace` ](../language-reference/namespaces.md)頂端的宣告。

接下來，建立新[ `module` ](../language-reference/modules.md)呼叫`PigLatin`並複製`toPigLatin`函式匯入它在這種情況：

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

這是您可以將組織中 F # 程式碼，函式和常見的方法如果您也想要從 C# 或 Visual Basic 專案中呼叫程式碼是有許多方法。

接下來，開啟`Script.fsx`檔案一次，並刪除整個`toPigLatin`函式，但務必要保留檔案中的下列兩行：

```
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

FSI 以載入指令碼所需的第一行`ClassLibraryDemo.fs`。  第二行在於其便利性： 略過為選擇性，但是您必須輸入`open ClassLibraryDemo`FSI 視窗，如果您想要將`ToPigLatin`模組納入範圍。

接下來，在 FSI 視窗中，呼叫函式`PigLatin`先前定義的模組：

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

成功！  取得與之前相同的結果，但現在已從 F # 實作檔案載入。  此處的主要差異是 F # 原始程式檔會編譯成執行 FSI 不只是在任何地方、 組件。

## <a name="summary"></a>總結

在本文中，您學到：

1. 如何設定與 Ionide Visual Studio 程式碼。
2. 如何使用 Ionide 建立第一個 F # 專案。
3. 如何使用 F # 指令碼處理 Ionide 中撰寫您的第一個 F # 函式，然後將它執行 FSI 中。
4. 如何將指令碼移轉至 F # 原始程式檔，然後從 FSI 呼叫該程式碼。

您現在要寫入更多 F # 程式碼使用 Visual Studio 程式碼和 Ionide 配備。

## <a name="troubleshooting"></a>疑難排解

以下是您可以疑難排解特定問題，您可能會遇到的幾個方法：

1. 若要取得程式碼編輯 Ionide 的功能，您的 F # 檔案需要儲存到磁碟，然後在 Visual Studio 程式碼工作區中開啟的資料夾內。
2. 如果您變更您的系統或 Ionide 必要條件安裝 Visual Studio 程式碼開啟，請重新啟動 Visual Studio 程式碼。
3. 請檢查您可以使用 F # 編譯器和 F # interactive 從命令列不完整的路徑。  您可以輸入`fsc`對於 F # 編譯器，命令列中和`fsi`或`fsharpi`Visual F # 工具在 Windows 和 Mac/Linux 上的 Mono 上分別。
4. 如果您在專案目錄中有無效的字元，Ionide 可能無法運作。  如果發生這種情況，請重新命名專案目錄。
5. 如果使用無 Ionide 命令，請檢查您[Visual Studio Code 按鍵組合](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)查看如果您要覆寫的它們不小心。
6. 如果您的電腦上中斷 Ionide 上述都無法有固定的問題，請嘗試移除`ionide-fsharp`目錄在電腦上重新安裝外掛程式套件。

Ionide 是開放原始碼專案所建立與維護由 F # 社群的成員。  請報告問題，並隨意在參與[Ionide VSCode: FSharp GitHub 儲存機制](https://github.com/ionide/ionide-vscode-fsharp)。

如果您有要報告的問題，請遵循[取得記錄檔使用 回報問題時的指示](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。

您也可以要求取得進一步的協助從 Ionide 開發人員和 F # 中的社群[Ionide Gitter 通道](https://gitter.im/ionide/ionide-project)。

## <a name="next-steps"></a>後續步驟

若要深入了解 F # 和語言的功能，請參閱[教學課程的 F #](../tour.md)。

## <a name="see-also"></a>另請參閱

[F# 的教學課程](../tour.md)

[F# 語言參考](../language-reference/index.md)

[函式](../language-reference/functions/index.md)

[模組](../language-reference/modules.md)

[命名空間](../language-reference/namespaces.md)

[Ionide VSCode: FSharp](https://github.com/ionide/ionide-vscode-fsharp)
