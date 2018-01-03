---
title: "USER_THREAD 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: USER_THREAD
api_location: diasymreader.dll
api_type: COM
f1_keywords: USER_THREAD
helpviewer_keywords: USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 50533ce25812ad49d538c5a6a6c814d7a9704053
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="userthread-structure"></a><span data-ttu-id="37696-102">USER_THREAD 結構</span><span class="sxs-lookup"><span data-stu-id="37696-102">USER_THREAD Structure</span></span>
<span data-ttu-id="37696-103">提供資訊給偵錯工具執行緒。</span><span class="sxs-lookup"><span data-stu-id="37696-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="37696-104">如需詳細資訊，請參閱[inotifysource2:: Setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="37696-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37696-105">語法</span><span class="sxs-lookup"><span data-stu-id="37696-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="37696-106">成員</span><span class="sxs-lookup"><span data-stu-id="37696-106">Members</span></span>  
  
|<span data-ttu-id="37696-107">成員</span><span class="sxs-lookup"><span data-stu-id="37696-107">Member</span></span>|<span data-ttu-id="37696-108">描述</span><span class="sxs-lookup"><span data-stu-id="37696-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="37696-109">執行緒緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="37696-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="37696-110">執行緒的緩衝區，以位元組為單位的長度。</span><span class="sxs-lookup"><span data-stu-id="37696-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="37696-111">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="37696-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37696-112">需求</span><span class="sxs-lookup"><span data-stu-id="37696-112">Requirements</span></span>  
 <span data-ttu-id="37696-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="37696-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37696-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="37696-114">See Also</span></span>  
 [<span data-ttu-id="37696-115">SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="37696-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="37696-116">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="37696-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
