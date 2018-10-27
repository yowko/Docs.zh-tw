---
title: '開始使用 Visual Studio Code 中的 F #'
description: '了解如何使用 F # 與 Visual Studio Code 和 ionide 使用者外掛程式套件。'
ms.date: 05/28/2018
ms.openlocfilehash: e962be2796cf0d6eb90d459730659e492f864716
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192664"
---
# <a name="get-started-with-f-in-visual-studio-code"></a>開始使用 Visual Studio Code 中的 F #

您可以撰寫 F # [Visual Studio Code](https://code.visualstudio.com)具有[Ionide 外掛程式](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp)若要取得 IntelliSense 與基本的程式碼好跨平台、 輕量級整合式開發環境 (IDE) 體驗重構作業。 請瀏覽[Ionide.io](http://ionide.io)若要深入了解此外掛程式。

若要開始，請確定您已[F # 和 ionide 使用者外掛程式安裝正確](install-fsharp.md#install-f-with-visual-studio-code)。

## <a name="creating-your-first-project-with-ionide"></a>透過 Ionide 建立第一個專案

若要建立新的 F # 專案，開啟 Visual Studio Code （您可以為它命名您喜歡） 的新資料夾中。

接下來，開啟 命令選擇區 (**檢視 > 命令選擇區**) 並輸入下列命令：

```
> F# new project
```

這由[偽造](https://github.com/fsharp-editing/Forge)專案。

> [!NOTE]
如果看不到範本選項，請嘗試重新整理的範本，藉由在命令選擇區中執行下列命令： `>F#: Refresh Project Templates`。

選取 [F #:: 新專案] 點擊**Enter**。 這會帶您前往下一個步驟，也就是選取專案範本。

挑選`classlib`範本，然後按**Enter**。

接下來，選擇要建立的專案中的目錄。 如果保留空白，它會使用目前的目錄。

最後，命名您的專案中的最後一個步驟。 F # 會使用[Pascal 大小寫慣例](http://c2.com/cgi/wiki?PascalCase)專案名稱。 本文章使用`ClassLibraryDemo`做為名稱。 一旦您輸入您想為您的專案的名稱，點擊**Enter**。

如果您遵循上一個步驟，您應該會看到 Visual Studio 程式碼工作區左手邊顯示與下列：

1. F # 專案下, 面`ClassLibraryDemo`資料夾。
2. 新增套件透過正確的目錄結構[ `Paket` ](https://fsprojects.github.io/Paket/)。
3. 跨平台建置指令碼[ `FAKE` ](https://fsharp.github.io/FAKE/)。
4. `paket.exe`可以擷取封裝，並為您解決相依性的可執行檔。
5. A`.gitignore`檔案，如果您想要將此專案新增至 Git 架構原始檔控制。

## <a name="writing-some-code"></a>撰寫一些程式碼

開啟*ClassLibraryDemo*資料夾。  您應該會看到下列檔案：

1. `ClassLibraryDemo.fs`定義的類別與 F # 實作檔。
2. `ClassLibraryDemo.fsproj`F # 專案檔用來建置此專案。
3. `Script.fsx`會載入原始程式檔的 F # 指令碼檔案。
4. `paket.references`指定專案相依性的 Paket 檔案。

開啟`Script.fsx`，並在結尾處新增下列程式碼：

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx)]

此函式會將單字轉換成一種[Pig Latin](https://en.wikipedia.org/wiki/Pig_Latin)。 下一個步驟是使用 F # Interactive (FSI) 進行評估。

反白顯示整個函式 （它應該是很長的 11 行）。 之後它會反白顯示，保存**Alt**鍵並按下**Enter**。 您會發現下面顯示的視窗，並應該會顯示類似如下：

![透過 Ionide 的 F # Interactive 輸出範例](media/getting-started-vscode/vscode-fsi.png)

這會執行三項工作：

1. 它會啟動 FSI 程序。
2. 它透過 FSI 程序傳送您反白顯示的程式碼。
3. FSI 程序會評估您透過傳送的程式碼。

因為您透過傳送[函式](../language-reference/functions/index.md)，您現在可以呼叫該函式與 FSI ！ 在互動式視窗中，輸入下列命令：

```fsharp
toPigLatin "banana";;
```

您應該會看到下列結果：

```fsharp
val it : string = "ananabay"
```

現在，讓我們試一次的第一個字母母音的群組。 輸入下列程式碼：

```fsharp
toPigLatin "apple";;
```

您應該會看到下列結果：

```fsharp
val it : string = "appleyay"
```

函式看起來如預期般運作。 恭喜，您剛在 Visual Studio Code 中撰寫您的第一個 F # 函式，並評估使用 FSI ！

>[!NOTE]
您可能已經注意到，結尾 FSI 中的行`;;`。 這是因為 FSI 可讓您輸入多行。 `;;`結尾可讓 FSI 知道程式碼完成時。

## <a name="explaining-the-code"></a>說明程式碼

如果您不確定程式碼實際上在做什麼，以下是逐步執行精靈。

如您所見，`toPigLatin`是函式會採用做為輸入的字組，並將它轉換成該單字的 Pig Latin 表示法。 此規則如下所示：

如果在 word 中的第一個字元是由某個母音開頭，新增"yay 」 到字尾。 如果它未啟動與母音的群組，移動該第一個字元到字尾，"ay 」 加入它。

您可能已經注意到下列 FSI 中：

```fsharp
val toPigLatin : word:string -> string
```

這指出`toPigLatin`是函式，接受`string`做為輸入 (稱為`word`)，並傳回另一個`string`。 這就所謂[函式的型別簽章](https://fsharpforfunandprofit.com/posts/function-signatures/)，基本的一項 F # 是了解 F # 程式碼的索引鍵。 您也會發現這如果您將滑鼠停留在 Visual Studio Code 中的函式。

在此函式主體中，您會注意到兩個不同的部分：

1. 內部函式，呼叫`isVowel`，，決定如果指定的字元 (`c`) 檢查是否符合其中一個透過提供的模式是母音的群組[模式比對](../language-reference/pattern-matching.md):

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L2-L6)]

2. [ `if..then..else` ](../language-reference/conditional-expressions-if-then-else.md)檢查是否第一個字元是母音的群組，並傳回值超出輸入字元的建構基礎 if 的第一個字元的運算式是否母音的群組：

   [!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/to-pig-latin.fsx#L8-L11)]

流程`toPigLatin`因此：

檢查是否輸入單字的第一個字元是母音的群組。 如果是，將 「 yay"附加到字尾。 否則，移動該第一個字元到字尾，而且"ay 」 加入它。

沒有一個最後的一件事来注意一點： 沒有任何明確指令來從與許多其他語言有不同的函式傳回。 這是因為 F # 是以運算式為基礎，而且在函式主體中的最後一個運算式傳回的值。 因為`if..then..else`本身是運算式的主體`then`區塊或主體`else`區塊將會傳回輸入的值而定。

## <a name="moving-your-script-code-into-the-implementation-file"></a>將您的指令碼移到實作檔案

在本文中先前各節示範常見的第一個步驟，在撰寫 F # 程式碼： 撰寫的初始函式和以 FSI 以互動方式執行。 這也稱為 REPL 為導向的開發，其中[REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)代表 「 讀取-評估-列印迴圈 」。 它是適合用來試驗功能，直到您完全運作。

REPL 導向開發方法的下一個步驟是將工作程式碼移至 F # 實作檔。 它接著要編譯的 F # 編譯器可以執行的組件。

若要開始，請開啟`ClassLibraryDemo.fs`。  您會發現，一些程式碼已經在存在。 請繼續並刪除類別定義，但請務必保留[ `namespace` ](../language-reference/namespaces.md)頂端的宣告。

接下來，建立新[ `module` ](../language-reference/modules.md)稱為`PigLatin`並複製`toPigLatin`函式匯入它，例如：

[!code-fsharp[ToPigLatin](../../../samples/snippets/fsharp/getting-started/pig-latin.fs#L1-L14)]

接下來，開啟`Script.fsx`同樣地，檔案，並刪除整個`toPigLatin`函式，但請務必保持檔案中的下列兩行：

```fsharp
#load "ClassLibraryDemo.fs"
open ClassLibraryDemo
```

第一行所需的指令碼載入 FSI `ClassLibraryDemo.fs`。 第二行可讓您輕鬆： 省略它是選擇性的但您必須輸入`open ClassLibraryDemo`FSI 視窗，如果您想要讓`ToPigLatin`進入範圍內的模組。

接下來，在 FSI 視窗中，呼叫函式搭配`PigLatin`您稍早定義的模組：

```
> PigLatin.toPigLatin "banana";;
val it : string = "ananabay"
> PigLatin.toPigLatin "apple";;
val it : string = "appleyay"
```

成功！ 取得與之前相同的結果，但現在從 F # 實作檔載入。 此處的主要差異是 F # 原始程式檔會編譯成組件可不只是在 FSI 隨處執行。

## <a name="summary"></a>總結

在本文中，您已了解：

1. 如何設定 Visual Studio Code，透過 Ionide。
2. 如何透過 Ionide 建立第一個 F # 專案。
3. 如何使用 ionide 使用者撰寫您的第一個 F # 函式，然後將它執行 FSI 中的 F # 指令碼。
4. 如何將您的指令碼移轉至 F # 原始程式檔，並接著從 FSI 呼叫該程式碼。

您要現在可以撰寫更多 F # 程式碼使用 Visual Studio Code 和 ionide 使用者。

## <a name="troubleshooting"></a>疑難排解

以下是幾種方式，您可以針對某些您可能會遇到的問題進行疑難排解：

1. 若要取得程式碼編輯 ionide 使用者的功能，您的 F # 檔案必須儲存到磁碟，然後在 Visual Studio Code 工作區中開啟的資料夾內。
2. 如果您已對您的系統中的變更，或使用開啟的 Visual Studio Code 安裝 Ionide 必要條件，請重新啟動 Visual Studio Code。
3. 請檢查您可以使用 F # 編譯器和 F # interactive 命令列，而不需要完整的路徑。 則可以輸入`fsc`F # 編譯器命令列中並`fsi`或`fsharpi`Visual F # 工具在 Windows 和 Mac/Linux 上的 Mono 上分別。
4. 如果您在專案目錄中有無效的字元，ionide 使用者可能無法運作。  如果發生這種情況，請重新命名您的專案目錄。
5. 如果使用 none Ionide 命令時，請檢查您[Visual Studio Code 按鍵繫結關係](https://code.visualstudio.com/docs/customization/keybindings#_customizing-shortcuts)以查看 如果您要覆寫它們意外。
6. 如果 Ionide 已損毀您的電腦上，並以上皆非已修正您的問題，請嘗試移除`ionide-fsharp`目錄在您的電腦上重新安裝的外掛程式套件。

Ionide 是開放原始碼專案所建立與維護的 F # 社群的成員。 請回報問題，並歡迎您在參與[Ionide VSCode: FSharp GitHub 存放庫](https://github.com/ionide/ionide-vscode-fsharp)。

如果您有要報告的問題，請遵循[取得的記錄檔使用時回報問題的指示](https://github.com/ionide/ionide-vscode-fsharp#how-to-get-logs-for-debugging--issue-reporting)。

您也可以要求取得進一步的協助從 Ionide 開發人員和 F # 社群[Ionide Gitter 通道](https://gitter.im/ionide/ionide-project)。

## <a name="next-steps"></a>後續步驟

若要深入了解 F # 和語言的功能，請參閱[的 F # 教學課程](../tour.md)。
