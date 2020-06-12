---
title: 使用 Visual Studio 來調試 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio 來偵測 .NET Core 主控台應用程式。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 743603cb037406948190c7090ca3527bfc40db18
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702063"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>教學課程：使用 Visual Studio 來對 .NET Core 主控台應用程式進行 Debug

本教學課程介紹 Visual Studio 中提供的調試工具。

## <a name="prerequisites"></a>Prerequisites

- 本教學課程適用于您在[Visual Studio 2019 的建立 .Net Core 主控台應用程式](with-visual-studio.md)中建立的主控台應用程式。

## <a name="use-debug-build-configuration"></a>使用 Debug build configuration

*Debug*和*Release*是 Visual Studio 的內建組建設定。 您可以使用 Debug 組建設定進行偵錯工具，以及發行設定進行最終發行散發。

在 Debug 設定中，程式會使用完整符號的 Debug 資訊進行編譯，而不會進行優化。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。 程式的發行設定沒有符號的 debug 資訊，而且已完全優化。

 根據預設，Visual Studio Code 會使用 Debug 組建設定，因此您不需要在進行偵錯工具之前加以變更。

1. 啟動 Visual Studio。

1. 在 Visual Studio 2019 中，開啟您在[建立 .Net Core 主控台應用程式](with-visual-studio.md)中建立的專案。

   目前的組建組態會顯示在工具列上。 下列工具列影像顯示 Visual Studio 設定為編譯應用程式的 Debug 版本：

   ![已反白顯示 debug 的 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

## <a name="set-a-breakpoint"></a>設定中斷點

「中斷點」** 會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。

1. 在顯示名稱、日期和時間的行上設定*中斷點*，方法是按一下該行上程式碼視窗的左邊界。 左邊界位於行號的左邊。  設定中斷點的另一種方式是將游標放在程式程式碼中，然後從功能表列選擇 [ **Debug**  >  **切換中斷點**]。

   如下圖所示，Visual Studio 會藉由反白顯示中斷點，並在左邊界顯示一個紅色點，來指出其設定的行。

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. 按<kbd>F5</kbd>以在 Debug 模式中執行程式。 另一個開始進行偵錯工具的方式，是從功能表中選擇 [**調試**程式] [  >  **開始調試**]。

1. 當程式提示您輸入名稱時，在主控台視窗中輸入字串，然後按<kbd>enter</kbd>鍵。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [區域變數]**** 視窗會顯示目前正在執行的方法中所定義變數的值。

   ![Visual Studio 中中斷點的螢幕擷取畫面](./media/debugging-with-visual-studio/breakpoint-hit.png)

## <a name="use-the-immediate-window"></a>使用即時運算視窗

[即時運算 **] 視窗可**讓您與正在調試的應用程式互動。 您可以互動方式變更變數的值，以查看它對您的程式有何影響。

1. 如果看**不到 [** 即時運算] 視窗，請選擇 [ **Debug**  >  **Windows**  >  **Immediate**] 加以顯示。

1. `name = "Gracie"`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。

1. `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()`在 [即時**Immediate**運算] 視窗中輸入，然後按<kbd>enter</kbd>鍵。

   [即時**運算] 視窗**會顯示字串變數的值和值的屬性 <xref:System.DateTime> 。 此外，變數的值會在 [**區域變數**] 視窗中更新。

   ![Visual Studio 2019 中的區域變數和即時運算視窗](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. 按<kbd>F5</kbd>繼續執行程式。 另**一個繼續進行**的方式，是  >  從功能表中選擇 [**繼續**流覽]。

   主控台視窗中顯示的值會對應至**您在 [即時運算] 視窗**中所做的變更。

   ![主控台視窗顯示輸入的值](./media/debugging-with-visual-studio/console-window.png)

1. 按任意鍵以結束應用程式，並停止進行偵錯工具。

## <a name="set-a-conditional-breakpoint"></a>設定條件式中斷點

程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以使用稱為*條件式中斷點*的實用調試功能來測試此項。

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在內容功能表中，選取 [**條件**] 以開啟 [**中斷點設定**] 對話方塊。 選取 [**條件**] 方塊（如果尚未選取）。

   ![顯示中斷點設定面板的編輯器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. 針對**條件運算式**，在欄位中輸入下列程式碼，其中會顯示測試是否為5的範例程式碼 `x` 。 如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   每次叫用中斷點時，偵錯工具就會呼叫 `String.IsNullOrEmpty(name)` 方法，而且只有在方法呼叫傳回時，才會在這一行上中斷 `true` 。

   除了條件運算式之外，您還可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行。 另一個選項是指定*篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱等屬性來中斷程式執行。

1. 選取 [**關閉**] 以關閉對話方塊。

1. 按<kbd>F5</kbd>鍵以進行偵錯工具啟動。

1. 當系統提示您輸入名稱時，請在主控台視窗中按下<kbd>enter</kbd>鍵。

1. 由於已滿足您指定的條件（ `name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType> ），因此程式會在到達中斷點且在方法執行之前停止執行 `Console.WriteLine` 。

1. 選取 [**區域變數**] 視窗，其中會顯示目前執行之方法的本機變數值。 在此情況下， `Main` 是目前正在執行的方法。 注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。

1. **在 [即時**運算] 視窗中輸入下列語句，然後按<kbd>enter</kbd>鍵，以確認此值為空字串。 結果為 `true`。

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   問號會引導 [即時運算] 視窗來[評估運算式](/visualstudio/ide/reference/immediate-window#enter-commands)。

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. 按<kbd>F5</kbd>繼續執行程式。

1. 按任意鍵以關閉主控台視窗並停止調試。

1. 按一下程式碼視窗左邊界中的點，以清除中斷點。 清除中斷點的另一種方法是在選取程式程式碼時，選擇 [ **Debug > 切換中斷點**]。

## <a name="step-through-a-program"></a>逐步執行程式

Visual Studio 也可讓您逐行執行程式並監視其執行情況。 一般來說，您會設定中斷點，並在程式碼的一小部分追蹤程式流程。 因為此程式很小，所以您可以逐步執行整個程式。

1. 選擇 [**調試**  >  **逐步執行**]。 另一個一次用來調試一個語句的方式是按<kbd>F11</kbd>。

   Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   C#

   ![Visual Studio 逐步執行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Visual Studio 逐步執行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   此時，[**區域變數**] 視窗 `args` 會顯示陣列是空的，而且 `name` 和 `date` 都有預設值。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 按<kbd>F11</kbd>。 Visual Studio 現在會醒目提示要執行的下一行。 [**區域變數**] 視窗不變，而且主控台視窗會保持空白。

   C#

   ![Visual Studio 逐步執行方法原始檔 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Visual Studio 逐步執行方法原始檔 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. 按<kbd>F11</kbd>。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 [**區域變數**] 視窗 `name` 會顯示為 `null` ，而主控台視窗會顯示「您的名稱是什麼？」字串。

1. 在主控台視窗中輸入字串，然後按<kbd>enter</kbd>，以回應提示。 主控台沒有回應，而且您輸入的字串不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍然會捕捉您的輸入。

1. 按<kbd>F11</kbd>。 Visual Studio 會反白顯示包含 `date` 變數指派的語句（ `currentDate` 在 Visual Basic 中）。 [**區域變數**] 視窗會顯示呼叫方法時所傳回的值 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 。 主控台視窗也會顯示您在提示字元中輸入的字串。

1. 按<kbd>F11</kbd>。 [**區域變數**] 視窗會顯示 `date` 從屬性指派之後的變數值 <xref:System.DateTime.Now?displayProperty=nameWithType> 。 主控台視窗沒有變更。

1. 按<kbd>F11</kbd>。 Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗會顯示已格式化的字串。

1. 選擇 [ **Debug**  >  **跳出**]。另一個停止逐步執行的方法是按<kbd>Shift</kbd> + <kbd>F11</kbd>。

   主控台視窗會顯示訊息並等候您按下按鍵。

1. 按任意鍵以關閉主控台視窗並停止調試。

## <a name="use-release-build-configuration"></a>使用發行組建設定

測試過應用程式的 Debug 版本之後，您也應該編譯和測試發行版本。 發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。 例如，針對改善效能而設計的編譯器優化，可以在多執行緒應用程式中建立競爭條件。

若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯]**** 變更為 [發行]****。

![醒目提示 [偵錯] 的預設 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

當您按下<kbd>F5</kbd>或從 [**建立**] 功能表選擇 [**建立方案**] 時，Visual Studio 會編譯應用程式的發行版本。 您可以像執行 Debug 錯版本一樣進行測試。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已使用 Visual Studio 調試工具。 在下一個教學課程中，您會發佈可部署的應用程式版本。

> [!div class="nextstepaction"]
> [使用 Visual Studio 發行 .NET Core 主控台應用程式](publishing-with-visual-studio.md)
