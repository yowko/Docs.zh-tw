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
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609439"
---
# <a name="user_thread-structure"></a><span data-ttu-id="7504a-102">USER_THREAD 結構</span><span class="sxs-lookup"><span data-stu-id="7504a-102">USER_THREAD Structure</span></span>
<span data-ttu-id="7504a-103">提供有關執行緒的詳細資訊給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="7504a-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="7504a-104">如需詳細資訊，請參閱[INotifySource2：： SetNotifyFilter](inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7504a-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7504a-105">語法</span><span class="sxs-lookup"><span data-stu-id="7504a-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="7504a-106">成員</span><span class="sxs-lookup"><span data-stu-id="7504a-106">Members</span></span>  
  
|<span data-ttu-id="7504a-107">成員</span><span class="sxs-lookup"><span data-stu-id="7504a-107">Member</span></span>|<span data-ttu-id="7504a-108">說明</span><span class="sxs-lookup"><span data-stu-id="7504a-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="7504a-109">執行緒緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="7504a-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="7504a-110">執行緒緩衝區的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="7504a-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="7504a-111">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="7504a-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7504a-112">需求</span><span class="sxs-lookup"><span data-stu-id="7504a-112">Requirements</span></span>  
 <span data-ttu-id="7504a-113">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="7504a-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7504a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7504a-114">See also</span></span>

- [<span data-ttu-id="7504a-115">SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="7504a-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="7504a-116">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="7504a-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
