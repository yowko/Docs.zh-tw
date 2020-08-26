---
title: 使用 Visual Studio 來對 .NET Core 主控台應用程式進行偵錯工具
description: 瞭解如何使用 Visual Studio 來進行 .NET Core 主控台應用程式的偵錯工具。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 0555c6b4185da088333503c1e744da2dd7b4f2e4
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867590"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>教學課程：使用 Visual Studio 對 .NET Core 主控台應用程式進行偵錯工具

本教學課程介紹 Visual Studio 中提供的調試工具。

## <a name="prerequisites"></a>先決條件

- 本教學課程適用于您 [使用 Visual Studio 建立 .Net Core 主控台應用程式](with-visual-studio.md)中所建立的主控台應用程式。

## <a name="use-debug-build-configuration"></a>使用 Debug build configuration

*Debug* 和 *Release* 是 Visual Studio 的內建組建設定。 您可以使用 Debug 組建設定進行偵錯工具，並使用發行設定來進行最終發行散發。

在「偵錯工具」設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。 程式的發行設定沒有符號的 debug 資訊，而且已完全優化。

 根據預設，Visual Studio Code 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前進行變更。

1. 啟動 Visual Studio。

1. 開啟您在 [使用 Visual Studio 建立 .Net Core 主控台應用程式](with-visual-studio.md)中建立的專案。

   目前的組建組態會顯示在工具列上。 下列工具列影像顯示 Visual Studio 設定為編譯應用程式的偵錯工具版本：

   ![醒目提示反白顯示的 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」** 會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。

1. 在顯示名稱、日期和時間的行上設定 *中斷點* ，方法是按一下該行程式碼視窗的左邊界。 左邊界是行號的左邊。  設定中斷點的另一種方式是將游標放在程式程式碼中，然後從功能表列選擇 [ **Debug**  >  **切換中斷點**]。

   如下圖所示，Visual Studio 表示藉由反白顯示中斷點，並在左邊界中顯示紅點，來設定中斷點的行。

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. 按下 <kbd>F5</kbd> 鍵，在「偵測模式」中執行程式。 啟動偵錯工具的另一種方式是從功能表中選擇 [ **Debug**  >  **開始調試**程式]。

1. 當程式提示您輸入名稱時，在主控台視窗中輸入字串，然後按 <kbd>enter</kbd>鍵。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [區域變數]**** 視窗會顯示目前正在執行的方法中所定義變數的值。

   ![Visual Studio 中中斷點的螢幕擷取畫面](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a>使用即時運算視窗

[即時 **運算] 視窗** 可讓您與您要進行偵錯工具的應用程式互動。 您可以互動方式變更變數的值，以查看它對您的程式有何影響。

1. 如果看**不到 [** 即時運算] 視窗，請選擇 [ **Debug**  >  **Windows**  >  **Immediate**] 來顯示。

1. `name = "Gracie"`在 [即時**Immediate**運算] 視窗中輸入，然後按下<kbd>enter</kbd>鍵。

1. `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`在 [即時**Immediate**運算] 視窗中輸入，然後按下<kbd>enter</kbd>鍵。

   [即時 **運算] 視窗** 會顯示字串變數的值和值的屬性 <xref:System.DateTime> 。 此外，[ **區域變數** ] 視窗中的變數值也會更新。

   ![Visual Studio 2019 中的區域變數和立即視窗](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. 按 <kbd>F5</kbd> 繼續執行程式。 另一個繼續的方法是從功能表中選擇 [ **Debug**  >  **continue** ]。

   [主控台] 視窗中顯示的值會對應到您在 [即時 **運算] 視窗** 中所做的變更。

   ![顯示輸入值的主控台視窗](./media/debugging-with-visual-studio/console-window.png)

1. 按任意鍵以結束應用程式，並停止偵錯工具。

## <a name="set-a-conditional-breakpoint"></a>設定條件式中斷點

程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以使用稱為 *條件式中斷點*的實用調試功能來進行測試。

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在內容功能表中，選取 [ **條件** ] 以開啟 [ **中斷點設定** ] 對話方塊。 如果尚未選取 [ **條件** ] 方塊，請選取該方塊。

   ![顯示中斷點設定面板的編輯器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. 在 **條件運算式**的欄位中，輸入下列程式碼，以顯示測試是否為5的範例程式碼 `x` 。 如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在此行上中斷 `true` 。

   您可以指定叫用 *計數*（而不是條件運算式），以在指定的次數執行語句之前中斷程式執行。 另一個選項是指定 *篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱，以這類屬性來中斷程式執行。

1. 選取 [ **關閉** ] 以關閉對話方塊。

1. 按下 <kbd>F5</kbd>來啟動程式並進行偵錯工具。

1. 當系統提示您輸入名稱時，在主控台視窗中按 <kbd>enter</kbd> 鍵。

1. 因為您 (指定的條件 `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>) 已滿足，所以程式執行會在到達中斷點時，以及 `Console.WriteLine` 方法執行之前停止。

1. 選取 [ **區域變數** ] 視窗，此視窗會顯示目前正在執行之方法的本機變數值。 在此案例中， `Main` 是目前執行的方法。 注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。

1. **在 [即時**運算] 視窗中輸入下列語句，然後按<kbd>enter</kbd>，確認值為空字串。 結果為 `true`。

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   問號會指示 [即時運算] 視窗 [評估運算式](/visualstudio/ide/reference/immediate-window#enter-commands)。

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. 按 <kbd>F5</kbd> 繼續執行程式。

1. 按任意鍵以關閉主控台視窗並停止調試。

1. 按一下程式碼視窗左邊界中的點，以清除中斷點。 清除中斷點的另一種方式是在選取程式程式碼時，選擇 **Debug > 切換中斷點** 。

## <a name="step-through-a-program"></a>逐步執行程式

Visual Studio 也可讓您逐行執行程式並監視其執行情況。 一般來說，您會設定中斷點，並遵循程式流程程式碼的一小部分。 因為這個程式很小，所以您可以逐步執行整個程式。

1. 選擇 [**調試**  >  **逐步執行**]。 另一次一次調試一個語句的另一種方式是按 <kbd>F11</kbd>鍵。

   Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   C#

   ![Visual Studio 逐步執行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Visual Studio 逐步執行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   此時，[ **區域變數** ] 視窗 `args` 會顯示陣列是空的，而且 `name` `date` 具有預設值。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 按 <kbd>F11</kbd>鍵。 Visual Studio 現在會醒目提示要執行的下一行。 [ **區域變數** ] 視窗會保持不變，而且主控台視窗會維持空白。

   C#

   ![Visual Studio 逐步執行方法原始檔 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Visual Studio 逐步執行方法原始檔 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. 按 <kbd>F11</kbd>鍵。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 [ **區域變數** ] 視窗 `name` 會顯示 `null` ，而主控台視窗則會顯示「您的名稱為何？」字串。

1. 在主控台視窗中輸入字串，然後按 <kbd>enter</kbd>，以回應提示。 主控台沒有回應，而且您輸入的字串不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍會捕捉您的輸入。

1. 按 <kbd>F11</kbd>鍵。 Visual Studio 反白顯示 `date` Visual Basic) 中包含變數指派 (的語句 `currentDate` 。 [ **區域變數** ] 視窗會顯示呼叫方法所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。 主控台視窗也會顯示您在提示字元中輸入的字串。

1. 按 <kbd>F11</kbd>鍵。 [ **區域變數** ] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。 主控台視窗沒有變更。

1. 按 <kbd>F11</kbd>鍵。 Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗會顯示已格式化的字串。

1. 選擇 [ **Debug**  >  **跳出**]。停止逐步執行的另一個方法是按<kbd>Shift</kbd> + <kbd>F11</kbd>。

   主控台視窗會顯示訊息並等候您按下按鍵。

1. 按任意鍵以關閉主控台視窗並停止調試。

## <a name="use-release-build-configuration"></a>使用發行組建設定

測試應用程式的偵錯工具版本之後，您應該也要編譯並測試發行版本。 發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。 例如，針對改善效能而設計的編譯器優化，可能會在多執行緒應用程式中建立競爭條件。

若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯]**** 變更為 [發行]****。

![醒目提示 [偵錯] 的預設 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

當您按下<kbd>F5</kbd> ，或從 [**組建**] 功能表選擇 [**組建方案**] 時，Visual Studio 會編譯應用程式的發行版本。 您可以進行測試，就像是執行調試版本一樣。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已使用 Visual Studio 調試工具。 在下一個教學課程中，您將發行應用程式的可部署版本。

> [!div class="nextstepaction"]
> [使用 Visual Studio 發佈 .NET Core 主控台應用程式](publishing-with-visual-studio.md)
