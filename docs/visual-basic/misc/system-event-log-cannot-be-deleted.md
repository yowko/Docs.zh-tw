---
title: 無法刪除系統事件記錄檔
ms.date: 07/20/2015
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
ms.openlocfilehash: e00527300a77f6bc006555ee688e055e1a351056
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554953"
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="2b311-102">無法刪除系統事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="2b311-102">System event log cannot be deleted</span></span>
<span data-ttu-id="2b311-103">嘗試刪除無法刪除的系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b311-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="2b311-104">系統記錄檔可追蹤系統事件 (例如系統啟動和硬體故障)。</span><span class="sxs-lookup"><span data-stu-id="2b311-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2b311-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2b311-105">To correct this error</span></span>  
  
- <span data-ttu-id="2b311-106">請考慮讓應用程式寫入至應用程式或自訂記錄檔，而不是系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b311-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
- <span data-ttu-id="2b311-107">請不要嘗試刪除系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="2b311-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b311-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b311-108">See also</span></span>

- <span data-ttu-id="2b311-109">[管理事件記錄檔](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2b311-109">[Administering Event Logs](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="2b311-110">[如何：建立和移除自訂事件記錄檔](/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2b311-110">[How to: Create and Remove Custom Event Logs](/previous-versions/visualstudio/visual-studio-2008/49dwckkz(v=vs.90))</span></span>
