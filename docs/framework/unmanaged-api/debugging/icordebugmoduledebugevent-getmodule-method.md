---
title: "ICorDebugModuleDebugEvent::GetModule 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b11ab8991a9f44cf2868474a8a0f6dcc1c3308c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="91381-102">ICorDebugModuleDebugEvent::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="91381-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="91381-103">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="91381-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91381-104">語法</span><span class="sxs-lookup"><span data-stu-id="91381-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91381-105">參數</span><span class="sxs-lookup"><span data-stu-id="91381-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="91381-106">[out]ICorDebugModule 物件代表剛載入或卸載的合併的模組的位址指標。</span><span class="sxs-lookup"><span data-stu-id="91381-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91381-107">備註</span><span class="sxs-lookup"><span data-stu-id="91381-107">Remarks</span></span>  
 <span data-ttu-id="91381-108">您可以呼叫[GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法，以判斷是否載入或卸載模組。</span><span class="sxs-lookup"><span data-stu-id="91381-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91381-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="91381-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91381-110">需求</span><span class="sxs-lookup"><span data-stu-id="91381-110">Requirements</span></span>  
 <span data-ttu-id="91381-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91381-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91381-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91381-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91381-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91381-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91381-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91381-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91381-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="91381-115">See Also</span></span>  
 [<span data-ttu-id="91381-116">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="91381-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 [<span data-ttu-id="91381-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="91381-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
