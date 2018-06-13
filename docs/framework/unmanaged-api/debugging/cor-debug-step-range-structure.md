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
ms.openlocfilehash: d5809221f2f31bc725c6a62fa5f8f91822f1c157
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407222"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="3a603-102">COR_DEBUG_STEP_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="3a603-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="3a603-103">包含程式碼範圍的位移資訊。</span><span class="sxs-lookup"><span data-stu-id="3a603-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="3a603-104">這個結構由[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3a603-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a603-105">語法</span><span class="sxs-lookup"><span data-stu-id="3a603-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="3a603-106">成員</span><span class="sxs-lookup"><span data-stu-id="3a603-106">Members</span></span>  
  
|<span data-ttu-id="3a603-107">成員</span><span class="sxs-lookup"><span data-stu-id="3a603-107">Member</span></span>|<span data-ttu-id="3a603-108">描述</span><span class="sxs-lookup"><span data-stu-id="3a603-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="3a603-109">範圍開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="3a603-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="3a603-110">範圍結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="3a603-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a603-111">需求</span><span class="sxs-lookup"><span data-stu-id="3a603-111">Requirements</span></span>  
 <span data-ttu-id="3a603-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a603-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a603-113">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="3a603-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="3a603-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a603-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a603-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a603-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a603-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a603-116">See Also</span></span>  
 [<span data-ttu-id="3a603-117">StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="3a603-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)  
 [<span data-ttu-id="3a603-118">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="3a603-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="3a603-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="3a603-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
