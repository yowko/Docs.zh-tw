---
title: ICorDebugModuleDebugEvent::GetModule 方法
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c0cc1305f47f03c8c9b35bab5c980cb23d1b157
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138433"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="a278a-102">ICorDebugModuleDebugEvent::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="a278a-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="a278a-103">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="a278a-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a278a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a278a-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a278a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a278a-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="a278a-106">[out]ICorDebugModule 物件，代表剛載入或卸載的合併的模組的位址指標。</span><span class="sxs-lookup"><span data-stu-id="a278a-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a278a-107">備註</span><span class="sxs-lookup"><span data-stu-id="a278a-107">Remarks</span></span>  
 <span data-ttu-id="a278a-108">您可以呼叫[GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法，以判斷是否載入或卸載模組。</span><span class="sxs-lookup"><span data-stu-id="a278a-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a278a-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="a278a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a278a-110">需求</span><span class="sxs-lookup"><span data-stu-id="a278a-110">Requirements</span></span>  
 <span data-ttu-id="a278a-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a278a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a278a-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a278a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a278a-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a278a-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a278a-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="a278a-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a278a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a278a-115">See also</span></span>

- [<span data-ttu-id="a278a-116">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="a278a-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="a278a-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a278a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
