---
title: 無法刪除系統事件記錄檔
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: 72f648751107db90449a085e1a49892927fcd29b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620484"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="deaf1-102">無法刪除系統事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="deaf1-102">System event log cannot be deleted</span></span>
<span data-ttu-id="deaf1-103">嘗試刪除無法刪除的系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="deaf1-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="deaf1-104">系統記錄檔可追蹤系統事件 (例如系統啟動和硬體故障)。</span><span class="sxs-lookup"><span data-stu-id="deaf1-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="deaf1-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="deaf1-105">To correct this error</span></span>  
  
- <span data-ttu-id="deaf1-106">請考慮讓應用程式寫入至應用程式或自訂記錄檔，而不是系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="deaf1-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
- <span data-ttu-id="deaf1-107">請不要嘗試刪除系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="deaf1-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deaf1-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="deaf1-108">See also</span></span>

- <span data-ttu-id="deaf1-109">[管理事件記錄檔](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="deaf1-109">[Administering Event Logs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="deaf1-110">[如何：建立和移除自訂事件記錄檔](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="deaf1-110">[How to: Create and Remove Custom Event Logs](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span></span>
