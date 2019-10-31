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
ms.openlocfilehash: cc02f63808b1929b93777c8bbc67c47000b0b424
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132752"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="2a625-102">CorDebugUnmappedStop 列舉</span><span class="sxs-lookup"><span data-stu-id="2a625-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="2a625-103">指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="2a625-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a625-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a625-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2a625-105">Members</span><span class="sxs-lookup"><span data-stu-id="2a625-105">Members</span></span>  
  
|<span data-ttu-id="2a625-106">成員</span><span class="sxs-lookup"><span data-stu-id="2a625-106">Member</span></span>|<span data-ttu-id="2a625-107">描述</span><span class="sxs-lookup"><span data-stu-id="2a625-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="2a625-108">請勿在任何類型的未對應程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="2a625-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="2a625-109">在初構程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="2a625-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="2a625-110">停止結束程式碼。</span><span class="sxs-lookup"><span data-stu-id="2a625-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="2a625-111">在沒有對應資訊的程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="2a625-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="2a625-112">在未對應的程式碼中停止，而不符合初構、終解、無對應資訊或非受控類別。</span><span class="sxs-lookup"><span data-stu-id="2a625-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="2a625-113">在未受管理的程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="2a625-113">Stop in unmanaged code.</span></span> <span data-ttu-id="2a625-114">此值僅適用于 interop 調試。</span><span class="sxs-lookup"><span data-stu-id="2a625-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="2a625-115">停止所有類型的未對應程式碼。</span><span class="sxs-lookup"><span data-stu-id="2a625-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a625-116">備註</span><span class="sxs-lookup"><span data-stu-id="2a625-116">Remarks</span></span>  
 <span data-ttu-id="2a625-117">使用[ICorDebugStepper：： SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)方法來設定旗標，以指定分檔器將停止的未對應程式碼。</span><span class="sxs-lookup"><span data-stu-id="2a625-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a625-118">需求</span><span class="sxs-lookup"><span data-stu-id="2a625-118">Requirements</span></span>  
 <span data-ttu-id="2a625-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a625-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a625-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a625-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a625-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a625-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a625-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a625-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a625-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a625-123">See also</span></span>

- [<span data-ttu-id="2a625-124">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="2a625-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
