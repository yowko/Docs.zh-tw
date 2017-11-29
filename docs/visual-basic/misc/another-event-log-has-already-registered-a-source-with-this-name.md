---
title: "另一個事件記錄檔已經註冊此名稱的來源"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="4132a-102">另一個事件記錄檔已經註冊此名稱的來源</span><span class="sxs-lookup"><span data-stu-id="4132a-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="4132a-103">嘗試將項目寫入事件記錄檔，其中指定的來源已向另一個事件記錄檔登錄。</span><span class="sxs-lookup"><span data-stu-id="4132a-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="4132a-104">您必須設定您 <xref:System.Diagnostics.EventLog.Source%2A> 元件執行個體的 <xref:System.Diagnostics.EventLog> 屬性，元件才能將項目寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4132a-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="4132a-105">當發生這種情況時，系統會檢查您所指定的來源已向元件寫入的事件記錄檔登錄，並視需要呼叫 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 。</span><span class="sxs-lookup"><span data-stu-id="4132a-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4132a-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4132a-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="4132a-107">請使用 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 或 <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> 方法移除來源與第一個記錄檔的關聯。</span><span class="sxs-lookup"><span data-stu-id="4132a-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="4132a-108">向新的記錄檔登錄來源。</span><span class="sxs-lookup"><span data-stu-id="4132a-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4132a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4132a-109">See Also</span></span>  
 [<span data-ttu-id="4132a-110">My.Application.Log 物件</span><span class="sxs-lookup"><span data-stu-id="4132a-110">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="4132a-111">如何： 移除的事件來源</span><span class="sxs-lookup"><span data-stu-id="4132a-111">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [<span data-ttu-id="4132a-112">如何： 加入您的應用程式事件記錄檔項目的來源</span><span class="sxs-lookup"><span data-stu-id="4132a-112">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
