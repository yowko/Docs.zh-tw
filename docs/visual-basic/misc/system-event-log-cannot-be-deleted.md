---
title: "無法刪除系統事件記錄檔"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 26ca8819-4ce5-49c6-98f3-27fe9e2e8e3d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e07c6514d8ef3dd4f1cad40cbab1ff1c54c65796
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="system-event-log-cannot-be-deleted"></a><span data-ttu-id="4514f-102">無法刪除系統事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="4514f-102">System event log cannot be deleted</span></span>
<span data-ttu-id="4514f-103">嘗試刪除無法刪除的系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4514f-103">An attempt has been made to delete the system event log, which cannot be deleted.</span></span> <span data-ttu-id="4514f-104">系統記錄檔可追蹤系統事件 (例如系統啟動和硬體故障)。</span><span class="sxs-lookup"><span data-stu-id="4514f-104">The system log tracks system events such as system startup and hardware failures.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4514f-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="4514f-105">To correct this error</span></span>  
  
-   <span data-ttu-id="4514f-106">請考慮讓應用程式寫入至應用程式或自訂記錄檔，而不是系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4514f-106">Consider having your application write to an application or custom log, rather than the system event log.</span></span>  
  
-   <span data-ttu-id="4514f-107">請不要嘗試刪除系統事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4514f-107">Do not attempt to delete the system event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4514f-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="4514f-108">See Also</span></span>  
 [<span data-ttu-id="4514f-109">管理事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="4514f-109">Administering Event Logs</span></span>](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="4514f-110">如何： 建立和移除自訂事件記錄檔</span><span class="sxs-lookup"><span data-stu-id="4514f-110">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/library/af9b7da0-80c7-46ac-b7f7-897063ddd503)
