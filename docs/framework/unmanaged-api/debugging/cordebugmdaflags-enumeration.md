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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 732523935eec62bffbc15705bc93c97f14c90064
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148417"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="c593c-102">CorDebugMDAFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="c593c-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="c593c-103">指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="c593c-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c593c-104">語法</span><span class="sxs-lookup"><span data-stu-id="c593c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="c593c-105">成員</span><span class="sxs-lookup"><span data-stu-id="c593c-105">Members</span></span>  
  
|<span data-ttu-id="c593c-106">成員</span><span class="sxs-lookup"><span data-stu-id="c593c-106">Member</span></span>|<span data-ttu-id="c593c-107">描述</span><span class="sxs-lookup"><span data-stu-id="c593c-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="c593c-108">因為 MDA 引發的進度落後的執行緒引發之 MDA。</span><span class="sxs-lookup"><span data-stu-id="c593c-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c593c-109">備註</span><span class="sxs-lookup"><span data-stu-id="c593c-109">Remarks</span></span>  
 <span data-ttu-id="c593c-110">呼叫堆疊不會再描述最初發生 MDA，當執行緒被視為具有*順延*。</span><span class="sxs-lookup"><span data-stu-id="c593c-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="c593c-111">這是作業的不尋常的情況下，帶來了無效，在結束時的執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="c593c-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c593c-112">需求</span><span class="sxs-lookup"><span data-stu-id="c593c-112">Requirements</span></span>  
 <span data-ttu-id="c593c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c593c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c593c-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c593c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c593c-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c593c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c593c-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c593c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c593c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c593c-117">See also</span></span>

- [<span data-ttu-id="c593c-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="c593c-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
