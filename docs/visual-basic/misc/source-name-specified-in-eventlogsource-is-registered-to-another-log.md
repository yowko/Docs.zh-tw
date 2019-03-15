---
title: 在 EventLogSource 中指定的來源名稱會登錄到不在 EventLogName 指定的記錄檔
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 22129ab0c4f7fe0a78300907a949d9368028c9fa
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58022301"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="6ae4b-102">在 EventLogSource 中指定的來源名稱會登錄到不在 EventLogName 指定的記錄檔</span><span class="sxs-lookup"><span data-stu-id="6ae4b-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="6ae4b-103">`EventLog` 嘗試參考登錄到不同記錄檔的來源。</span><span class="sxs-lookup"><span data-stu-id="6ae4b-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="6ae4b-104">如果要將項目寫入事件記錄檔，您必須指定 <xref:System.Diagnostics.EventLog.Source%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6ae4b-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="6ae4b-105"><xref:System.Diagnostics.EventLog.Source%2A> 屬性會將元件和事件記錄登錄為有效的項目來源。</span><span class="sxs-lookup"><span data-stu-id="6ae4b-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="6ae4b-106">單一來源一次只能和一筆事件記錄建立關聯 (因此寫入項目)。</span><span class="sxs-lookup"><span data-stu-id="6ae4b-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="6ae4b-107">根據預設，如果您嘗試寫入項目，卻沒有先將元件登錄為有效的來源，系統會使用 <xref:System.Diagnostics.EventLog.Source%2A> 屬性的值當做來源字串，自動登錄來源和事件記錄。</span><span class="sxs-lookup"><span data-stu-id="6ae4b-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6ae4b-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6ae4b-108">To correct this error</span></span>  
  
-   <span data-ttu-id="6ae4b-109">請確定來源已登錄到正確的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6ae4b-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="6ae4b-110">若要這樣做，請使用 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 方法或其多載之一，指定可向事件記錄檔唯一識別元件的字串。</span><span class="sxs-lookup"><span data-stu-id="6ae4b-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae4b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ae4b-111">See also</span></span>

- <span data-ttu-id="6ae4b-112">[管理事件記錄檔](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6ae4b-112">[Administering Event Logs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="6ae4b-113">[事件記錄檔參考](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6ae4b-113">[Event Log References](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span></span>
- <span data-ttu-id="6ae4b-114">[如何：做為來源的事件記錄檔項目加入您的應用程式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6ae4b-114">[How to: Add Your Application as a Source of Event Log Entries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span></span>
- <span data-ttu-id="6ae4b-115">[如何：移除的事件來源](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6ae4b-115">[How to: Remove an Event Source](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span></span>
