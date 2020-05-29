---
title: 使用 Visual Studio Code 來調試 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio Code 來偵測 .NET Core 主控台應用程式。
ms.date: 05/26/2020
ms.openlocfilehash: eaeb97f54442006d2f0e29483a68dc3de89b5778
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202586"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-code"></a>教學課程：使用 Visual Studio Code 來對 .NET Core 主控台應用程式進行 Debug

本教學課程介紹使用 .NET Core 應用程式的 Visual Studio Code 中可用的偵錯工具。

## <a name="prerequisites"></a>Prerequisites

- 本教學課程適用于您在 Visual Studio Code 中建立[.Net Core 主控台應用程式](with-visual-studio-code.md)中建立的主控台應用程式。

## <a name="use-debug-build-configuration"></a>使用 Debug build configuration

「*調試*程式」和「*發行*」是 .net Core 的組建設定中的兩個。 您可以使用 Debug 組建設定進行偵錯工具，以及發行設定進行最終發行散發。

在 Debug 設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。 程式的發行設定沒有符號的 debug 資訊，而且已完全優化。

 根據預設，Visual Studio Code 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前加以變更。

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」會在含有中斷點的行執行「之前」**，暫時中斷應用程式的執行。

1. 在*Program.cs*中，按一下程式碼視窗的左邊界，在顯示名稱、日期和時間的行上設定*中斷點*。 左邊界位於行號的左邊。 設定中斷點的另一種方式是將游標放在程式程式碼中，然後按<kbd>F9</kbd>鍵。

   如下圖所示，Visual Studio Code 會藉由在左邊界顯示一個紅點，來表示設定中斷點的行。

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="中斷點集":::

## <a name="set-up-for-terminal-input"></a>設定終端機輸入

中斷點位於 `Console.ReadLine` 方法呼叫之後。 **偵錯主控台**不接受執行中程式的終端機輸入。 若要在進行偵錯工具時處理終端機輸入，您可以使用整合式終端機（其中一個 Visual Studio Code 視窗）或外部終端機。 在本教學課程中，您會使用整合式終端機。

1. 開啟 *. vscode/啟動 json*。

1. 將 `console` 設定變更為 `integratedTerminal` 。

   寄件者: 

   ```
   "console": "internalConsole",
   ```

   變更為：

   ```
   "console": "integratedTerminal",
   ```

1. 儲存您的變更。

## <a name="start-debugging"></a>開始偵錯

1. 選取左側功能表上的 [偵錯工具] 圖示，以開啟 [Debug] 視圖。

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="在 Visual Studio Code 中開啟 [偵錯] 索引標籤":::

1. 選取窗格頂端的綠色箭號（在 [ **.Net Core 啟動（主控台）**] 旁邊），開始進行偵錯工具。  另一個開始進行偵錯工具的方式是按<kbd>F5</kbd>。

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="開始偵錯":::

1. 選取 [**終端**機] 索引標籤，以查看「您的名稱是什麼？」 提示程式在等候回應之前顯示。

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="選取 [終端機] 索引標籤":::

1. 在**終端**機視窗中輸入字串，以回應名稱的提示，然後按<kbd>enter</kbd>鍵。

   程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [**變數**] 視窗的 [**區域變數**] 區段會顯示目前正在執行的方法中所定義的變數值。

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="命中中斷點，顯示區域變數":::

## <a name="change-variable-values"></a>變更變數值

[**偵錯主控台**] 視窗可讓您與正在進行偵錯工具的應用程式互動。 您可以變更變數的值，以查看它對您的程式有何影響。

1. 選取 [**偵錯主控台**] 索引標籤。

1. 在 [ `name = "Gracie"` **偵錯主控台**] 視窗底部的提示中輸入，然後按<kbd>enter</kbd>鍵。

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="變更變數值":::

1. `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`在 [**偵錯主控台**] 視窗底部輸入，然後按<kbd>enter</kbd>鍵。

   [**變數**] 視窗會顯示和變數的新值 `name` `date` 。

1. 選取工具列中的 [**繼續**] 按鈕，繼續執行程式。 另一個繼續的方式是按<kbd>F5</kbd>。

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="繼續進行調試":::

1. 再次選取 [**終端**機] 索引標籤。

   主控台視窗中顯示的值會對應至您在**偵錯主控台**中進行的變更。

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="顯示輸入值的終端機":::

1. 按任意鍵以結束應用程式，並停止進行偵錯工具。

## <a name="set-a-conditional-breakpoint"></a>設定條件式中斷點

程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以使用稱為*條件式中斷點*的實用調試功能來測試此項。

1. 在代表中斷點的紅點上按一下滑鼠右鍵（<kbd>Ctrl</kbd>+ 按一下 [macOS]）。 在內容功能表中，選取 [**編輯中斷點**] 以開啟對話方塊，讓您輸入條件運算式。

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="[中斷點] 操作功能表":::

1. `Expression`在下拉式選單中，輸入下列條件運算式，然後按<kbd>enter</kbd>鍵。

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="輸入條件運算式":::

   每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在這一行上中斷 `true` 。

   除了條件運算式以外，您還可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行，或*篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱等屬性來中斷程式執行。

1. 按<kbd>F5</kbd>鍵以進行偵錯工具啟動。

1. 在 [**終端**機] 索引標籤中，當系統提示您輸入您的名稱時，按<kbd>enter</kbd>鍵。

   由於已滿足您指定的條件（ `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType> ），因此程式會在到達中斷點且在方法執行之前停止執行 `Console.WriteLine` 。

   [**變數**] 視窗會顯示變數的值 `name` 為 `""` 、或 <xref:System.String.Empty?displayProperty=nameWithType> 。

1. 在**偵錯主控台**提示字元中輸入下列語句，然後按<kbd>enter</kbd>，以確認此值為空字串。 結果為 `true`。

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="在執行語句之後，偵錯主控台傳回 true 的值":::

1. 選取工具列上的 [繼續]**** 按鈕以繼續程式執行。

1. 選取 [**終端**機] 索引標籤，然後按任意鍵以結束程式並停止偵測。

1. 按一下程式碼視窗左邊界中的點，以清除中斷點。 清除中斷點的另一種方法是在選取程式程式碼時按<kbd>F9</kbd> 。

1. 如果您收到中斷點條件將遺失的警告，請選取 [**移除中斷點**]。

## <a name="step-through-a-program"></a>逐步執行程式

Visual Studio Code 也可讓您逐行執行程式並監視其執行。 一般來說，您會設定中斷點，並在程式碼的一小部分追蹤程式流程。 因為此程式很小，所以您可以逐步執行整個程式。

1. 在方法的左大括弧上設定中斷點 `Main` 。

1. 按 <kbd>F5</kbd> 開始偵錯。

   Visual Studio Code 會反白顯示中斷點行。

   此時，[**變數**] 視窗 `args` 會顯示陣列是空的，而且 `name` 和 `date` 都有預設值。

1. 選取 [**逐步執行**] 或按<kbd>F11</kbd>。

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="[逐步執行] 按鈕":::

   Visual Studio Code 會反白顯示下一行。

1. 選取 [**逐步執行**] 或按<kbd>F11</kbd>。

   Visual Studio Code 會 `Console.WriteLine` 針對名稱提示執行，並反白顯示下一行執行。 下一行是的 `Console.ReadLine` `name` 。 [**變數**] 視窗不變，而且 [**終端**機] 索引標籤會顯示「您的名稱是什麼？」 及時.

1. 選取 [**逐步執行**] 或按<kbd>F11</kbd>。

   Visual Studio 會反白顯示 `name` 變數指派。 [**變數**] 視窗 `name` 會顯示仍然是 `null` 。

1. 在 [終端機] 索引標籤中輸入字串，然後按<kbd>enter</kbd>鍵，以回應提示。

   當您輸入時，[**終端**機] 索引標籤可能不會顯示您輸入的字串，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法會抓取您的輸入。

1. 選取 [**逐步執行**] 或按<kbd>F11</kbd>。

   Visual Studio Code 會反白顯示 `date` 變數指派。 [**變數**] 視窗會顯示呼叫方法時所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。 [**終端**機] 索引標籤會顯示您在提示字元中輸入的字串。

1. 選取 [**逐步執行**] 或按<kbd>F11</kbd>。

   [**變數**] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。

1. 選取 [**逐步執行**] 或按<kbd>F11</kbd>。

   Visual Studio Code 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗會顯示已格式化的字串。

1. 選取 [**跳出**] 或按<kbd>Shift</kbd> + <kbd>F11</kbd>。

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="跳出按鈕":::

1. 選取 [**終端**機] 索引標籤。

   終端機會顯示「按任意鍵結束 ...」

1. 按任意鍵以結束程式。

## <a name="select-release-build-configuration"></a>選取發行組建設定

測試過應用程式的 Debug 版本之後，您也應該編譯和測試發行版本。 發行版本包含可能會影響應用程式行為的編譯器優化。 例如，針對改善效能而設計的編譯器優化，可以在多執行緒應用程式中建立競爭條件。

若要建立並測試主控台應用程式的發行版本，請開啟**終端**機並執行下列命令：

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a>其他資源

* [在 Visual Studio Code 中偵錯](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已使用 Visual Studio Code 調試工具。 若要瞭解如何發佈應用程式的可部署版本，請參閱[發佈您的應用程式](cli-create-console-app.md#publish-your-app)。

<!--In the next tutorial, you publish a deployable version of the app.

> [!div class="nextstepaction"]
> [Publish a .NET Core console application with Visual Studio Code](publishing-with-visual-studio-code.md)
-->
