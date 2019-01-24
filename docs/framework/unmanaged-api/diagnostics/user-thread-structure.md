---
title: USER_THREAD 結構
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acc4da79796e975d349d1cb33c301c25c4791cb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709074"
---
# <a name="userthread-structure"></a><span data-ttu-id="14402-102">USER_THREAD 結構</span><span class="sxs-lookup"><span data-stu-id="14402-102">USER_THREAD Structure</span></span>
<span data-ttu-id="14402-103">提供偵錯工具執行緒的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="14402-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="14402-104">如需詳細資訊，請參閱 < [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="14402-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14402-105">語法</span><span class="sxs-lookup"><span data-stu-id="14402-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="14402-106">成員</span><span class="sxs-lookup"><span data-stu-id="14402-106">Members</span></span>  
  
|<span data-ttu-id="14402-107">成員</span><span class="sxs-lookup"><span data-stu-id="14402-107">Member</span></span>|<span data-ttu-id="14402-108">描述</span><span class="sxs-lookup"><span data-stu-id="14402-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="14402-109">執行緒緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="14402-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="14402-110">執行緒的緩衝區，以位元組為單位的長度。</span><span class="sxs-lookup"><span data-stu-id="14402-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="14402-111">執行緒 id。</span><span class="sxs-lookup"><span data-stu-id="14402-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14402-112">需求</span><span class="sxs-lookup"><span data-stu-id="14402-112">Requirements</span></span>  
 <span data-ttu-id="14402-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="14402-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14402-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14402-114">See also</span></span>
- [<span data-ttu-id="14402-115">SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="14402-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="14402-116">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="14402-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
