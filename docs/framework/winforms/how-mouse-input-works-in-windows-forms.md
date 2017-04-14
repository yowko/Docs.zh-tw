---
title: "滑鼠輸入在 Windows Form 中的運作方式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "滑鼠, 輸入"
  - "Windows Form, 滑鼠輸入"
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 滑鼠輸入在 Windows Form 中的運作方式
接收及處理滑鼠輸入是每個 Windows 應用程式的重要部分。  處理滑鼠事件可讓您在應用程式中執行某個動作；或者您可使用滑鼠位置資訊來執行點擊測試 \(Hit Testing\) 或其他動作。  此外，您還可以變更應用程式中控制項對滑鼠輸入的處理方式。  這個主題將詳細描述這些滑鼠事件以及如何取得和變更滑鼠的系統設定。  如需滑鼠事件所提供的資料以及滑鼠 Click 事件的引發順序等相關詳細資訊，請參閱 [Windows Form 中的滑鼠事件](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)。  
  
## 滑鼠位置和點擊測試  
 使用者移動滑鼠時，作業系統會隨之移動滑鼠指標。  滑鼠指標包含稱之為作用點 \(Hot Spot\) 的單一像素，它是作業系統所追蹤的點且將其識別為指標位置。  當使用者移動滑鼠或按下滑鼠按鍵時，包含 <xref:System.Windows.Forms.Cursor.HotSpot%2A> 的 <xref:System.Windows.Forms.Control> 會引發適當的滑鼠事件。  處理滑鼠事件或使用 <xref:System.Windows.Forms.Cursor> 類別的 <xref:System.Windows.Forms.Cursor.Position%2A> 屬性時，您可利用 <xref:System.Windows.Forms.MouseEventArgs> 的 <xref:System.Windows.Forms.MouseEventArgs.Location%2A> 屬性來取得目前的滑鼠位置。  接著您可使用滑鼠位置資訊來執行點擊測試，然後再依據滑鼠的位置執行某項動作。  點擊測試功能已內建在 Windows Form 中的數種控制項，例如 <xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.MonthCalendar> 和 <xref:System.Windows.Forms.DataGridView> 控制項。  點擊測試是與適當的滑鼠事件搭配使用，例如 <xref:System.Windows.Forms.Control.MouseHover>，非常適合用於判斷應用程式應於何時執行某一特定動作。  
  
## 滑鼠事件  
 回應滑鼠輸入的主要方式即是處理滑鼠事件；  下表會說明滑鼠事件以及這些事件引發的時機：  
  
|滑鼠事件|描述|  
|----------|--------|  
|<xref:System.Windows.Forms.Control.Click>|當釋放滑鼠按鈕時會發生這個事件，通常是在 <xref:System.Windows.Forms.Control.MouseUp> 事件之前。  這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。  當您僅需要判斷按一下的時間點時，請處理這個事件。|  
|<xref:System.Windows.Forms.Control.MouseClick>|當使用者以滑鼠按一下控制項時會發生這個事件。  這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。  當您需要取得按一下時的滑鼠相關資訊，請處理這個事件。|  
|<xref:System.Windows.Forms.Control.DoubleClick>|當按兩下控制項時會發生這個事件。  這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。  當您僅需要判斷按兩下的時間點時，請處理這個事件。|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|當使用者以滑鼠按兩下控制項時會發生這個事件。  這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。  當您需要取得按兩下時的滑鼠相關資訊，請處理這個事件。|  
|<xref:System.Windows.Forms.Control.MouseDown>|當滑鼠指標移至控制項上且使用者按下滑鼠按鈕時會發生這個事件。  這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseEnter>|當滑鼠指標進入控制項的框線或工作區 \(視控制項型別而定\) 時會發生這個事件。  這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseHover>|當滑鼠指標在控制項上靜止不動時會發生這個事件。  這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseLeave>|當滑鼠指標離開控制項的框線或工作區 \(視控制項型別而定\) 時會發生這個事件。  這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseMove>|當滑鼠指標在控制項上移動時會發生這個事件。  這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseUp>|當滑鼠指標移至控制項上且使用者釋放滑鼠按鈕時會發生這個事件。  這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseWheel>|當使用者在控制項具有焦點的情況下轉動滑鼠滾輪時會發生這個事件。  這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。  您可以使用 <xref:System.Windows.Forms.MouseEventArgs> 的 <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> 屬性來判斷滑鼠所捲動的距離。|  
  
## 變更滑鼠輸入和偵測系統設定  
 您可以從控制項進行衍生然後使用 <xref:System.Windows.Forms.Control.GetStyle%2A> 和 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，來偵測該控制項處理滑鼠輸入的方式。  <xref:System.Windows.Forms.Control.SetStyle%2A> 方法採用 <xref:System.Windows.Forms.ControlStyles> 值的位元組合，來判斷控制項將有標準按一下或按兩下行為，或是控制項將進行它自己的滑鼠處理。  此外，<xref:System.Windows.Forms.SystemInformation> 類別包括描述滑鼠功能的屬性以及指定滑鼠與作業系統之互動方式的屬性。  下表摘要說明了這些屬性：  
  
|屬性|描述|  
|--------|--------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|取得區域的維度 \(以像素為單位\)，在此範圍內使用者必須按兩次，作業系統才會將這兩次的按一下動作視為按兩下。|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|取得毫秒數，這是第一次按一下和第二次按一下的最大時間間隔，作業系統在此期間內會將滑鼠動作視為按兩下動作。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|取得滑鼠上的按鈕數目。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|取得值，指出是否已調換滑鼠左右按鈕的功能。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|取得矩型的維度 \(以像素為單位\)，滑鼠指標必須在此範圍內停留一段滑鼠暫留時間，才能產生滑鼠暫留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|取得時間 \(以毫秒為單位\)，滑鼠指標在該段時間內必須停留在停留矩形內，才能產生滑鼠停留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|取得值，指出是否已安裝滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|取得值，指出目前的滑鼠速度，範圍可以從 1 到 20。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|取得值，指出是否已安裝具有滑鼠滾輪的滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|取得滑鼠滾輪單次轉動的遞增差異值總數。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|取得轉動滑鼠滾輪時要捲動的行數。|  
  
## 請參閱  
 [Windows Form 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)   
 [Windows Form 中的滑鼠捕捉](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)   
 [Windows Form 中的滑鼠指標](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)