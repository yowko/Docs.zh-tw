---
title: COR_DEBUG_STEP_RANGE 結構
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bda8079cff8f5e8fafade03a02c3dfe8798c5ca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740777"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="0c8f8-102">COR_DEBUG_STEP_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="0c8f8-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="0c8f8-103">包含程式碼範圍的位移資訊。</span><span class="sxs-lookup"><span data-stu-id="0c8f8-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="0c8f8-104">此結構由[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0c8f8-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c8f8-105">語法</span><span class="sxs-lookup"><span data-stu-id="0c8f8-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="0c8f8-106">成員</span><span class="sxs-lookup"><span data-stu-id="0c8f8-106">Members</span></span>  
  
|<span data-ttu-id="0c8f8-107">成員</span><span class="sxs-lookup"><span data-stu-id="0c8f8-107">Member</span></span>|<span data-ttu-id="0c8f8-108">描述</span><span class="sxs-lookup"><span data-stu-id="0c8f8-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="0c8f8-109">範圍開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="0c8f8-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="0c8f8-110">範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="0c8f8-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c8f8-111">需求</span><span class="sxs-lookup"><span data-stu-id="0c8f8-111">Requirements</span></span>  
 <span data-ttu-id="0c8f8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c8f8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c8f8-113">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="0c8f8-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="0c8f8-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c8f8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c8f8-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c8f8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8f8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c8f8-116">See also</span></span>

- [<span data-ttu-id="0c8f8-117">StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="0c8f8-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="0c8f8-118">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="0c8f8-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="0c8f8-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="0c8f8-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
