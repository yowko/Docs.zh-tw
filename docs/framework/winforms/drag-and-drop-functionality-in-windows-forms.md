---
title: Windows Form 中的拖放功能
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: 29ed138f80705539b96f82898e50e80dd0e3cb16
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527025"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Windows Form 中的拖放功能
Windows Form 包含一組實作拖放行為的方法、事件和類別。 本主題提供 Windows Form 中的拖放功能支援概觀。  另請參閱[拖放作業和剪貼簿支援](https://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\))。  
  
## <a name="performing-drag-and-drop-operations"></a>執行拖放作業  
 若要執行拖放作業時，請使用 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.DoDragDrop%2A> 方法。 如需如何執行拖放作業的詳細資訊，請參閱 <xref:System.Windows.Forms.Control.DoDragDrop%2A>。 若要取得必須在開始拖放作業前先將滑鼠指標拖曳到其上的矩形，請使用 <xref:System.Windows.Forms.SystemInformation> 類別的 <xref:System.Windows.Forms.SystemInformation.DragSize%2A> 屬性。  
  
## <a name="events-related-to-drag-and-drop-operations"></a>與拖放作業相關的事件  
 拖放作業包含兩類事件：拖放作業的目前目標所發生的事件，以及拖放作業的來源所發生的事件。  
  
### <a name="events-on-the-current-target"></a>目前目標所發生的事件  
 下表顯示拖放作業的目前目標所發生的事件。  
  
|滑鼠事件|描述|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|這個事件會在將物件拖曳至控制項的界限內時發生。 這個事件的處理常式會接收 <xref:System.Windows.Forms.DragEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.DragOver>|這個事件會在滑鼠指標位於控制項界限內的情況下拖曳物件時發生。 這個事件的處理常式會接收 <xref:System.Windows.Forms.DragEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.DragDrop>|這個事件會在拖放作業完成時發生。 這個事件的處理常式會接收 <xref:System.Windows.Forms.DragEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.DragLeave>|這個事件會在將物件拖曳出控制項的界限時發生。 這個事件的處理常式會接收 <xref:System.EventArgs> 類型的引數。|  
  
 <xref:System.Windows.Forms.DragEventArgs> 類別提供滑鼠指標的位置、滑鼠按鈕和鍵盤輔助按鍵的目前狀態、正在拖曳的資料，以及可指定拖曳事件來源所允許的作業和作業的目標置放效果的 <xref:System.Windows.Forms.DragDropEffects> 值。  
  
### <a name="events-on-the-source"></a>來源所發生的事件  
 下表顯示拖放作業的來源所發生的事件。  
  
|滑鼠事件|描述|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|這個事件會在拖曳作業期間發生。 它提供了一個可對正在發生拖放作業的使用者顯示視覺提示的機會，例如變更滑鼠指標。 這個事件的處理常式會接收 <xref:System.Windows.Forms.GiveFeedbackEventArgs> 類型的引數。|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|這個事件會在拖放作業期間引發，讓拖曳來源能夠決定是否應取消拖放作業。 這個事件的處理常式會接收 <xref:System.Windows.Forms.QueryContinueDragEventArgs> 類型的引數。|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> 類別提供滑鼠按鈕和鍵盤輔助按鍵的目前狀態、指定是否已按下 ESC 鍵的值，以及可設定以指定是否應該繼續拖放作業的 <xref:System.Windows.Forms.DragAction> 值。  
  
## <a name="see-also"></a>另請參閱
- [Windows Forms 應用程式中的滑鼠輸入](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
