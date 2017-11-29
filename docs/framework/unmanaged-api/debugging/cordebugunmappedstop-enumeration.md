---
title: "CorDebugUnmappedStop 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUnmappedStop
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUnmappedStop
helpviewer_keywords: CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e75c827533a921c4cab31b2e8b0996dffa532fe2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="cbe2d-102">CorDebugUnmappedStop 列舉</span><span class="sxs-lookup"><span data-stu-id="cbe2d-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="cbe2d-103">指定可在步進器執行程式碼時觸發暫止的未對應程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="cbe2d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cbe2d-105">成員</span><span class="sxs-lookup"><span data-stu-id="cbe2d-105">Members</span></span>  
  
|<span data-ttu-id="cbe2d-106">成員</span><span class="sxs-lookup"><span data-stu-id="cbe2d-106">Member</span></span>|<span data-ttu-id="cbe2d-107">說明</span><span class="sxs-lookup"><span data-stu-id="cbe2d-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="cbe2d-108">不會停止任何類型的未對應的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="cbe2d-109">初構程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="cbe2d-110">終解程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="cbe2d-111">沒有對應資訊的程式碼中停止。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="cbe2d-112">停止並不適用於初構、 終解、 否對應資訊或未受管理的類別目錄的未對應程式碼中。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="cbe2d-113">停止在 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-113">Stop in unmanaged code.</span></span> <span data-ttu-id="cbe2d-114">此值為有效只能搭配 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="cbe2d-115">停止所有類型的未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbe2d-116">備註</span><span class="sxs-lookup"><span data-stu-id="cbe2d-116">Remarks</span></span>  
 <span data-ttu-id="cbe2d-117">使用[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)方法來設定旗標，指定在其中將會停止 stepper 未對應的程式碼。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbe2d-118">需求</span><span class="sxs-lookup"><span data-stu-id="cbe2d-118">Requirements</span></span>  
 <span data-ttu-id="cbe2d-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cbe2d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbe2d-120">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbe2d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbe2d-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbe2d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbe2d-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbe2d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe2d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbe2d-123">See Also</span></span>  
 [<span data-ttu-id="cbe2d-124">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="cbe2d-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
