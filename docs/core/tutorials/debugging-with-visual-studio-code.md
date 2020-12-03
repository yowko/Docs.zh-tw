---
title: 使用 Visual Studio Code 來對 .NET 主控台應用程式進行偵錯工具
description: 瞭解如何使用 Visual Studio Code 來進行 .NET 主控台應用程式的偵錯工具。
ms.date: 05/26/2020
ms.openlocfilehash: 7215ed4a93b31ebac313c04708734667148c4e02
ms.sourcegitcommit: 30fef5b0ed76e334377d28fa8e80159b29353e10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96556105"
---
# <a name="tutorial-debug-a-net-console-application-using-visual-studio-code"></a>教學課程：使用 Visual Studio Code 來對 .NET 主控台應用程式進行偵錯工具

本教學課程介紹可在 Visual Studio Code 中使用的偵錯工具，以使用 .NET 應用程式。

## <a name="prerequisites"></a>先決條件

- 本教學課程適用于您 [使用 Visual Studio Code 建立 .net 主控台應用程式](with-visual-studio-code.md)中所建立的主控台應用程式。

## <a name="use-debug-build-configuration"></a>使用 Debug build configuration

*Debug* 和 *Release* 是 .net Core 的內建組建設定。 您可以使用 Debug 組建設定進行偵錯工具，並使用發行設定來進行最終發行散發。

在「偵錯工具」設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。 程式的發行設定沒有符號的 debug 資訊，而且已完全優化。

根據預設，Visual Studio Code 啟動設定會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前加以變更。

1. 啟動 Visual Studio Code。

1. 開啟您在 [使用 Visual Studio Code 建立 .net 主控台應用程式](with-visual-studio-code.md)中建立的專案資料夾。

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。

1. 開啟 *Program.cs* 檔案。

1. 在程式碼視窗的左邊界中按一下，在顯示名稱、日期和時間的行上設定 *中斷點* 。 左邊界是行號的左邊。 設定中斷點的其他方式是按 <kbd>F9</kbd> ，或在 **Run**  >  選取程式程式碼時，從功能表中選擇 [執行 **切換中斷點**]。

   Visual Studio Code 表示在左邊界中顯示紅點來設定中斷點的行。

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-set.png" alt-text="已設定中斷點":::

## <a name="set-up-for-terminal-input"></a>設定終端機輸入

中斷點位於 `Console.ReadLine` 方法呼叫之後。 **偵錯主控台** 不接受執行程式的終端機輸入。 若要在偵錯時處理終端輸入，您可以使用整合式終端 (其中一個 Visual Studio Code 視窗) 或外部終端。 針對此教學課程，您會使用整合式終端。

1. 開啟 *.vscode/launch.json*。

1. 將 `console` 設定從變更 `internalConsole` 為 `integratedTerminal` ：

   ```json
   "console": "integratedTerminal",
   ```

1. 儲存您的變更。

## <a name="start-debugging"></a>開始偵錯

1. 選取左側功能表上的 [偵錯工具] 圖示，以開啟 [偵錯工具]。

   :::image type="content" source="media/debugging-with-visual-studio-code/select-debug-pane.png" alt-text="在 Visual Studio Code 中開啟 [偵錯] 索引標籤":::

1. 選取窗格頂端的綠色箭號，在 [ **.Net Core 啟動] (主控台)** 旁。 在偵測模式下啟動程式的其他方式是按 <kbd>F5</kbd> ，或從功能表中選擇 [**執行**  >  **開始調試** 程式]。

   :::image type="content" source="media/debugging-with-visual-studio-code/start-debugging.png" alt-text="開始調試":::

1. 選取 [ **終端** 機] 索引標籤，以查看「您的姓名為何？」 提示程式在等候回應之前顯示。

   :::image type="content" source="media/debugging-with-visual-studio-code/select-terminal.png" alt-text="選取 [終端機] 索引標籤":::

1. 在 **終端** 機視窗中輸入字串，以回應提示輸入名稱，然後按 <kbd>enter</kbd>。

   程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [**變數**] 視窗的 [**區域變數**] 區段會顯示目前正在執行的方法中所定義變數的值。

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-hit.png" alt-text="點擊中斷點，顯示區域變數":::

## <a name="use-the-debug-console"></a>使用偵錯主控台

**偵錯主控台** 視窗可讓您與您要進行偵錯工具的應用程式互動。 您可以變更變數的值，以查看它對您的程式有何影響。

1. 選取 [ **偵錯主控台** ] 索引標籤。

1. 在 `name = "Gracie"` **偵錯主控台** 視窗底部的提示字元中輸入，然後按 <kbd>enter</kbd> 鍵。

   :::image type="content" source="media/debugging-with-visual-studio-code/change-variable-values.png" alt-text="變更變數值":::

1. `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`在 **偵錯主控台** 視窗的底部輸入，然後按下 <kbd>enter</kbd>鍵。

   [ **變數** ] 視窗會顯示和變數的新值 `name` `date` 。

1. 選取工具列中的 [ **繼續** ] 按鈕，以繼續程式執行。 另一個繼續的方法是按 <kbd>F5</kbd>。

   :::image type="content" source="media/debugging-with-visual-studio-code/continue-debugging.png" alt-text="繼續進行調試":::

1. 再次選取 [ **終端** 機] 索引標籤。

   [主控台] 視窗中顯示的值會對應到您在 **偵錯主控台** 中所做的變更。

   :::image type="content" source="media/debugging-with-visual-studio-code/changed-variable-values.png" alt-text="顯示輸入值的終端機":::

1. 按任意鍵以結束應用程式，並停止偵錯工具。

## <a name="set-a-conditional-breakpoint"></a>設定條件式中斷點

程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以使用稱為 *條件式中斷點* 的實用調試功能來進行測試。

1. 以滑鼠右鍵按一下 (<kbd>Ctrl</kbd>-按一下代表中斷點的紅點上的 macOS) 。 在內容功能表中，選取 [ **編輯中斷點** ] 以開啟可讓您輸入條件運算式的對話方塊。

   :::image type="content" source="media/debugging-with-visual-studio-code/breakpoint-context-menu.png" alt-text="[中斷點] 操作功能表":::

1. `Expression`在下拉式清單中選取，輸入下列條件運算式，然後按<kbd>enter</kbd>鍵。

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/conditional-expression.png" alt-text="輸入條件運算式":::

   每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在此行上中斷 `true` 。

   您可以指定叫用 *計數*（而不是條件運算式），以在指定的次數執行語句之前中斷程式執行。 另一個選項是指定 *篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱，以這類屬性來中斷程式執行。

1. 按下 <kbd>F5</kbd>來啟動程式並進行偵錯工具。

1. 在 [ **終端** 機] 索引標籤中，當系統提示您輸入名稱時，請按 <kbd>enter</kbd> 鍵。

   因為您 (指定的條件 `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>) 已滿足，所以程式執行會在到達中斷點時，以及 `Console.WriteLine` 方法執行之前停止。

   [ **變數** ] 視窗會顯示變數的值 `name` 為 `""` 、或 <xref:System.String.Empty?displayProperty=nameWithType> 。

1. 在 **偵錯主控台** 提示字元中輸入下列語句，並按 <kbd>enter</kbd>鍵，確認值為空字串。 結果為 `true`。

   ```csharp
   name == String.Empty
   ```

   :::image type="content" source="media/debugging-with-visual-studio-code/expression-in-debug-console.png" alt-text="偵錯主控台在執行語句之後傳回值 true":::

1. 選取工具列上的 [繼續] 按鈕以繼續程式執行。

1. 選取 [ **終端** 機] 索引標籤，然後按任意鍵以結束程式並停止偵錯工具。

1. 按一下程式碼視窗左邊界中的點，以清除中斷點。 清除中斷點的其他方式是在選取程式程式碼時，按 <kbd>F9</kbd> 或從功能表中選擇 [ **執行] > 切換中斷點** 。

1. 如果您收到警告，指出中斷點條件將會遺失，請選取 [ **移除中斷點**]。

## <a name="step-through-a-program"></a>逐步執行程式

Visual Studio Code 也可讓您逐行執行程式並監視其執行情況。 一般來說，您會設定中斷點，並遵循程式流程程式碼的一小部分。 因為這個程式很小，所以您可以逐步執行整個程式。

1. 在方法的左大括弧上設定中斷點 `Main` 。

1. 按 <kbd>F5</kbd> 開始偵錯。

   Visual Studio Code 反白顯示中斷點線。

   此時，[ **變數** ] 視窗 `args` 會顯示陣列是空的，而且 `name` `date` 具有預設值。

1. 選取 [**執行**  >  **步驟**] 或按 <kbd>F11</kbd>鍵。

   :::image type="content" source="media/debugging-with-visual-studio-code/step-into.png" alt-text="[逐步執行] 按鈕":::

   Visual Studio Code 反白顯示下一行。

1. 選取 [**執行**  >  **步驟**] 或按 <kbd>F11</kbd>鍵。

   Visual Studio Code 會執行 `Console.WriteLine` 名稱提示的，並反白顯示下一行執行。 下一行是的 `Console.ReadLine` `name` 。 [ **變數** ] 視窗不會變更，且 [ **終端** 機] 索引標籤會顯示「您的名稱為何？」 提示。

1. 選取 [**執行**  >  **步驟**] 或按 <kbd>F11</kbd>鍵。

   Visual Studio 會反白顯示 `name` 變數指派。 [ **變數** ] 視窗 `name` 會顯示仍然是 `null` 。

1. 在 [終端機] 索引標籤中輸入字串，然後按 <kbd>enter</kbd>，以回應提示。

   當您輸入時，[ **終端** 機] 索引標籤可能不會顯示您輸入的字串，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法將會捕捉您的輸入。

1. 選取 [**執行**  >  **步驟**] 或按 <kbd>F11</kbd>鍵。

   Visual Studio Code 會反白顯示 `date` 變數指派。 [ **變數** ] 視窗會顯示呼叫方法所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。 [ **終端** 機] 索引標籤會顯示您在提示字元中輸入的字串。

1. 選取 [**執行**  >  **步驟**] 或按 <kbd>F11</kbd>鍵。

   [ **變數** ] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。

1. 選取 [**執行**  >  **步驟**] 或按 <kbd>F11</kbd>鍵。

   Visual Studio Code 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗會顯示已格式化的字串。

1. 選取 [**執行**  >  **跳出**] 或按 <kbd>Shift</kbd> + <kbd>F11</kbd>。

   :::image type="content" source="media/debugging-with-visual-studio-code/step-out.png" alt-text="跳出按鈕":::

1. 選取 [ **終端** 機] 索引標籤。

   終端機會顯示「按任意鍵結束 ...」

1. 按任意鍵以結束該程式。

## <a name="use-release-build-configuration"></a>使用發行組建設定

測試應用程式的偵錯工具版本之後，您應該也要編譯並測試發行版本。 發行版本所併入的編譯器優化，可能會影響應用程式的行為。 例如，針對改善效能而設計的編譯器優化，可能會在多執行緒應用程式中建立競爭條件。

若要建立並測試您主控台應用程式的發行版本，請開啟 **終端** 機並執行下列命令：

```dotnetcli
dotnet run --configuration Release
```

## <a name="additional-resources"></a>其他資源

* [在 Visual Studio Code 中偵錯](https://code.visualstudio.com/docs/editor/debugging)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已使用 Visual Studio Code 調試工具。 在下一個教學課程中，您將發行應用程式的可部署版本。

> [!div class="nextstepaction"]
> [使用 Visual Studio Code 發佈 .NET 主控台應用程式](publishing-with-visual-studio-code.md)
