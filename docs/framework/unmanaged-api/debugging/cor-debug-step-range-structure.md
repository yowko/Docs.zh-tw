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
ms.openlocfilehash: cd85ba2e6a907ff9546614e02b4da5f45e74b924
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726635"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="a9b6e-102">COR_DEBUG_STEP_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="a9b6e-102">COR_DEBUG_STEP_RANGE Structure</span></span>

<span data-ttu-id="a9b6e-103">包含程式碼範圍的位移資訊。</span><span class="sxs-lookup"><span data-stu-id="a9b6e-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="a9b6e-104">此結構是由 [ICorDebugStepper：： StepRange](icordebugstepper-steprange-method.md) 方法所使用。</span><span class="sxs-lookup"><span data-stu-id="a9b6e-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b6e-105">語法</span><span class="sxs-lookup"><span data-stu-id="a9b6e-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="a9b6e-106">成員</span><span class="sxs-lookup"><span data-stu-id="a9b6e-106">Members</span></span>  
  
|<span data-ttu-id="a9b6e-107">member</span><span class="sxs-lookup"><span data-stu-id="a9b6e-107">Member</span></span>|<span data-ttu-id="a9b6e-108">描述</span><span class="sxs-lookup"><span data-stu-id="a9b6e-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="a9b6e-109">範圍開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="a9b6e-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="a9b6e-110">範圍結尾的位移。</span><span class="sxs-lookup"><span data-stu-id="a9b6e-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a9b6e-111">需求</span><span class="sxs-lookup"><span data-stu-id="a9b6e-111">Requirements</span></span>  

 <span data-ttu-id="a9b6e-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9b6e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9b6e-113">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="a9b6e-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a9b6e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9b6e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9b6e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9b6e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b6e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9b6e-116">See also</span></span>

- [<span data-ttu-id="a9b6e-117">StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="a9b6e-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="a9b6e-118">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="a9b6e-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a9b6e-119">偵錯</span><span class="sxs-lookup"><span data-stu-id="a9b6e-119">Debugging</span></span>](index.md)
