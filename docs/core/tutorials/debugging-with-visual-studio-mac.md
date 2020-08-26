---
title: 使用 Visual Studio for Mac 來對 .NET Core 主控台應用程式進行偵錯工具
description: 瞭解如何使用 Visual Studio Mac 來對 .NET Core 主控台應用程式進行 debug 錯。
ms.date: 06/08/2020
ms.openlocfilehash: 79936fb99d0bc37c1234eb8f227eb5415ae48b93
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867564"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio-for-mac"></a>教學課程：使用 Visual Studio for Mac 對 .NET Core 主控台應用程式進行偵錯工具

本教學課程介紹 Visual Studio for Mac 中提供的調試工具。

## <a name="prerequisites"></a>先決條件

- 本教學課程適用于您 [使用 Visual Studio for Mac 建立 .Net Core 主控台應用程式](with-visual-studio-mac.md)中所建立的主控台應用程式。

## <a name="use-debug-build-configuration"></a>使用 Debug build configuration

*Debug* 和 *Release* 是 Visual Studio 的內建組建設定。 您可以使用 Debug 組建設定進行偵錯工具，並使用發行設定來進行最終發行散發。

在「偵錯工具」設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。 程式的發行設定沒有符號的 debug 資訊，而且已完全優化。

根據預設，Visual Studio 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前進行變更。

1. 開始 Visual Studio for Mac。

1. 開啟您在 [使用 Visual Studio for Mac 建立 .Net Core 主控台應用程式](with-visual-studio-mac.md)中建立的專案。

   目前的組建組態會顯示在工具列上。 下列工具列影像顯示 Visual Studio 設定為編譯應用程式的偵錯工具版本：

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-debug.png" alt-text="醒目提示反白顯示的 Visual Studio 工具列":::

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」** 會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。

1. 在顯示名稱、日期和時間的行上設定中斷點。 若要這樣做，請將游標放在程式程式碼中，然後按<kbd>⌘</kbd> <kbd>\\</kbd> (<kbd>命令</kbd> + <kbd>\\</kbd>) 。 設定中斷點的另一種方式是， **Run**  >  從功能表中選取 [執行**切換中斷點**]。

   Visual Studio 表示藉由反白顯示中斷點，並在左邊界中顯示紅點，來設定中斷點的行。

   :::image type="content" source="media/debugging-with-visual-studio-mac/set-breakpoint-in-editor.png" alt-text="已設定中斷點的 Visual Studio 程式視窗":::

1. 按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) ，以在偵測模式中啟動程式。 啟動偵錯工具的另一種方式是從功能表中選擇 [**執行**  >  **開始調試**程式]。

1. 當程式提示您輸入名稱時，在終端機視窗中輸入字串，然後按 <kbd>enter</kbd>鍵。

1. 在方法執行之前，程式執行會在到達中斷點時停止 `Console.WriteLine` 。

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-hit.png" alt-text="Visual Studio 中中斷點的螢幕擷取畫面":::

## <a name="use-the-immediate-window"></a>使用即時運算視窗

[即時 **運算] 視窗** 可讓您與您要進行偵錯工具的應用程式互動。 您可以互動方式變更變數的值，以查看它對您的程式有何影響。

1. 如果看**不到 [** 即時運算] 視窗，請選擇 [立即**觀看**  >  **Debug pad**] 來顯示它  >  ** **。

1. `name = "Gracie"`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。

1. `date = date.AddDays(1)`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。

   [即時 **運算] 視窗** 會顯示字串變數的新值和值的屬性 <xref:System.DateTime> 。

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window.png" alt-text="Visual Studio 中的 [即時運算] 視窗":::

   [區域變數]**** 視窗會顯示目前正在執行的方法中所定義變數的值。 您剛剛變更之變數的值會在 [ **區域變數** ] 視窗中更新。

   :::image type="content" source="media/debugging-with-visual-studio-mac/locals-window.png" alt-text="Visual Studio 中的 [區域變數] 視窗":::

1. 按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以繼續進行調試。

   顯示在終端機中的值會對應到您在 [即時 **運算] 視窗** 中所做的變更。

   如果您看不到終端機，請選取底部導覽列中的 [ **終端機-HelloWorld** ]。

   :::image type="content" source="media/debugging-with-visual-studio-mac/terminal-hello-world.png" alt-text="底部導覽列中的終端 Hello World":::

1. 按任意鍵以結束程式。

1. 關閉終端機視窗。

## <a name="set-a-conditional-breakpoint"></a>設定條件式中斷點

程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以使用稱為 *條件式中斷點*的實用調試功能來進行測試。

1. <kbd>ctrl</kbd>-按一下代表中斷點的紅點。 在內容功能表中，選取 [ **編輯中斷點**]。

1. 在 [ **編輯中斷點** ] 對話方塊中，在下欄欄位中輸入下列程式碼， **並將下列條件設為 true**， **然後選取**[套用]。

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   :::image type="content" source="media/debugging-with-visual-studio-mac/breakpoint-settings.png" alt-text="顯示中斷點設定面板的編輯器":::

   每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在此行上中斷 `true` 。

   您可以指定叫用 *計數*（而不是條件運算式），以在指定的次數執行語句之前中斷程式執行。

1. 按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以開始進行調試。

1. 當系統提示您輸入名稱時，請在終端機視窗中按下 <kbd>enter</kbd> 。

   因為您 (指定的條件 `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>) 已滿足，所以程式執行會在到達中斷點時停止。

1. 選取 [ **區域變數** ] 視窗，此視窗會顯示目前正在執行之方法的本機變數值。 在此案例中， `Main` 是目前執行的方法。 請注意，變數的值 `name` 是 `""` ，也就是 <xref:System.String.Empty?displayProperty=nameWithType> 。

1. 您也可以 `name` 在 [即時運算] 視窗中輸入變數名稱，然後按<kbd>enter</kbd>， **Immediate**以查看值是否為空字串。

   :::image type="content" source="media/debugging-with-visual-studio-mac/immediate-window-output.png" alt-text="顯示名稱為空字串的 [即時運算] 視窗":::

1. 按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以繼續進行調試。

1. 在終端機視窗中，按任意鍵以結束程式。

1. 關閉終端機視窗。

1. 按一下程式碼視窗左邊界的紅點，以清除中斷點。 清除中斷點的另一種方式是在選取程式程式碼時，選擇 [ **執行] > 切換中斷點** 。

## <a name="step-through-a-program"></a>逐步執行程式

Visual Studio 也可讓您逐行執行程式並監視其執行情況。 一般來說，您會設定中斷點，並遵循程式流程程式碼的一小部分。 因為這個程式很小，所以您可以逐步執行整個程式。

1. 在大括弧上設定中斷點，以標示方法的開頭 `Main` (按下<kbd>命令</kbd> + <kbd>\\</kbd>) 。

1. 按<kbd>⌘</kbd><kbd>↵</kbd> (<kbd>命令</kbd> + <kbd>輸入</kbd>) 以開始進行調試。

   Visual Studio 在含有中斷點的行上停止。

1. 按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 或選取 [**執行**  >  **逐步**執行] 以一行前進。

   Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   :::image type="content" source="media/debugging-with-visual-studio-mac/step-into-method.png" alt-text="Visual Studio 逐步執行方法":::

   此時，[ **區域變數** ] 視窗 `args` 會顯示陣列是空的，而且 `name` `date` 具有預設值。 此外，Visual Studio 也開啟了空白的終端機。

1. 按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。

   Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 [ **區域變數** ] 視窗 `name` 會顯示 `null` ，而終端機會顯示「您的姓名為何？」字串。

1. 在主控台視窗中輸入字串，然後按 <kbd>enter</kbd>，以回應提示。

1. 按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。

   Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。 [ **區域變數** ] 視窗會顯示呼叫方法所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。 終端機會顯示您在提示字元中輸入的字串。

1. 按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。

   [ **區域變數** ] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。 終端機未變更。

1. 按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>i</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>i</kbd>) 。

   Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 終端機會顯示格式化的字串。

1. 按<kbd>⇧</kbd><kbd>⌘</kbd><kbd>U</kbd> (<kbd>shift</kbd> + <kbd>命令</kbd> + <kbd>U</kbd>) 或選取 [**執行**  >  **跳出**]。

   終端機會顯示一則訊息，並等候您按下按鍵。

1. 按任意鍵以結束程式。

## <a name="use-release-build-configuration"></a>使用發行組建設定

測試應用程式的偵錯工具版本之後，您應該也要編譯並測試發行版本。 發行版本所併入的編譯器優化可能會對應用程式的行為造成負面影響。 例如，針對改善效能而設計的編譯器優化，可能會在多執行緒應用程式中建立競爭條件。

若要建立並測試主控台應用程式的發行版本，請執行下列步驟：

1. 將工具列上的組建設定從 [ **Debug** ] 變更為 [ **發行**]。

   :::image type="content" source="media/debugging-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="醒目提示 [偵錯] 的預設 Visual Studio 工具列":::

1. 按<kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>命令</kbd> + <kbd>輸入</kbd>) ，以在不進行調試的情況下執行。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已使用 Visual Studio 調試工具。 在下一個教學課程中，您將發行應用程式的可部署版本。

> [!div class="nextstepaction"]
> [使用 Visual Studio for Mac 發佈 .NET Core 主控台應用程式](publishing-with-visual-studio-mac.md)
