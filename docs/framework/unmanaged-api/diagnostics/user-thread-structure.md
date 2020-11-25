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
ms.openlocfilehash: 409651aa69e957418ad46f61e1bd57add0eb10a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722891"
---
# <a name="user_thread-structure"></a><span data-ttu-id="70125-102">USER_THREAD 結構</span><span class="sxs-lookup"><span data-stu-id="70125-102">USER_THREAD Structure</span></span>

<span data-ttu-id="70125-103">提供有關執行緒的資訊給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="70125-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="70125-104">如需詳細資訊，請參閱 [INotifySource2：： SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="70125-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70125-105">語法</span><span class="sxs-lookup"><span data-stu-id="70125-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="70125-106">成員</span><span class="sxs-lookup"><span data-stu-id="70125-106">Members</span></span>  
  
|<span data-ttu-id="70125-107">member</span><span class="sxs-lookup"><span data-stu-id="70125-107">Member</span></span>|<span data-ttu-id="70125-108">描述</span><span class="sxs-lookup"><span data-stu-id="70125-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="70125-109">執行緒緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="70125-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="70125-110">執行緒緩衝區的長度（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="70125-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="70125-111">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="70125-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70125-112">需求</span><span class="sxs-lookup"><span data-stu-id="70125-112">Requirements</span></span>  

 <span data-ttu-id="70125-113">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="70125-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70125-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70125-114">See also</span></span>

- [<span data-ttu-id="70125-115">SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="70125-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="70125-116">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="70125-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
