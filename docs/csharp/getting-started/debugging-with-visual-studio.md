---
title: "使用 Visual Studio 2017 偵錯 C# Hello World 應用程式 | Microsoft Docs"
description: "了解如何使用 Visual Studio 2017 對以 C# 撰寫的 Hello World 應用程式進行偵錯。"
keywords: ".NET Core, .NET Core 主控台應用程式, .NET Core 偵錯"
author: BillWagner
ms.author: wiwagn
ms.date: 04/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: cb213625-cc60-438b-9b9e-49aed0e4a974
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 026158029bfc843bd6cd171933091dc9ac6d4dbe
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# 使用 Visual Studio 2017 針對您的 C# Hello World 應用程式進行偵錯
<a id="debugging-your-c-hello-world-application-with-visual-studio-2017" class="xliff"></a>

到目前為止，您已遵循[在 Visual Studio 2017 中使用 .NET Core 組置 C# Hello World 應用程式](.\with-visual-studio.md)中的步驟來建立和執行簡單的主控台應用程式。 在您撰寫並編譯應用程式之後，便可以開始測試它。 Visual Studio 包含一組完整的偵錯工具，可供您在針對應用程式進行測試和疑難排解時使用。

## 在偵錯模式下進行偵錯
<a id="debugging-in-debug-mode" class="xliff"></a>

[偵錯] 和 [發行] 是 Visual Studio 其中兩個預設的組建組態。 目前的組建組態會顯示在工具列上。 下列工具列影像顯示 Visual Studio 已設定為在 [偵錯] 模式下編譯您的應用程式。

   ![Visual Studio 工具列](./media/debugging-with-visual-studio/toolbar1.png)

您應該一律從在 [偵錯] 模式下進行程式測試開始。 [偵錯] 模式會關閉大多數的編譯器最佳化，並可在組置程序期間提供更豐富的資訊。

## 設定中斷點
<a id="setting-a-breakpoint" class="xliff"></a>

請在 [偵錯] 模式下執行程式並嘗試幾個偵錯功能：

1. 「中斷點」會在含有中斷點的行執行「之前」，暫時中斷應用程式的執行。 在程式碼視窗左邊界中按一下顯示 `Console.WriteLine("\nHello, {0}, on {1:d} at {1:t}", name, date);` 的這一行，以將中斷點設定在該行，或在已選取該行的情況下選擇 [偵錯]  >  [切換中斷點] 功能表項目。 如下圖所示，Visual Studio 會以醒目提示並在左邊界顯示一個紅色圓圈的方式，指出已設定中斷點的行。

   ![已設定中斷點的 Visual Studio 程式視窗](./media/debugging-with-visual-studio/setbreakpoint.png)

1. 在 [偵錯] 模式下執行程式，方法是選取工具列上帶有綠色箭號的 **HelloWorld** 按鈕、按 F5，或選擇 [偵錯]  >  [開始偵錯]。

1. 當程式提示輸入名稱時，在主控台視窗中輸入字串，然後按 Enter。

1. 程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。 [自動變數] 視窗會顯示目前行附近所使用變數的值。 [區域變數] 視窗會顯示目前正在執行的方法中所定義變數的值。

   ![Visual Studio Application Insights](./media/debugging-with-visual-studio/break.png)

1. 您可以變更變數的值，以了解它會如何影響我們的程式。 如果看不到 [即時運算視窗]，請選擇 [偵錯]  >  [視窗]  >  [即時運算] 功能表項目。 [即時運算視窗] 可讓您與正在進行偵錯的應用程式互動。

1. 您可以藉由互動方式變更變數的值。 在 [即時運算視窗] 中輸入`name = "Gracie"`，然後按 Enter 鍵。

1. 在 [即時運算視窗] 中輸入 `date = new DateTime(2016,11,01,11,59,00)`，然後按 Enter 鍵。

   此 [即時運算視窗] 會顯示字串變數的值和 @System.DateTime 值的屬性。 此外，[自動變數] 和 [區域變數] 視窗中變數的值也會更新。

   ![[自動變數] 視窗和 [即時運算] 視窗](./media/debugging-with-visual-studio/autosimmediate.png)

1. 選取工具列中的 [繼續] 按鈕，或選取 [偵錯]  >  [繼續] 功能表項目，以繼續程式執行。 主控台視窗中顯示的值會與您在 [即時運算視窗] 中所做的變更對應。

   ![主控台視窗顯示在 [What is your name?] 提示字元上的輸入值 Jack，後面接著 Hello Gracie ，時間：11/1/2016 上午 11:59](./media/debugging-with-visual-studio/changed.png)

1. 按任意鍵以結束應用程式並結束 [偵錯] 模式。

## 設定條件中斷點
<a id="setting-a-conditional-breakpoint" class="xliff"></a>

您的程式會顯示使用者輸入的字串。 如果使用者未進行任何輸入時，會發生什麼情況？ 您可以利用有用的「條件中斷點」偵錯功能來測試此情況，以在一或多個條件成立時中斷程式執行。

若要設定條件中斷點並測試使用無法輸入字串時會發生的情況，請執行下列操作：

1. 在代表中斷點的紅點上按一下滑鼠右鍵。 在內容功能表上，選取 [條件] 以開啟 [中斷點設定] 對話方塊。 核取 [條件] 的方塊。

   ![中斷點設定面板](./media/debugging-with-visual-studio/breakpointsettings.png)

1. 對於 [條件運算式]，請以下列內容取代 "e.g. x == 5"：

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   您將針對程式碼條件進行測試。 您可以指定一個「叫用次數」，以在陳述式執行次數達到指定的次數之前中斷程式執行；或是指定一個「篩選條件」，以根據執行緒識別碼、處理序名稱或執行緒名稱等屬性中斷應用程式執行。

1. 選取 [關閉] 按鈕以關閉對話方塊。

1. 在 [偵錯] 模式下執行程式。

1. 在主控台視窗中，於提示您輸入名稱時，按 Enter 鍵。

1. 由於已經滿足我們指定的條件 (`name` 是 `null` 或 [`String.Empty`](xref:System.String.Empty))，因此程式會在到達中斷點且在 `Console.WriteLine` 方法執行之前，停止執行。

1. 選取 [區域變數] 視窗，此視窗會顯示目前正在執行之方法 (在您的程式中為 `Main` 方法) 的區域變數值。 注意到 `name` 變數的值會是 `""` 或 [`String.Empty`](xref:System.String.Empty)。

1. 請在 [即時運算視窗] 中輸入下列陳述式來確認此值是空字串。 結果為 `true`。

   ```csharp
   ? name == String.Empty
   ```

   ![[即時運算視窗] 在執行陳述式之後傳回值 true](./media/debugging-with-visual-studio/emptystring.png)

1. 選取工具列上的 [繼續] 按鈕以繼續程式執行。

1. 按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。

1. 按一下程式碼視窗左邊界中的點，或在已選取資料列的情況下選擇 [偵錯] > [切換中斷點] 功能表項目，以清除中斷點。

## 逐步執行程式
<a id="stepping-through-a-program" class="xliff"></a>

Visual Studio 也可讓您逐行執行程式並監視其執行情況。 通常，您會設定中斷點，然後使用此功能來依循程式流程執行您程式碼的一小部分。 由於您的程式相當小，因此您可以透過執行下列操作將整個程式執行一遍：

1. 在功能表列上，選擇 [偵錯]  >  [逐步執行]，或按 F11 鍵。 Visual Studio 會醒目提示要執行的下一行，並在該行旁邊顯示一個箭頭。

   ![Visual Studio 視窗](./media/debugging-with-visual-studio/stepinto1.png)

   此時，[自動變數] 視窗會顯示您的程式只有定義一個變數 `args`。 由於您尚未將任何命令行引數傳遞給程式，因此其值是空的字串陣列。 此外，Visual Studio 已開啟一個空白主控台視窗。

1. 選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。 Visual Studio 現在會醒目提示要執行的下一行。 如圖所示，執行上一個陳述式與這個陳述式之間的程式碼所花費的時間少於一毫秒。 `args` 仍是唯一的已宣告變數，而主控台視窗會保留空白。

   ![Visual Studio 視窗](./media/debugging-with-visual-studio/stepinto2.png)

1. 選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。 Visual Studio 會醒目提示包含 `name` 變數指派的陳述式。 [自動變數] 視窗會顯示 `name` 是 `null`，而主控台視窗則會顯示 "What is your name?" 字串。

1. 在主控台視窗中輸入一個字串並按 Enter，以回應提示。 主控台不會有回應，您輸入的字串也不會顯示在主控台視窗中，但 [`Console.ReadLine`](xref:System.Console.ReadLine) 方法仍然會擷取您的輸入。

1. 選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。 Visual Studio 會醒目提示包含 `date` 變數指派的陳述式。 [自動變數] 視窗會顯示 [`DateTime.Now`](xref:System.DateTime.Now) 屬性值，以及對 [`Console.ReadLine`](xref:System.Console.ReadLine) 方法進行呼叫所傳回的值。 主控台視窗也會顯示在主控台提示輸入時輸入的字串。

1. 選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。 [自動變數] 視窗現在會顯示從 [`DateTime.Now`](xref:System.DateTime.Now) 屬性指派之後的 `date` 變數值。 主控台視窗沒有變更。

1. 選取 [偵錯]  >  [逐步執行]，或按 F11 鍵。 Visual Studio 會呼叫 [`Console.WriteLine`](xref:System.Console.WriteLine(System.String,System.Object,System.Object)) 方法。 `date` 和 `name` 變數的值會顯示在 [自動變數] 視窗中，而主控台視窗則會顯示已格式化的字串。

1. 選取 [偵錯]  >  [跳離函式]，或按 Shift 和 F11 鍵。 這會停止逐步執行。 主控台視窗會顯示訊息並等候您按下按鍵。

1. 按任意鍵以關閉主控台視窗並結束 [偵錯] 模式。

## 組置發行版本
<a id="building-a-release-version" class="xliff"></a>

在對應用程式偵錯組建進行測試之後，您還應該編譯和測試發行版本。 發行版本會納入編譯器最佳化，這些最佳化有時會對應用程式的行為造成負面影響。 例如，設計來提升效能的編譯器最佳化可能會在非同步或多執行緒應用程式中，建立競爭條件。

若要組置並測試您主控台應用程式的發行版本，請將工具列上的組建組態從 [偵錯] 變更為 [發行]。

![Image](./media/debugging-with-visual-studio/toolbar2.png)

當您按 F5 或從 [組建] 功能表中選擇 [組置方案] 時，Visual Studio 就會編譯您主控台應用程式的發行版本。 您可以測試該版本，就像您對應用程式的偵錯版本所做的一樣。

完成應用程式偵錯之後，下一個步驟就是發行可部署的應用程式版本。 如需如何執行這項操作的資訊，請參閱[使用 Visual Studio 2017 發行 C# Hello World 應用程式](./publishing-with-visual-studio.md)。

