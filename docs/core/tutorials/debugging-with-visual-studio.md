---
title: 調試您的Hello世界.NET核心應用程式與視覺化工作室
description: 瞭解如何調試使用 Visual Studio 編寫的"Hello World"應用或視覺化基本版。
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156669"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>使用視覺化工作室調試您的 C# 或視覺化基本 .NET 核心 Hello World 應用程式

到目前為止，您已經按照在[Visual Studio 2019 中創建第一個 .NET 酷睿主控台應用程式](with-visual-studio.md)的步驟來創建和運行簡單的主控台應用程式。 在您撰寫並編譯應用程式之後，便可以開始測試它。 Visual Studio 包含一套全面的調試工具，可用於對應用程式進行故障排除。

## <a name="debug-build-configuration"></a>調試組建組態

[偵錯]** 和 [發行]** 是 Visual Studio 其中兩個預設的組建組態。 目前的組建組態會顯示在工具列上。 以下工具列圖像顯示 Visual Studio 配置為編譯應用程式的調試版本：

![具有調試突出顯示的視覺化工作室工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

首先運行應用的調試版本。 調試組建組態將關閉大多數編譯器優化，並在生成過程中提供更豐富的資訊。

## <a name="set-a-breakpoint"></a>設定中斷點

運行程式並嘗試一些調試功能：

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. 通過按一下該行上代碼視窗的左邊`Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");`距，在行上設置*讀取的中斷點*。 還可以設置中斷點，將撥圖放在程式碼中，然後按**F9**或從功能表列中選擇 **"調試** > **切換中斷點**"。

   「中斷點」會在含有中斷點的行執行「之前」**，暫時中斷應用程式的執行。

   如下圖所示，Visual Studio 通過突出顯示中斷點並在其左邊距顯示一個紅色圓圈來指示設置中斷點的行。

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. 在偵錯模式下運行程式，選擇工具列上帶有綠色箭頭的**HelloWorld**按鈕，按**F5**，或選擇**調試** > **啟動調試**。

1. 當程式提示名稱時，在主控台視窗中輸入字串，**然後按**Enter 。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [區域變數]**** 視窗會顯示目前正在執行的方法中所定義變數的值。

   ![視覺工作室中斷點截圖](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. **通過"立即"** 視窗，您可以與正在調試的應用程式進行交互。 您可以以對話模式更改變數的值，以查看它如何影響程式。

   1. 如果 **"立即"** 視窗不可見，則通過選擇 **"立即調試** > **Windows"** > **Immediate**來顯示它。

   1. 輸入`name = "Gracie"`**"立即"** 視窗並按**Enter**鍵。

   1. 輸入`date = DateTime.Parse("11/16/2019 5:25 PM")`**"立即"** 視窗並按**Enter**鍵。

   **"立即"** 視窗顯示字串變數的值和值的屬性<xref:System.DateTime>。 此外，變數的值在 **"區域變數"** 視窗中更新。

   ![2019 年視覺化工作室中的本地和即時視窗](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. 通過在工具列中選擇 **"繼續"** 按鈕或選擇 **"調試** > **繼續"** 來繼續程式執行。 主控台視窗中顯示的值與您在 **"立即"** 視窗中所做的更改相對應。

   ![顯示輸入值的主控台視窗](./media/debugging-with-visual-studio/console-window.png)

1. 按任意鍵退出應用程式並停止調試。

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. 通過按一下該行上代碼視窗的左邊`Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")`距，在行上設置*讀取的中斷點*。 還可以設置中斷點，將 care 放在所需的線路上，然後從功能表列中選擇 **"調試** > **切換中斷點**"。

   「中斷點」會在含有中斷點的行執行「之前」**，暫時中斷應用程式的執行。

   如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. 在偵錯模式下運行程式，選擇工具列上帶有綠色箭頭的**HelloWorld**按鈕，按**F5**，或選擇**調試** > **啟動調試**。

1. 當程式提示名稱並按 Enter 時，在主控台視窗中**輸入**字串。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [區域變數]**** 視窗會顯示目前正在執行的方法中所定義變數的值。

1. **通過"立即"** 視窗，您可以與正在調試的應用程式進行交互。 您可以以對話模式更改變數的值，以查看它如何影響程式。

   1. 如果 **"立即"** 視窗不可見，則通過選擇 **"立即調試** > **Windows"** > **Immediate**來顯示它。

   1. 輸入`name = "Gracie"`**"立即"** 視窗並按**Enter**鍵。

   1. 輸入`date = DateTime.Parse("11/16/2019 5:25 PM")`**"立即"** 視窗並按**Enter**鍵。

   變數的值在 **"區域變數"** 視窗中更新。

1. 選取工具列中的 [繼續]**** 按鈕，或選取 [偵錯]**** >  [繼續]**** 功能表項目，以繼續程式執行。 主控台視窗中顯示的值與您在 **"立即"** 視窗中所做的更改相對應。

   ![顯示輸入值的主控台視窗](./media/debugging-with-visual-studio/console-window.png)

1. 按任意鍵退出應用程式並停止調試。

---

## <a name="set-a-conditional-breakpoint"></a>設置條件中斷點

您的程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以使用稱為*條件中斷點*的有用調試功能來測試，當滿足一個或多個條件時，該功能將中斷程式執行。

若要設定條件中斷點並測試使用無法輸入字串時會發生的情況，請執行下列操作：

# <a name="c"></a>[C#](#tab/csharp)

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在內容功能表上，選取 [條件]**** 以開啟 [中斷點設定]**** 對話方塊。 如果尚未選中條件，請選中 **"條件**"核取方塊。

   ![顯示中斷點設定面板的編輯器 - C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. 對於**條件運算式**，將"例如 x = = 5"替換為以下內容：

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   您正在測試一個代碼條件，`String.IsNullOrEmpty(name)`方法調用是因為`true``name`尚未分配值，或者因為它的值是空字串 （""）。 也可以指定*命中計數*，該計數在語句執行指定次數之前中斷程式執行，也可以指定*篩選器條件*，該條件基於執行緒識別碼、進程名稱或執行緒名稱等屬性中斷程式執行。

1. 選擇 **"關閉"** 以關閉對話方塊。

1. 通過按**F5**啟動程式以調試。

1. 在主控台視窗中，在提示輸入您的姓名時按**Enter**鍵。

1. 由於您指定的`name`條件或`null`<xref:System.String.Empty?displayProperty=nameWithType>已滿足，因此程式執行在到達中斷點時和`Console.WriteLine`方法執行之前停止。

1. 選擇 **"區域變數"** 視窗，該視窗顯示當前執行方法的區域變數的值。 在這種情況下，`Main`是當前執行的方法。 注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。

1. 通過在 **"立即"** 視窗中輸入以下語句並按**Enter**， 確認該值是空字串。 結果為 `true`。

   ```csharp
   ? name == String.Empty
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. 選取工具列上的 [繼續]**** 按鈕以繼續程式執行。

1. 按任意鍵關閉主控台視窗並停止調試。

1. 按一下代碼視窗左邊距中的點，或在選擇程式碼時選擇 **"調試>切換中斷點**"來清除中斷點。

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在內容功能表上，選取 [條件]**** 以開啟 [中斷點設定]**** 對話方塊。 核取 [條件]**** 的方塊。

   ![顯示中斷點設定面板的編輯器 - Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. 對於**條件運算式**，請將"例如 x = 5"替換為以下內容：

   ```vb
   String.IsNullOrEmpty(name)
   ```

   您正在測試一個代碼條件，`String.IsNullOrEmpty(name)`方法調用是因為`true``name`尚未分配值，或者因為它的值是空字串 （""）。 也可以指定*命中計數*，該計數在語句執行指定次數之前中斷程式執行，也可以指定*篩選器條件*，該條件基於執行緒識別碼、進程名稱或執行緒名稱等屬性中斷程式執行。

1. 選擇 **"關閉"** 以關閉對話方塊。

1. 通過按**F5**啟動程式以調試。

1. 在主控台視窗中，在提示輸入您的姓名時按**Enter**鍵。

1. 由於您指定的`name`條件或`null`<xref:System.String.Empty?displayProperty=nameWithType>已滿足，因此程式執行在到達中斷點時和`Console.WriteLine`方法執行之前停止。

1. 選擇 **"區域變數"** 視窗，該視窗顯示當前執行方法的區域變數的值。 在這種情況下，`Main`是當前執行的方法。 注意到 `name` 變數的值會是 `""` 或 <xref:System.String.Empty?displayProperty=nameWithType>。

1. 通過在 **"立即"** 視窗中輸入以下語句並按**Enter**， 確認該值是空字串。 結果為 `true`。

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. 選取工具列上的 [繼續]**** 按鈕以繼續程式執行。

1. 按任意鍵關閉主控台視窗並停止調試。

1. 按一下程式碼視窗左邊界中的點，或在已選取資料列的情況下選擇 [偵錯] > [切換中斷點]**** 功能表項目，以清除中斷點。

---
## <a name="step-through-a-program"></a>單一步驟程式

Visual Studio 也可讓您逐行執行程式並監視其執行情況。 通常，您會設定中斷點，然後使用此功能來依循程式流程執行您程式碼的一小部分。 由於程式很小，您可以單一步驟整個程式：

# <a name="c"></a>[C#](#tab/csharp)

1. 在功能表列上，選擇 **"調試** > **步驟進入"** 或按**F11**。 Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   ![Visual Studio 逐步執行方法 - C#](./media/debugging-with-visual-studio/step-into-method.png)

   此時，"**區域變數"** 視窗顯示程式只定義了一個變數`args`。 由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 現在會醒目提示要執行的下一行。 如圖所示，執行最後一個語句和此語句之間的代碼不到一毫秒。 `args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。

   ![Visual Studio 逐步執行方法原始檔 - C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 **"區域變數"** 視窗`name`顯示`null`的是 ，主控台視窗顯示字串"您的姓名是什麼？

1. 通過在主控台視窗中輸入字串並按**Enter**回應提示。 主控台無回應，您輸入的字串不顯示在主控台視窗中，但<xref:System.Console.ReadLine%2A?displayProperty=nameWithType>該方法仍將捕獲您的輸入。

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。 **"區域變數"** 視窗顯示對<xref:System.Console.ReadLine%2A?displayProperty=nameWithType>方法的調用返回的值。 主控台視窗還顯示您在提示符下輸入的字串。

1. 選擇 **"調試** > **步驟"或**按**F11**。 **"區域變數"** 視窗顯示從`date`<xref:System.DateTime.Now?displayProperty=nameWithType>屬性分配後變數的值。 主控台視窗沒有變更。

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗顯示格式化的字串。

1. 選擇**調試** > **步進或**按**Shift**+**F11**。 這會停止逐步執行。 主控台視窗會顯示訊息並等候您按下按鍵。

1. 按任意鍵關閉主控台視窗並停止調試。

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. 在功能表列上，選擇 **"調試** > **步驟進入"** 或按**F11**。 Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   ![Visual Studio 逐步執行方法 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   此時，"**區域變數"** 視窗顯示程式只定義了一個變數`args`。 由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 現在會醒目提示要執行的下一行。 如圖所示，執行上一個陳述式與這個陳述式之間的程式碼所花費的時間少於一毫秒。 `args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。

   ![Visual Studio 逐步執行方法原始檔 - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 **"區域變數"** 視窗`name`顯示`Nothing`的是 ，主控台視窗顯示字串"您的姓名是什麼？

1. 通過在主控台視窗中輸入字串並按**Enter**回應提示。 主控台不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> 方法仍然會擷取您的輸入。

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 會醒目提示包含 `currentDate` 變數指派的陳述式。 **"區域變數"** 視窗顯示對<xref:System.Console.ReadLine%2A?displayProperty=nameWithType>方法的調用返回的值。 主控台視窗也會顯示在主控台提示輸入時輸入的字串。

1. 選擇 **"調試** > **步驟"或**按**F11**。 主控台視窗沒有變更。

1. 選擇 **"調試** > **步驟"或**按**F11**。 Visual Studio 會呼叫 <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> 方法。 主控台視窗顯示格式化的字串。

1. 選擇**調試** > **步進或**按**Shift**+**F11**。 這會停止逐步執行。 主控台視窗會顯示訊息並等候您按下按鍵。

1. 按任意鍵關閉主控台視窗並停止調試。

---

## <a name="build-a-release-version"></a>構建發佈版本

測試應用程式的調試版本後，還應編譯和測試發佈版本。 發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。 例如，旨在提高性能的編譯器優化可以在多執行緒應用程式中創建競爭條件。

若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯]**** 變更為 [發行]****。

![醒目提示 [偵錯] 的預設 Visual Studio 工具列](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

當您按**F5**或從 **"生成"** 功能表中選擇 **"生成解決方案**"時，Visual Studio 會編譯應用程式的發佈版本。 您可以像測試版本一樣對其進行測試。

## <a name="next-steps"></a>後續步驟

調試應用程式後，下一步是發佈應用程式的可部署版本。 有關如何執行此操作的資訊，請參閱使用 Visual [Studio 發佈您的 .NET 核心 Hello World 應用程式](publishing-with-visual-studio.md)。
