---
title: "CorDebugStateChange 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStateChange
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: caf49621342be0ff85ac3cb56b95bb87f524c3be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="95f17-102">CorDebugStateChange 列舉</span><span class="sxs-lookup"><span data-stu-id="95f17-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="95f17-103">描述依據處理序變更而必須捨棄的快取資料量。</span><span class="sxs-lookup"><span data-stu-id="95f17-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95f17-104">語法</span><span class="sxs-lookup"><span data-stu-id="95f17-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="95f17-105">成員</span><span class="sxs-lookup"><span data-stu-id="95f17-105">Members</span></span>  
  
|<span data-ttu-id="95f17-106">成員</span><span class="sxs-lookup"><span data-stu-id="95f17-106">Member</span></span>|<span data-ttu-id="95f17-107">描述</span><span class="sxs-lookup"><span data-stu-id="95f17-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="95f17-108">處理序透過向前執行已達到新的記憶體狀態。</span><span class="sxs-lookup"><span data-stu-id="95f17-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="95f17-109">指定的處理序記憶體可能與先前的記憶體不同。</span><span class="sxs-lookup"><span data-stu-id="95f17-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95f17-110">備註</span><span class="sxs-lookup"><span data-stu-id="95f17-110">Remarks</span></span>  
 <span data-ttu-id="95f17-111">成員`CorDebugStateChange`列舉型別提供做為引數時偵錯工具呼叫[ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)方法</span><span class="sxs-lookup"><span data-stu-id="95f17-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95f17-112">這個列舉僅適用於 .NET 原生偵錯案例。</span><span class="sxs-lookup"><span data-stu-id="95f17-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95f17-113">需求</span><span class="sxs-lookup"><span data-stu-id="95f17-113">Requirements</span></span>  
 <span data-ttu-id="95f17-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95f17-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95f17-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95f17-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95f17-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95f17-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95f17-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95f17-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f17-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95f17-118">See Also</span></span>  
 [<span data-ttu-id="95f17-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="95f17-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="95f17-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="95f17-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
