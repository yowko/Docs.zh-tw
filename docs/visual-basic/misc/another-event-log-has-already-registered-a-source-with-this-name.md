---
title: 另一個事件記錄檔已經註冊此名稱的來源
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: d932869504b2d8a5f3a948b190e5528bfcfa664f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940605"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="f0e13-102">另一個事件記錄檔已經註冊此名稱的來源</span><span class="sxs-lookup"><span data-stu-id="f0e13-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="f0e13-103">嘗試將項目寫入事件記錄檔，其中指定的來源已向另一個事件記錄檔登錄。</span><span class="sxs-lookup"><span data-stu-id="f0e13-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="f0e13-104">您必須設定您 <xref:System.Diagnostics.EventLog.Source%2A> 元件執行個體的 <xref:System.Diagnostics.EventLog> 屬性，元件才能將項目寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="f0e13-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="f0e13-105">當發生這種情況時，系統會檢查您所指定的來源已向元件寫入的事件記錄檔登錄，並視需要呼叫 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f0e13-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f0e13-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f0e13-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f0e13-107">請使用 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 或 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 方法移除來源與第一個記錄檔的關聯。</span><span class="sxs-lookup"><span data-stu-id="f0e13-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2. <span data-ttu-id="f0e13-108">向新的記錄檔登錄來源。</span><span class="sxs-lookup"><span data-stu-id="f0e13-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e13-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0e13-109">See also</span></span>

- [<span data-ttu-id="f0e13-110">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f0e13-110">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
