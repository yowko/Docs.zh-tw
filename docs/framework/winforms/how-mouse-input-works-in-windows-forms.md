---
title: 滑鼠輸入在 Windows Form 中的運作方式
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
ms.openlocfilehash: c9193ffa9ef34f1e43a92feec230fa2282264147
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203011"
---
# <a name="how-mouse-input-works-in-windows-forms"></a>滑鼠輸入在 Windows Form 中的運作方式
接收和處理滑鼠輸入是每個 Windows 應用程式中很重要的一部分。 您可以處理滑鼠事件，以在您的應用程式中執行的動作，或使用滑鼠位置資訊來執行點擊測試或其他動作。 此外，您可以變更您的應用程式中的控制項處理滑鼠輸入的方式。 本主題將描述這些詳細資料，以及如何取得和變更系統設定滑鼠的滑鼠事件。 如需使用滑鼠所提供的資料事件並在其中按一下滑鼠事件的順序引發，請參閱 < [Windows Form 中的滑鼠事件](mouse-events-in-windows-forms.md)。  
  
## <a name="mouse-location-and-hit-testing"></a>滑鼠位置和點擊測試  
 當使用者移動滑鼠時，作業系統會將滑鼠指標移至。 將滑鼠指標包含單一像素，稱為 「 作用點，它會追蹤的作業系統，且會辨識為指標的位置。 當使用者移動滑鼠，或按下滑鼠按鈕<xref:System.Windows.Forms.Control>，其中包含<xref:System.Windows.Forms.Cursor.HotSpot%2A>引發適當的滑鼠事件。 您可以取得與目前的滑鼠位置<xref:System.Windows.Forms.MouseEventArgs.Location%2A>的屬性<xref:System.Windows.Forms.MouseEventArgs>處理滑鼠事件時，或使用<xref:System.Windows.Forms.Cursor.Position%2A>屬性<xref:System.Windows.Forms.Cursor>類別。 您可以接著使用滑鼠位置資訊來執行點擊測試，然後再執行動作的滑鼠位置為基礎。 點擊測試的功能已內建在 Windows Form 中的數個控制項這類<xref:System.Windows.Forms.ListView>， <xref:System.Windows.Forms.TreeView>，<xref:System.Windows.Forms.MonthCalendar>和<xref:System.Windows.Forms.DataGridView>控制項。 搭配適當的滑鼠事件，<xref:System.Windows.Forms.Control.MouseHover>比方說，點擊測試是非常有助於判斷您的應用程式時應該執行特定動作。  
  
## <a name="mouse-events"></a>滑鼠事件  
 以回應滑鼠輸入的主要方式是處理滑鼠事件。 下表顯示滑鼠事件，並描述引發時。  
  
|滑鼠事件|描述|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|這個事件發生時放開滑鼠按鈕時，通常之前<xref:System.Windows.Forms.Control.MouseUp>事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。 處理當您只需要判斷時按一下，就會發生這個事件。|  
|<xref:System.Windows.Forms.Control.MouseClick>|在使用者按一下控制項時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 處理這個事件，當您需要按一下發生時，取得滑鼠的相關資訊。|  
|<xref:System.Windows.Forms.Control.DoubleClick>|按兩下控制項時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。 處理當您只需要判斷何時按兩下，就會發生這個事件。|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|當使用者按兩下滑鼠控制項，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 處理這個事件，當您需要取得有關滑鼠按兩下滑鼠時。|  
|<xref:System.Windows.Forms.Control.MouseDown>|當滑鼠指標位於控制項上方且使用者按下滑鼠按鈕時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseEnter>|當滑鼠指標進入控制項，視控制項的類型而定的框線或用戶端區域時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseHover>|當滑鼠指標會停止，並將滑鼠停留在控制項上方時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseLeave>|當滑鼠指標離開控制項，視控制項的類型而定的框線或用戶端區域時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseMove>|當滑鼠指標移動控制項上方時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseUp>|當滑鼠指標位於控制項上方且使用者放開滑鼠按鈕時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseWheel>|當控制項取得焦點且使用者滾動滑鼠滾輪時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 您可以使用<xref:System.Windows.Forms.MouseEventArgs.Delta%2A>屬性<xref:System.Windows.Forms.MouseEventArgs>來判斷滑鼠已捲動多遠。|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>變更滑鼠輸入，以及偵測系統設定  
 您可以偵測並變更控制項從 control 衍生，並使用處理滑鼠輸入的方式<xref:System.Windows.Forms.Control.GetStyle%2A>和<xref:System.Windows.Forms.Control.SetStyle%2A>方法。 <xref:System.Windows.Forms.Control.SetStyle%2A>方法會採用的位元組合<xref:System.Windows.Forms.ControlStyles>值來判斷控制項是否要有按一下或按兩下行為的標準，或如果控制項將處理滑鼠處理。 颾魤 ㄛ<xref:System.Windows.Forms.SystemInformation>類別所包含的屬性描述滑鼠的功能，並指定滑鼠與作業系統之間的互動方式。 下表摘要說明這些屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|取得維度，像素為單位，在其中，使用者必須按兩次，要考慮這兩個作業系統的區域中，按一下按兩下。|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|取得最大按第一次與第二次按滑鼠動作視為按兩下滑鼠的作業系統之間經過的毫秒數。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|取得滑鼠上的按鈕數目。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|取得值，指出是否已調換滑鼠左右按鈕的功能。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|取得矩型的維度 (以像素為單位)，滑鼠指標必須在此範圍內停留一段滑鼠暫留時間，才能產生滑鼠暫留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|取得時間 (以毫秒為單位)，滑鼠指標在該段時間內必須停留在停留矩形內，才能產生滑鼠停留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|取得值，指出是否已安裝滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|取得值，指出目前的滑鼠速度，從 1 到 20。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|取得值，指出是否已安裝具有滑鼠滾輪的滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|取得單一滑鼠滾輪旋轉增量的差異值數量。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|取得轉動滑鼠滾輪時要捲動的行數。|  
  
## <a name="see-also"></a>另請參閱

- [Windows Forms 應用程式中的滑鼠輸入](mouse-input-in-a-windows-forms-application.md)
- [Windows Form 中的滑鼠捕捉](mouse-capture-in-windows-forms.md)
- [Windows Form 中的滑鼠指標](mouse-pointers-in-windows-forms.md)
