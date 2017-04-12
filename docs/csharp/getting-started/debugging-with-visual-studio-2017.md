---
title: "使用 Visual Studio 2017 針對您的 C# Hello World 應用程式進行偵錯"
description: "了解如何使用 Visual Studio 2017 對以 C# 撰寫的 Hello World 應用程式進行偵錯"
keywords: ".NET Core, .NET Core 主控台應用程式, .NET Core 偵錯"
author: BillWagner
ms.author: wiwagn
ms.date: 10/24/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6a6a461984c140d180cf70cd7a1a33818a40b451
ms.lasthandoff: 03/13/2017

---

# <a name="debugging-your-c-hello-world-application-with-visual-studio-2017"></a>使用 Visual Studio 2017 針對您的 C# Hello World 應用程式進行偵錯 #

到目前為止，您已依照[在 Visual Studio 2017 中使用 .NET Core 來建置 C# Hello World 應用程式 (英文)](.\with-visual-studio-2017.md) 中的步驟來建立和執行簡單的主控台應用程式。 在您撰寫並編譯應用程式之後，您便可以開始測試它。 Visual Studio 包含一組完整的偵錯工具，可供您在針對應用程式進行測試和疑難排解時使用。 讓我們在進行應用程式偵錯時看看其中幾項工具。

## <a name="debugging-in-debug-mode"></a>在偵錯模式下進行偵錯 ##

[偵錯] 模式是 Visual Studio 的兩個預設組建組態其中之一。 (另一個是 [發行] 模式)。目前的組建組態會顯示在工具列上。 下圖顯示我們的應用程式將在 [偵錯] 模式下進行編譯。

   ![Image](./media/debugmode.jpg)

您應該一律從在 [偵錯] 模式下進行程式測試開始。 [偵錯] 模式會關閉大多數的編譯器最佳化，並可在組建程序所輸出的符號資料庫檔案 (.pdb 檔案) 中提供更豐富的資訊。

## <a name="setting-a-breakpoint"></a>設定中斷點 ##

讓我們在 [偵錯] 模式下執行程式並嘗試幾個偵錯功能：

1. 將游標放在顯示 `Console.WriteLine("\nHello, {0}, on {1:d} at {1:t}", name, date);` 的這一行並在程式碼視窗左邊界中按一下，或選擇 [偵錯]**** > [切換中斷點]**** 功能表項目，以設定中斷點。 (中斷點會在含有中斷點的行執行「之前」**，暫時中斷應用程式的執行)。如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。

   ![Image](./media/setbreakpoint_2017.jpg)

1. 在 [偵錯] 模式下執行程式，方法是選取工具列上帶有綠色箭號的 [HelloWorld] 按鈕、按 F5，或選擇 [偵錯]**** > [開始偵錯]****。

1. 當程式提示輸入名稱時，在主控台視窗中輸入字串，然後按 Enter。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 Visual Studio 應該會看起來類似下圖。 請注意，[自動變數]**** 視窗會顯示目前行附近所使用變數的值。 ([區域變數]**** 視窗會顯示目前正在執行的方法中所定義變數的值。)

   ![Image](./media/breakpoint_2017.jpg)

1. 讓我們來嘗試變更變數的值，以了解這會如何影響我們的程式。 如果看不到 [即時運算視窗]****，請選擇 [偵錯]**** > [視窗]**** > [即時運算]**** 功能表項目。 [即時運算視窗]**** 可讓您與正在進行偵錯的應用程式進行互動。

1. 您可以藉由互動方式變更變數的值。 在即時運算視窗中輸入 `name = "Yuma"`，然後按 Enter 鍵。

1. 在即時運算視窗中輸入 `date = new DateTime(2016,11,01,11,59,00)`，然後按 Enter 鍵。

   下圖顯示 [即時運算視窗]****：

   ![Image](./media/immediatewindow.jpg)

   請注意，此視窗會顯示字串變數的值和 @System.DateTime 值的屬性。 此外，[自動變數]**** 和 [區域變數]**** 視窗中變數的值也會更新。

1. 選取工具列中的 [繼續]**** 按鈕，或選擇 [偵錯]**** > [繼續]**** 功能表項目，以繼續程式執行。 產生的主控台視窗應該會類似下圖。 請注意，主控台視窗中顯示的值也會與我們在 [即時運算視窗]**** 中所做的變更對應。

   ![Image](./media/changed.jpg)

1. 按任意鍵以結束應用程式並結束 [偵錯] 模式。

## <a name="setting-a-conditional-breakpoint"></a>設定條件中斷點 ##

我們現在已知道程式將會正確顯示使用者所輸入的字串。 但如果使用者未進行任何輸入時，會發生什麼情況？ 我們可以進行這項測試，然後在過程中使用另一項偵錯功能，亦即設定條件中斷點的功能。

若要設定條件中斷點並測試使用無法輸入字串時會發生的情況，請執行下列操作：

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在操作功能表上，選取 [條件]**** 以開啟 [中斷點設定]**** 對話方塊，如下圖所示。

   ![Image](./media/breakpoint_settings.jpg)

1. 在顯示 "e.g. x == 5" 的文字方塊中，輸入下列內容：

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   在這裡，我們將針對程式碼條件進行測試。 我們也可以指定一個叫用次數，以在陳述式執行次數達到指定的次數之前中斷程式執行；或是指定一個篩選條件，以根據執行緒識別碼、處理序名稱及執行緒名稱等屬性中斷應用程式執行。

1. 選擇 [關閉]**** 按鈕以關閉應用程式。

1. 在 [偵錯] 模式下執行程式。

1. 在主控台視窗中，於提示您輸入名稱時，按 Enter 鍵。

1. 由於已經滿足我們指定的條件 (`name` 是 `null` 或 [String.Empty](xref:System.String.Empty))，因此程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。

1. 選擇 [區域變數]**** 視窗，此視窗會顯示目前正在執行之方法 (在此案例中為 `Main` 方法) 的區域變數值。

1. 請注意，`name` 變數的值會是 "" 或 [String.Empty](xref:System.String.Empty)。 請在 [即時運算視窗]**** 中輸入下列陳述式來確認此值：

   ```csharp
   ? name == String.Empty
   ```

   其結果如下圖所示。

   ![Image](./media/emptystring.jpg)

1. 選擇工具列上的 [繼續]**** 按鈕以繼續程式執行。

1. 按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。

1. 按一下程式碼視窗左邊界中的點，或選擇 [偵錯]**** > [切換中斷點]**** 功能表項目，以清除中斷點。

## <a name="stepping-through-a-program"></a>逐步執行程式 ##

Visual Studio 也可讓我們逐行執行程式並監視其執行情況。 通常，您會設定中斷點，然後使用此功能來依循程式流程執行您程式碼的一小部分。 由於我們的程式相當小，因此讓我們透過執行下列操作將整個程式執行一遍：

1. 在功能表列上，選擇 [偵錯]**** > [逐步執行]****，或按 F11 鍵。 Visual Studio 會醒目提示下一個要執行的行並在其旁邊顯示一個箭號，如下圖所示。

   ![Image](./media/step_into.jpg)

   此時，[自動變數]**** 視窗會顯示我們的程式只有定義一個變數 `args`。 由於我們尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 選擇 [偵錯]**** > [逐步執行]****，或按 F11 鍵。 Visual Studio 現在會醒目提示下一個要執行的行。 如圖所示，執行上一個陳述式與這個陳述式之間的程式碼花費了 3 毫秒。 `args` 仍是唯一的已宣告變數，而主控台視窗仍然空白。

   ![Image](./media/step_into_2.jpg)

1. 選擇 [偵錯]**** > [逐步執行]****，或按 F11 鍵。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 [自動變數]**** 視窗會顯示 `name` 是 `null`，而主控台視窗則會顯示 "What is your name?" 字串。

1. 在主控台視窗中輸入一個字串並按 Enter，以回應提示。 主控台將不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 [Console.ReadLine](xref:System.Console.ReadLine) 方法仍然會擷取您的輸入。

1. 選擇 [偵錯]**** > [逐步執行]****，或按 F11 鍵。 Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。 [自動變數]**** 視窗會顯示 [DateTime.Now](xref:System.DateTime.Now) 屬性值，以及對 [Console.ReadLine](xref:System.Console.ReadLine) 方法進行呼叫所傳回的值。 主控台視窗也會顯示在主控台提示輸入時輸入的字串。

1. 選擇 [偵錯]**** > [逐步執行]****，或按 F11 鍵。 [自動變數]**** 視窗現在會顯示從 [DateTime.Now](xref:System.DateTime.Now) 屬性指派之後的 `date` 變數值。 主控台視窗沒有變更。

1. 選擇 [偵錯]**** > [逐步執行]****，或按 F11 鍵。 Visual Studio 會呼叫 [Console.WriteLine](xref:System.Console.WriteLine(System.String,System.Object,System.Object)) 方法。 `date` 和 `name` 變數的值會顯示在 [自動變數]**** 視窗中，而主控台視窗則會顯示已格式化的字串。

1. 選擇 [偵錯]**** > [跳離函式]****，或按 Shift 和 F11 鍵。 這會停止逐步執行。 主控台視窗會顯示訊息並等候我們按下按鍵。

1. 按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。

## <a name="building-a-release-version"></a>建置發行版本 ##

在對應用程式組建進行測試和偵錯之後，您還應該編譯和測試發行版本。 發行版本會將編譯器最佳化納入，這些最佳化有時會影響應用程式的行為。 例如，設計來提升效能的編譯器最佳化可能會在非同步或多執行緒應用程式中，建立競爭條件。

若要建置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯]**** 變更為 [發行]****，如下圖所示。

![Image](./media/release.jpg)

當您按 F5 或從 [建置]**** 功能表中選擇 [建置方案]**** 時，Visual Studio 就會編譯您主控台應用程式的發行版本以供您測試。 您可以接著執行並測試該版本，就像您對應用程式的偵錯版本所做的一樣。

完成應用程式偵錯之後，下一個步驟就是發佈可散發的應用程式版本。 如需有關如何執行這項操作的資訊，請參閱[使用 Visual Studio 2017 來發佈 C# Hello World 應用程式 (英文)](./publishing-with-visual-studio-2017.md)。

