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
ms.openlocfilehash: 57d7c3256d7b52a4e55dbb5bc420b0438983d2f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219677"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="268da-102">COR_DEBUG_STEP_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="268da-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="268da-103">包含程式碼範圍的位移資訊。</span><span class="sxs-lookup"><span data-stu-id="268da-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="268da-104">此結構由[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="268da-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="268da-105">語法</span><span class="sxs-lookup"><span data-stu-id="268da-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="268da-106">成員</span><span class="sxs-lookup"><span data-stu-id="268da-106">Members</span></span>  
  
|<span data-ttu-id="268da-107">成員</span><span class="sxs-lookup"><span data-stu-id="268da-107">Member</span></span>|<span data-ttu-id="268da-108">描述</span><span class="sxs-lookup"><span data-stu-id="268da-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="268da-109">範圍開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="268da-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="268da-110">範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="268da-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="268da-111">需求</span><span class="sxs-lookup"><span data-stu-id="268da-111">Requirements</span></span>  
 <span data-ttu-id="268da-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="268da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="268da-113">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="268da-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="268da-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="268da-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="268da-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="268da-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="268da-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="268da-116">See also</span></span>

- [<span data-ttu-id="268da-117">StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="268da-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="268da-118">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="268da-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="268da-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="268da-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
