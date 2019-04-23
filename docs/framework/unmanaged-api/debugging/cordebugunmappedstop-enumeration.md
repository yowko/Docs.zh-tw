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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1cea8adcd12ecb3078e4469e6b018ed49064e0b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175925"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="17276-102">CorDebugUnmappedStop 列舉</span><span class="sxs-lookup"><span data-stu-id="17276-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="17276-103">指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="17276-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17276-104">語法</span><span class="sxs-lookup"><span data-stu-id="17276-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="17276-105">成員</span><span class="sxs-lookup"><span data-stu-id="17276-105">Members</span></span>  
  
|<span data-ttu-id="17276-106">成員</span><span class="sxs-lookup"><span data-stu-id="17276-106">Member</span></span>|<span data-ttu-id="17276-107">描述</span><span class="sxs-lookup"><span data-stu-id="17276-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="17276-108">不會停止任何類型的未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="17276-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="17276-109">停止在初構程式碼中。</span><span class="sxs-lookup"><span data-stu-id="17276-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="17276-110">終解程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="17276-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="17276-111">沒有對應資訊的程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="17276-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="17276-112">停止未對應的程式碼，並不適用於初構、 終解、 沒有對應資訊或未受管理的類別目錄中。</span><span class="sxs-lookup"><span data-stu-id="17276-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="17276-113">停止在 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="17276-113">Stop in unmanaged code.</span></span> <span data-ttu-id="17276-114">此值就有效只能搭配 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="17276-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="17276-115">停止所有類型的未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="17276-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17276-116">備註</span><span class="sxs-lookup"><span data-stu-id="17276-116">Remarks</span></span>  
 <span data-ttu-id="17276-117">使用[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)方法來設定旗標，指定在其中將會停止步進未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="17276-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17276-118">需求</span><span class="sxs-lookup"><span data-stu-id="17276-118">Requirements</span></span>  
 <span data-ttu-id="17276-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17276-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17276-120">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17276-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17276-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17276-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17276-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17276-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17276-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17276-123">See also</span></span>

- [<span data-ttu-id="17276-124">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="17276-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
