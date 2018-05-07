---
title: 另一個事件記錄檔已經註冊此名稱的來源
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: b12fd5dcdeaccb0dc294c44e4b8a898726978633
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>另一個事件記錄檔已經註冊此名稱的來源
嘗試將項目寫入事件記錄檔，其中指定的來源已向另一個事件記錄檔登錄。  
  
 您必須設定您 <xref:System.Diagnostics.EventLog.Source%2A> 元件執行個體的 <xref:System.Diagnostics.EventLog> 屬性，元件才能將項目寫入記錄檔。 當發生這種情況時，系統會檢查您所指定的來源已向元件寫入的事件記錄檔登錄，並視需要呼叫 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請使用 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 或 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 方法移除來源與第一個記錄檔的關聯。  
  
2.  向新的記錄檔登錄來源。  
  
## <a name="see-also"></a>另請參閱  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

