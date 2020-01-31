---
title: 滑鼠輸入的運作方式
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: 1164974e65ca1e96c0650569626ad4140baf004e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739631"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>滑鼠輸入在 Windows Form 中的運作方式
接收和處理滑鼠輸入是每個 Windows 應用程式的重要部分。 您可以處理滑鼠事件以在應用程式中執行動作，或使用滑鼠位置資訊來執行點擊測試或其他動作。 此外，您可以變更應用程式中的控制項處理滑鼠輸入的方式。 本主題詳細說明這些滑鼠事件，以及如何取得和變更滑鼠的系統設定。 如需滑鼠事件所提供的資料以及引發滑鼠點擊事件順序的詳細資訊，請參閱[Windows Forms 中的滑鼠事件](mouse-events-in-windows-forms.md)。  
  
## <a name="mouse-location-and-hit-testing"></a>滑鼠位置和點擊測試  
 當使用者移動滑鼠時，作業系統會移動滑鼠指標。 滑鼠指標包含稱為「作用點」的單一圖元，作業系統會將它追蹤並辨識為指標的位置。 當使用者移動滑鼠或按下滑鼠按鍵時，包含 <xref:System.Windows.Forms.Cursor.HotSpot%2A> 的 <xref:System.Windows.Forms.Control> 會引發適當的滑鼠事件。 處理滑鼠事件時，您可以使用 <xref:System.Windows.Forms.MouseEventArgs> 的 <xref:System.Windows.Forms.MouseEventArgs.Location%2A> 屬性來取得目前的滑鼠位置，或使用 <xref:System.Windows.Forms.Cursor> 類別的 <xref:System.Windows.Forms.Cursor.Position%2A> 屬性。 接著，您可以使用滑鼠位置資訊來執行點擊測試，然後根據滑鼠的位置來執行動作。 點擊測試功能內建于 Windows Forms 中的數個控制項，例如 <xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.MonthCalendar> 和 <xref:System.Windows.Forms.DataGridView> 控制項。 以適當的滑鼠事件使用，<xref:System.Windows.Forms.Control.MouseHover> 例如，點擊測試對於判斷您的應用程式何時應執行特定動作非常有用。  
  
## <a name="mouse-events"></a>滑鼠事件  
 回應滑鼠輸入的主要方式是處理滑鼠事件。 下表顯示滑鼠事件，並描述它們的引發時機。  
  
|滑鼠事件|描述|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|釋放滑鼠按鍵時（通常是在 <xref:System.Windows.Forms.Control.MouseUp> 事件之前），就會發生這個事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。 當您只需要判斷按一下發生的時間時，請處理這個事件。|  
|<xref:System.Windows.Forms.Control.MouseClick>|當使用者以滑鼠按一下控制項時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 當您在按一下時需要取得滑鼠的相關資訊時，請處理這個事件。|  
|<xref:System.Windows.Forms.Control.DoubleClick>|按兩下控制項時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。 當您只需要決定何時發生按兩下時，處理這個事件。|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|當使用者使用滑鼠按兩下控制項時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 當您需要在按兩下時取得滑鼠的相關資訊時，請處理這個事件。|  
|<xref:System.Windows.Forms.Control.MouseDown>|當滑鼠指標位於控制項上，且使用者按下滑鼠按鍵時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseEnter>|當滑鼠指標進入控制項的框線或工作區時（視控制項的類型而定），就會發生這個事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseHover>|當滑鼠指標停駐並停留在控制項上方時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseLeave>|當滑鼠指標離開控制項的框線或工作區時（視控制項的類型而定），就會發生這個事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseMove>|當滑鼠指標移至控制項上方時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseUp>|當滑鼠指標位於控制項上，而使用者放開滑鼠按鍵時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseWheel>|當控制項有焦點時，當使用者旋轉滑鼠滾輪時，就會發生這個事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 您可以使用 <xref:System.Windows.Forms.MouseEventArgs> 的 [<xref:System.Windows.Forms.MouseEventArgs.Delta%2A>] 屬性來決定滑鼠滾動的距離。|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>變更滑鼠輸入和偵測系統設定  
 您可以藉由衍生自控制項並使用 <xref:System.Windows.Forms.Control.GetStyle%2A> 和 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法，來偵測和變更控制項處理滑鼠輸入的方式。 <xref:System.Windows.Forms.Control.SetStyle%2A> 方法會接受 <xref:System.Windows.Forms.ControlStyles> 值的位元組合，以判斷控制項是否會有標準的點擊或按兩下行為，或控制項是否會處理自己的滑鼠處理。 此外，<xref:System.Windows.Forms.SystemInformation> 類別還包含描述滑鼠功能的屬性，並指定滑鼠與作業系統互動的方式。 下表摘要說明這些屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|取得區域的大小（以圖元為單位），使用者必須按兩次滑鼠按鍵，才可考慮按兩下這兩個點。|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|取得第一次點擊和第二次按一下時所能達到的最大毫秒數，讓作業系統將滑鼠動作視為按兩下。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|取得滑鼠上的按鈕數目。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|取得值，指出是否已調換滑鼠左右按鈕的功能。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|取得矩型的維度 (以像素為單位)，滑鼠指標必須在此範圍內停留一段滑鼠暫留時間，才能產生滑鼠暫留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|取得時間 (以毫秒為單位)，滑鼠指標在該段時間內必須停留在停留矩形內，才能產生滑鼠停留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|取得值，指出是否已安裝滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|取得值，指出目前的滑鼠速度，從1到20。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|取得值，指出是否已安裝具有滑鼠滾輪的滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|取得單一滑鼠滾輪旋轉增量的差異值數量。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|取得轉動滑鼠滾輪時要捲動的行數。|  
  
## <a name="see-also"></a>請參閱

- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
- [Windows Forms 中的滑鼠捕捉](mouse-capture-in-windows-forms.md)
- [Windows Forms 中的滑鼠指標](mouse-pointers-in-windows-forms.md)
