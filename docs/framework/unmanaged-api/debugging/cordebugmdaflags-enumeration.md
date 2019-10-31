---
title: CorDebugMDAFlags 列舉
ms.date: 03/30/2017
api_name:
- CorDebugMDAFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMDAFlags
helpviewer_keywords:
- CorDebugMDAFlags enumeration [.NET Framework debugging]
ms.assetid: 7c0c92fe-8bd2-477f-b307-aca0143732ca
topic_type:
- apiref
ms.openlocfilehash: c7af194351290ad937e40a2fc8b960c2c242629c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132801"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="c1735-102">CorDebugMDAFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="c1735-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="c1735-103">指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="c1735-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1735-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1735-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c1735-105">Members</span><span class="sxs-lookup"><span data-stu-id="c1735-105">Members</span></span>  
  
|<span data-ttu-id="c1735-106">成員</span><span class="sxs-lookup"><span data-stu-id="c1735-106">Member</span></span>|<span data-ttu-id="c1735-107">描述</span><span class="sxs-lookup"><span data-stu-id="c1735-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="c1735-108">引發 MDA 的執行緒在引發 MDA 之後已經落後。</span><span class="sxs-lookup"><span data-stu-id="c1735-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1735-109">備註</span><span class="sxs-lookup"><span data-stu-id="c1735-109">Remarks</span></span>  
 <span data-ttu-id="c1735-110">當呼叫堆疊不再說明最初引發 MDA 的位置時，會將執行緒視為已*落後*。</span><span class="sxs-lookup"><span data-stu-id="c1735-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="c1735-111">這是在結束時，執行緒執行無效作業所產生的異常情況。</span><span class="sxs-lookup"><span data-stu-id="c1735-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1735-112">需求</span><span class="sxs-lookup"><span data-stu-id="c1735-112">Requirements</span></span>  
 <span data-ttu-id="c1735-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1735-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1735-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1735-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1735-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1735-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1735-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1735-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1735-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1735-117">See also</span></span>

- [<span data-ttu-id="c1735-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="c1735-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
