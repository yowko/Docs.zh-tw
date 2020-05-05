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
ms.openlocfilehash: 772f1f0dee260ad3752b2f89e5fbe0d6bc27b87b
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795647"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="098bf-102">CorDebugUnmappedStop 列舉</span><span class="sxs-lookup"><span data-stu-id="098bf-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="098bf-103">指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="098bf-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="098bf-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="098bf-105">成員</span><span class="sxs-lookup"><span data-stu-id="098bf-105">Members</span></span>  
  
|<span data-ttu-id="098bf-106">member</span><span class="sxs-lookup"><span data-stu-id="098bf-106">Member</span></span>|<span data-ttu-id="098bf-107">說明</span><span class="sxs-lookup"><span data-stu-id="098bf-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="098bf-108">請勿在任何類型的未對應程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="098bf-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="098bf-109">在初構程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="098bf-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="098bf-110">停止結束程式碼。</span><span class="sxs-lookup"><span data-stu-id="098bf-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="098bf-111">在沒有對應資訊的程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="098bf-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="098bf-112">在未對應的程式碼中停止，而不符合初構、終解、無對應資訊或非受控類別。</span><span class="sxs-lookup"><span data-stu-id="098bf-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="098bf-113">在未受管理的程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="098bf-113">Stop in unmanaged code.</span></span> <span data-ttu-id="098bf-114">此值僅適用于 interop 調試。</span><span class="sxs-lookup"><span data-stu-id="098bf-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="098bf-115">停止所有類型的未對應程式碼。</span><span class="sxs-lookup"><span data-stu-id="098bf-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="098bf-116">備註</span><span class="sxs-lookup"><span data-stu-id="098bf-116">Remarks</span></span>  
 <span data-ttu-id="098bf-117">使用[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)方法來設定旗標，以指定分檔器將停止的未對應程式碼。</span><span class="sxs-lookup"><span data-stu-id="098bf-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="098bf-118">需求</span><span class="sxs-lookup"><span data-stu-id="098bf-118">Requirements</span></span>  
 <span data-ttu-id="098bf-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="098bf-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="098bf-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="098bf-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="098bf-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="098bf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="098bf-122">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="098bf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098bf-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="098bf-123">See also</span></span>

- [<span data-ttu-id="098bf-124">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="098bf-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
