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
ms.openlocfilehash: bf9f7f3d3419efc9e1dc7d75fc7272432c0cf5d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739688"
---
# <a name="cordebugmdaflags-enumeration"></a><span data-ttu-id="26253-102">CorDebugMDAFlags 列舉</span><span class="sxs-lookup"><span data-stu-id="26253-102">CorDebugMDAFlags Enumeration</span></span>
<span data-ttu-id="26253-103">指定會引發 Managed 偵錯助理 (MDA) 的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="26253-103">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26253-104">語法</span><span class="sxs-lookup"><span data-stu-id="26253-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMDAFlags {  
    MDA_FLAG_SLIP = 0x2  
} CorDebugMDAFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="26253-105">成員</span><span class="sxs-lookup"><span data-stu-id="26253-105">Members</span></span>  
  
|<span data-ttu-id="26253-106">成員</span><span class="sxs-lookup"><span data-stu-id="26253-106">Member</span></span>|<span data-ttu-id="26253-107">說明</span><span class="sxs-lookup"><span data-stu-id="26253-107">Description</span></span>|  
|------------|-----------------|  
|`MDA_FLAG_SLIP`|<span data-ttu-id="26253-108">因為 MDA 引發的進度落後的執行緒引發之 MDA。</span><span class="sxs-lookup"><span data-stu-id="26253-108">The thread on which the MDA was fired has slipped since the MDA was fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26253-109">備註</span><span class="sxs-lookup"><span data-stu-id="26253-109">Remarks</span></span>  
 <span data-ttu-id="26253-110">呼叫堆疊不會再描述最初發生 MDA，當執行緒被視為具有*順延*。</span><span class="sxs-lookup"><span data-stu-id="26253-110">When the call stack no longer describes where the MDA was originally raised, the thread is considered to have *slipped*.</span></span> <span data-ttu-id="26253-111">這是作業的不尋常的情況下，帶來了無效，在結束時的執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="26253-111">This is an unusual circumstance brought about by the thread's execution of an invalid operation upon exiting.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26253-112">需求</span><span class="sxs-lookup"><span data-stu-id="26253-112">Requirements</span></span>  
 <span data-ttu-id="26253-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="26253-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26253-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26253-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26253-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26253-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26253-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26253-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26253-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26253-117">See also</span></span>

- [<span data-ttu-id="26253-118">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="26253-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
