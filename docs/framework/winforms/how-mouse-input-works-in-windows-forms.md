---
title: "滑鼠輸入在 Windows Form 中的運作方式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, mouse input
- mouse [Windows Forms], input
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 388fd8d3e7f23dc55d46c5a097be99e9f1c34ab0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-mouse-input-works-in-windows-forms"></a>滑鼠輸入在 Windows Form 中的運作方式
接收和處理滑鼠輸入為每個 Windows 應用程式中很重要的一部分。 您可以處理應用程式中執行動作的滑鼠事件，或使用滑鼠位置資訊來執行的點擊測試或其他動作。 此外，您可以變更您的應用程式中的控制項處理滑鼠輸入的方式。 本主題將描述這些中的滑鼠事件的詳細資料，以及如何取得及變更滑鼠的系統設定。 如需詳細資訊，使用滑鼠提供之資料的相關事件，以滑鼠按一下事件的順序引發，請參閱[Windows Form 中的滑鼠事件](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)。  
  
## <a name="mouse-location-and-hit-testing"></a>滑鼠位置與點擊測試  
 當使用者移動滑鼠時，作業系統會將滑鼠指標移至。 滑鼠指標所包含之單一像素，稱為作用區，且作業系統會追蹤會辨識為指標的位置。 當使用者移動滑鼠，或按下滑鼠按鈕，<xref:System.Windows.Forms.Control>包含<xref:System.Windows.Forms.Cursor.HotSpot%2A>引發適當的滑鼠事件。 您可以取得與目前的滑鼠位置<xref:System.Windows.Forms.MouseEventArgs.Location%2A>屬性<xref:System.Windows.Forms.MouseEventArgs>處理滑鼠事件時，或使用<xref:System.Windows.Forms.Cursor.Position%2A>屬性<xref:System.Windows.Forms.Cursor>類別。 您可以接著執行點擊測試，使用滑鼠位置資訊，然後再執行動作的滑鼠位置為基礎。 點擊測試的功能已內建在 Windows Form 中的數個控制項例如<xref:System.Windows.Forms.ListView>， <xref:System.Windows.Forms.TreeView>，<xref:System.Windows.Forms.MonthCalendar>和<xref:System.Windows.Forms.DataGridView>控制項。 搭配適當的滑鼠事件，<xref:System.Windows.Forms.Control.MouseHover>比方說，點擊測試是非常有用來判斷您的應用程式時應該執行特定動作。  
  
## <a name="mouse-events"></a>滑鼠事件  
 處理滑鼠事件為主要方式來回應滑鼠輸入。 下表顯示滑鼠事件，並描述它們時引發的方法。  
  
|滑鼠事件|描述|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|放開滑鼠按鈕時，通常之前時，就會發生此事件<xref:System.Windows.Forms.Control.MouseUp>事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。 處理當您只需要判斷時按一下，就會發生這個事件。|  
|<xref:System.Windows.Forms.Control.MouseClick>|當使用者按一下控制項，使用滑鼠，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 處理這個事件，當您需要按一下發生時取得的滑鼠相關資訊。|  
|<xref:System.Windows.Forms.Control.DoubleClick>|按兩下控制項時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。 處理這個事件，當您只需要判斷按兩下時。|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|當使用者按兩下滑鼠的控制項，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 處理這個事件，當您需要取得按兩下滑鼠時的滑鼠相關的資訊。|  
|<xref:System.Windows.Forms.Control.MouseDown>|當滑鼠指標位於控制項上，而且使用者按下滑鼠按鈕時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseEnter>|當滑鼠指標進入控制項，視控制項的類型而定的框線或用戶端區域時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseHover>|當滑鼠指標會停止，並將滑鼠停留在控制項上時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseLeave>|當滑鼠指標離開控制項，視控制項的類型而定的框線或用戶端區域時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseMove>|當滑鼠指標移到控制項時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseUp>|當滑鼠指標位於控制項上，且使用者釋放滑鼠按鈕時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.MouseWheel>|控制項擁有焦點且使用者滾動滑鼠滾輪時，就會發生此事件。 這個事件的處理常式會接收 <xref:System.Windows.Forms.MouseEventArgs> 類型的引數。 您可以使用<xref:System.Windows.Forms.MouseEventArgs.Delta%2A>屬性<xref:System.Windows.Forms.MouseEventArgs>來判斷已捲動滑鼠的幅度。|  
  
## <a name="changing-mouse-input-and-detecting-system-settings"></a>變更滑鼠輸入，以及偵測系統設定  
 您可以偵測並變更控制項的滑鼠輸入透過處理衍生自控制項及使用的方式<xref:System.Windows.Forms.Control.GetStyle%2A>和<xref:System.Windows.Forms.Control.SetStyle%2A>方法。 <xref:System.Windows.Forms.Control.SetStyle%2A>方法會採用的位元組合<xref:System.Windows.Forms.ControlStyles>值來判斷控制項是否有按一下或按兩下行為的標準，或如果此控制項將處理滑鼠處理。 此外，<xref:System.Windows.Forms.SystemInformation>類別所包含的屬性描述滑鼠的功能，並指定與作業系統的滑鼠互動方式。 下表摘要說明這些屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|取得為像素為單位，區域中，使用者必須按兩次，要考慮這兩個作業系統的按下滑鼠按鍵。|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|取得最大的第一次按和作業系統，才能將滑鼠動作視為按兩下滑鼠的第二個點擊之間所經過的毫秒數。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|取得滑鼠上的按鈕數目。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|取得值，指出是否已調換滑鼠左右按鈕的功能。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|取得矩型的維度 (以像素為單位)，滑鼠指標必須在此範圍內停留一段滑鼠暫留時間，才能產生滑鼠暫留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|取得時間 (以毫秒為單位)，滑鼠指標在該段時間內必須停留在停留矩形內，才能產生滑鼠停留訊息。|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|取得值，指出是否已安裝滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|取得值，指出目前的滑鼠速度，從 1 到 20。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|取得值，指出是否已安裝具有滑鼠滾輪的滑鼠。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|取得單一滑鼠滾輪旋轉增量的差異值數量。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|取得轉動滑鼠滾輪時要捲動的行數。|  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Windows Forms 中的滑鼠捕捉](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)  
 [Windows Forms 中的滑鼠指標](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)
