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
ms.openlocfilehash: 51db7a2b6464b562e09ce061991898a8d604ead1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437977"
---
# <a name="user_thread-structure"></a><span data-ttu-id="b5522-102">USER_THREAD 結構</span><span class="sxs-lookup"><span data-stu-id="b5522-102">USER_THREAD Structure</span></span>
<span data-ttu-id="b5522-103">提供有關執行緒的詳細資訊給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="b5522-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="b5522-104">如需詳細資訊，請參閱[INotifySource2：： SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="b5522-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5522-105">語法</span><span class="sxs-lookup"><span data-stu-id="b5522-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="b5522-106">Members</span><span class="sxs-lookup"><span data-stu-id="b5522-106">Members</span></span>  
  
|<span data-ttu-id="b5522-107">成員</span><span class="sxs-lookup"><span data-stu-id="b5522-107">Member</span></span>|<span data-ttu-id="b5522-108">描述</span><span class="sxs-lookup"><span data-stu-id="b5522-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="b5522-109">執行緒緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="b5522-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="b5522-110">執行緒緩衝區的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="b5522-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="b5522-111">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="b5522-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5522-112">需求</span><span class="sxs-lookup"><span data-stu-id="b5522-112">Requirements</span></span>  
 <span data-ttu-id="b5522-113">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="b5522-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5522-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5522-114">See also</span></span>

- [<span data-ttu-id="b5522-115">SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="b5522-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="b5522-116">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="b5522-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
