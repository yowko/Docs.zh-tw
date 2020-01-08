---
title: 使用 Visual Studio 來進行 Hello World .NET Core 應用程式的 Debug
description: 瞭解如何在 Visual Studio 中C# ，對以或 Visual Basic 撰寫的 Hello World 應用程式進行 debug。
ms.date: 12/05/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 016b677639543c749a9940856f01b86e9a70859c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340102"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>使用 Visual Studio C#來 Debug 或 Visual Basic .net Core Hello World 應用程式

到目前為止，您已遵循在[Visual Studio 2019 中建立您的第一個 .Net Core 主控台應用程式](with-visual-studio.md)中的步驟，來建立和執行簡單的主控台應用程式。 在您撰寫並編譯應用程式之後，便可以開始測試它。 Visual Studio 包含一組完整的偵錯工具，可讓您用來針對應用程式進行疑難排解。

## <a name="debug-build-configuration"></a>Debug 組建設定

[偵錯] 和 [發行] 是 Visual Studio 其中兩個預設的組建組態。 目前的組建組態會顯示在工具列上。 下列工具列影像顯示 Visual Studio 設定為編譯應用程式的 Debug 版本：

![已反白顯示 debug 的 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

從執行應用程式的 Debug 版本開始。 「偵錯工具」組建設定會關閉大部分的編譯器優化，並在建立程式期間提供更豐富的資訊。

## <a name="set-a-breakpoint"></a>設定中斷點

執行您的程式並嘗試幾個偵錯工具功能：

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 在程式碼視窗的左邊界按一下該行，在讀取 `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` 的那一行上設定*中斷點*。 您也可以設定中斷點，方法是將插入號放在程式程式碼中，然後按**F9** ，或從功能表列選擇 [ **Debug** ] > [**切換中斷點**]。

   中斷點會在執行中斷點的行*之前*，暫時中斷應用程式的執行。

   如下圖所示，Visual Studio 會藉由反白顯示中斷點，並在左邊界顯示紅色圓圈，來指出其所在的行。

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. 在 [Debug] 模式中執行程式，方法是選取工具列上具有綠色箭號的 [ **HelloWorld** ] 按鈕，按**F5**，或選擇 [ **Debug** ] > **開始進行調試**。

1. 當程式提示您輸入名稱時，在主控台視窗中輸入字串，然後按**enter**鍵。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [區域變數] 視窗會顯示目前正在執行的方法中所定義變數的值。

   ![Visual Studio 中中斷點的螢幕擷取畫面](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. [即時運算 **] 視窗可**讓您與正在調試的應用程式互動。 您可以互動方式變更變數的值，以查看它對您的程式有何影響。

   1. 如果看**不到 [** 即時運算] 視窗，請選擇 [ **Debug** > **Windows** > **Immediate**] 加以顯示。

   1. **在 [即時**運算] 視窗中輸入 `name = "Gracie"`，然後按**enter**鍵。

   1. **在 [即時**運算] 視窗中輸入 `date = DateTime.Parse("11/16/2019 5:25 PM")`，然後按**enter**鍵。

   [即時**運算] 視窗**會顯示字串變數的值和 <xref:System.DateTime> 值的屬性。 此外，變數的值會在 [**區域變數**] 視窗中更新。

   ![Visual Studio 2019 中的區域變數和即時運算視窗](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. 選取工具列中的 [**繼續**] 按鈕，或選取 [ **Debug** **] > [繼續]** ，以繼續執行程式。 主控台視窗中顯示的值會對應至**您在 [即時運算] 視窗**中所做的變更。

   ![主控台視窗顯示輸入的值](./media/debugging-with-visual-studio/console-window.png)

1. 按任意鍵以結束應用程式，並停止進行偵錯工具。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 在程式碼視窗的左邊界按一下該行，在讀取 `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` 的那一行上設定*中斷點*。 您也可以設定中斷點，方法是將插入號放在想要的行上，然後從功能表列選擇 [ **Debug** ] > [**切換中斷點**]。

   中斷點會在執行中斷點的行*之前*，暫時中斷應用程式的執行。
   
   如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. 在 [Debug] 模式中執行程式，方法是選取工具列上具有綠色箭號的 [ **HelloWorld** ] 按鈕，按**F5**，或選擇 [ **Debug** ] > **開始進行調試**。

1. 當程式提示您輸入名稱，然後按**enter**鍵時，請在主控台視窗中輸入字串。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [區域變數] 視窗會顯示目前正在執行的方法中所定義變數的值。

1. [即時運算 **] 視窗可**讓您與正在調試的應用程式互動。 您可以互動方式變更變數的值，以查看它對您的程式有何影響。

   1. 如果看**不到 [** 即時運算] 視窗，請選擇 [ **Debug** > **Windows** > **Immediate**] 加以顯示。

   1. **在 [即時**運算] 視窗中輸入 `name = "Gracie"`，然後按**enter**鍵。

   1. **在 [即時**運算] 視窗中輸入 `date = DateTime.Parse("11/16/2019 5:25 PM")`，然後按**enter**鍵。

   變數的值會在 [**區域變數**] 視窗中更新。

1. 選取工具列中的 [繼續] 按鈕，或選取 [偵錯] >  [繼續] 功能表項目，以繼續程式執行。 主控台視窗中顯示的值會對應至**您在 [即時運算] 視窗**中所做的變更。

   ![主控台視窗顯示輸入的值](./media/debugging-with-visual-studio/console-window.png)

1. 按任意鍵以結束應用程式，並停止進行偵錯工具。

---

## <a name="set-a-conditional-breakpoint"></a>設定條件式中斷點

您的程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以使用稱為「*條件式中斷點*」的實用偵錯工具來測試此功能，以在符合一或多個條件時中斷程式執行。

若要設定條件中斷點並測試使用無法輸入字串時會發生的情況，請執行下列操作：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在內容功能表上，選取 [條件] 以開啟 [中斷點設定] 對話方塊。 勾選 [**條件**] 方塊（如果尚未選取）。

   ![顯示中斷點設定面板的編輯器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. 針對**條件運算式**，將 "（例如 x = = 5"）取代為下列內容：

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   您正在測試程式碼條件，`String.IsNullOrEmpty(name)` 方法呼叫 `true` 的原因可能是 `name` 尚未指派值，或其值為空字串（""）。 除了條件運算式之外，您也可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行; 或*篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱等屬性來中斷程式執行。

1. 選取 [**關閉**] 以關閉對話方塊。

1. 按**F5**鍵以進行偵錯工具啟動。

1. 當系統提示您輸入名稱時，請在主控台視窗中按下**enter**鍵。

1. 因為已滿足您指定的條件，`name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>，所以程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前停止執行。

1. 選取 [**區域變數**] 視窗，其中會顯示目前執行之方法的本機變數值。 在此情況下，`Main` 是目前正在執行的方法。 注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。

1. **在 [即時**運算] 視窗中輸入下列語句，然後按**enter**鍵，以確認此值為空字串。 結果為 `true`。

   ```csharp
   ? name == String.Empty
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. 選取工具列上的 [繼續] 按鈕以繼續程式執行。

1. 按任意鍵以關閉主控台視窗並停止調試。

1. 按一下程式碼視窗左邊界中的點，或在選取程式程式碼時選擇 [ **Debug] > [切換中斷點**]，以清除中斷點。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在內容功能表上，選取 [條件] 以開啟 [中斷點設定] 對話方塊。 核取 [條件] 的方塊。

   ![顯示中斷點設定面板的編輯器 - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. 對於 [條件運算式]，請以下列內容取代 "e.g. x == 5"：

   ```vb
   String.IsNullOrEmpty(name)
   ```

   您正在測試程式碼條件，`String.IsNullOrEmpty(name)` 方法呼叫 `true` 的原因可能是 `name` 尚未指派值，或其值為空字串（""）。 除了條件運算式之外，您也可以指定叫用*計數*，這會在語句執行指定的次數之前中斷程式執行; 或*篩選準則*，以根據執行緒識別碼、進程名稱或執行緒名稱等屬性來中斷程式執行。

1. 選取 [**關閉**] 以關閉對話方塊。

1. 按**F5**鍵以進行偵錯工具啟動。

1. 當系統提示您輸入名稱時，請在主控台視窗中按下**enter**鍵。

1. 因為已滿足您指定的條件，`name` 是 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType>，所以程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前停止執行。

1. 選取 [**區域變數**] 視窗，其中會顯示目前執行之方法的本機變數值。 在此情況下，`Main` 是目前正在執行的方法。 注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。

1. **在 [即時**運算] 視窗中輸入下列語句，然後按**enter**鍵，以確認此值為空字串。 結果為 `true`。

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. 選取工具列上的 [繼續] 按鈕以繼續程式執行。

1. 按任意鍵以關閉主控台視窗並停止調試。

1. 按一下程式碼視窗左邊界中的點，或在已選取資料列的情況下選擇 [偵錯] > [切換中斷點] 功能表項目，以清除中斷點。

---
## <a name="step-through-a-program"></a>逐步執行程式

Visual Studio 也可讓您逐行執行程式並監視其執行情況。 通常，您會設定中斷點，然後使用此功能來依循程式流程執行您程式碼的一小部分。 因為您的程式很小，您可以逐步執行整個程式：

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 在功能表列上，選擇 [ **Debug** ] > [**逐步**執行]，或按**F11**。 Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   ![Visual Studio 逐步執行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   此時，[**區域變數**] 視窗會顯示您的程式已只定義一個變數，`args`。 由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 現在會醒目提示要執行的下一行。 如圖所示，在最後一個語句與這個語句之間執行程式碼所花費的時間不到一毫秒。 `args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。

   ![Visual Studio 逐步執行方法原始檔 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 [**區域變數**] 視窗會顯示 `null`的 `name`，而主控台視窗會顯示「您的名稱是什麼？」字串。

1. 在主控台視窗中輸入字串，然後按**enter**，以回應提示。 主控台沒有回應，而且您輸入的字串不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍會捕捉您的輸入。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。 [**區域變數**] 視窗會顯示呼叫 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法時所傳回的值。 主控台視窗也會顯示您在提示字元中輸入的字串。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 [**區域變數**] 視窗會顯示從 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性指派之後，`date` 變數的值。 主控台視窗沒有變更。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗會顯示已格式化的字串。

1. 選取 [ **Debug** > **跳出**] 或按**Shift**+**F11**。 這會停止逐步執行。 主控台視窗會顯示訊息並等候您按下按鍵。

1. 按任意鍵以關閉主控台視窗並停止調試。

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 在功能表列上，選擇 [ **Debug** ] > [**逐步**執行]，或按**F11**。 Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   ![Visual Studio 逐步執行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   此時，[**區域變數**] 視窗會顯示您的程式已只定義一個變數，`args`。 由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 現在會醒目提示要執行的下一行。 如圖所示，執行上一個陳述式與這個陳述式之間的程式碼所花費的時間少於一毫秒。 `args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。

   ![Visual Studio 逐步執行方法原始檔 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 [**區域變數**] 視窗會顯示 `Nothing`的 `name`，而主控台視窗會顯示「您的名稱是什麼？」字串。

1. 在主控台視窗中輸入字串，然後按**enter**，以回應提示。 主控台不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍然會擷取您的輸入。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 會醒目提示包含 `currentDate` 變數指派的陳述式。 [**區域變數**] 視窗會顯示呼叫 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法時所傳回的值。 主控台視窗也會顯示在主控台提示輸入時輸入的字串。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 主控台視窗沒有變更。

1. 選取 [ **Debug** > **逐步**執行] 或按**F11**。 Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗會顯示已格式化的字串。

1. 選取 [ **Debug** > **跳出**] 或按**Shift**+**F11**。 這會停止逐步執行。 主控台視窗會顯示訊息並等候您按下按鍵。

1. 按任意鍵以關閉主控台視窗並停止調試。

---

## <a name="build-a-release-version"></a>建立發行版本

測試過應用程式的 Debug 版本之後，您也應該編譯和測試發行版本。 發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。 例如，針對改善效能而設計的編譯器優化，可以在多執行緒應用程式中建立競爭條件。

若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯] 變更為 [發行]。

![醒目提示 [偵錯] 的預設 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

當您按下**F5**或從 [**建立**] 功能表選擇 [**建立方案**] 時，Visual Studio 會編譯應用程式的發行版本。 您可以像執行 Debug 錯版本一樣進行測試。

## <a name="next-steps"></a>後續步驟

在您完成應用程式的調試之後，下一步就是發佈可部署的應用程式版本。 如需如何執行此動作的詳細資訊，請參閱[使用 Visual Studio 發佈您的 .Net Core Hello World 應用程式](publishing-with-visual-studio.md)。
