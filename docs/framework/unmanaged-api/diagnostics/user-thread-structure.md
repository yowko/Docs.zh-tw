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
ms.openlocfilehash: 11551221732e454e48111d48d60ca9b72f7f9b66
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59127151"
---
# <a name="userthread-structure"></a><span data-ttu-id="042a2-102">USER_THREAD 結構</span><span class="sxs-lookup"><span data-stu-id="042a2-102">USER_THREAD Structure</span></span>
<span data-ttu-id="042a2-103">提供偵錯工具執行緒的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="042a2-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="042a2-104">如需詳細資訊，請參閱 < [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="042a2-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="042a2-105">語法</span><span class="sxs-lookup"><span data-stu-id="042a2-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="042a2-106">成員</span><span class="sxs-lookup"><span data-stu-id="042a2-106">Members</span></span>  
  
|<span data-ttu-id="042a2-107">成員</span><span class="sxs-lookup"><span data-stu-id="042a2-107">Member</span></span>|<span data-ttu-id="042a2-108">描述</span><span class="sxs-lookup"><span data-stu-id="042a2-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="042a2-109">執行緒緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="042a2-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="042a2-110">執行緒的緩衝區，以位元組為單位的長度。</span><span class="sxs-lookup"><span data-stu-id="042a2-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="042a2-111">執行緒 id。</span><span class="sxs-lookup"><span data-stu-id="042a2-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="042a2-112">需求</span><span class="sxs-lookup"><span data-stu-id="042a2-112">Requirements</span></span>  
 <span data-ttu-id="042a2-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="042a2-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042a2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="042a2-114">See also</span></span>

- [<span data-ttu-id="042a2-115">SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="042a2-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="042a2-116">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="042a2-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
