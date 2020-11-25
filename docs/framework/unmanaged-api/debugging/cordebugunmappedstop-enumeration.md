---
title: CorDebugUnmappedStop 列舉
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: e251bf67adcaf2bbd6565eda068d487eb0d70efd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725765"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="5113f-102">CorDebugUnmappedStop 列舉</span><span class="sxs-lookup"><span data-stu-id="5113f-102">CorDebugUnmappedStop Enumeration</span></span>

<span data-ttu-id="5113f-103">指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="5113f-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5113f-104">語法</span><span class="sxs-lookup"><span data-stu-id="5113f-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="5113f-105">成員</span><span class="sxs-lookup"><span data-stu-id="5113f-105">Members</span></span>  
  
|<span data-ttu-id="5113f-106">member</span><span class="sxs-lookup"><span data-stu-id="5113f-106">Member</span></span>|<span data-ttu-id="5113f-107">描述</span><span class="sxs-lookup"><span data-stu-id="5113f-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="5113f-108">請勿在任何未對應的程式碼類型中停止。</span><span class="sxs-lookup"><span data-stu-id="5113f-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="5113f-109">在初構程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="5113f-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="5113f-110">在終解程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="5113f-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="5113f-111">在沒有對應資訊的程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="5113f-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="5113f-112">在未對應的程式碼中停止，但不符合初構、終解、無對應資訊或非受控類別。</span><span class="sxs-lookup"><span data-stu-id="5113f-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="5113f-113">停止非受控碼。</span><span class="sxs-lookup"><span data-stu-id="5113f-113">Stop in unmanaged code.</span></span> <span data-ttu-id="5113f-114">此值僅適用于 interop 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5113f-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="5113f-115">在所有未對應的程式碼類型中停止。</span><span class="sxs-lookup"><span data-stu-id="5113f-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5113f-116">備註</span><span class="sxs-lookup"><span data-stu-id="5113f-116">Remarks</span></span>  

 <span data-ttu-id="5113f-117">您可以使用 [ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) 方法來設定旗標，以指定將停止執行程式的未對應程式碼。</span><span class="sxs-lookup"><span data-stu-id="5113f-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5113f-118">需求</span><span class="sxs-lookup"><span data-stu-id="5113f-118">Requirements</span></span>  

 <span data-ttu-id="5113f-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5113f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5113f-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5113f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5113f-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5113f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5113f-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5113f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5113f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5113f-123">See also</span></span>

- [<span data-ttu-id="5113f-124">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="5113f-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
