---
title: ICorDebugModuleDebugEvent::GetModule 方法
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ad20bdee5fee83b62d5da7f52c607835055616f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672327"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="1c218-102">ICorDebugModuleDebugEvent::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="1c218-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="1c218-103">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="1c218-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c218-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c218-104">Syntax</span></span>  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c218-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c218-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="1c218-106">[out]ICorDebugModule 物件，代表剛載入或卸載的合併的模組的位址指標。</span><span class="sxs-lookup"><span data-stu-id="1c218-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c218-107">備註</span><span class="sxs-lookup"><span data-stu-id="1c218-107">Remarks</span></span>  
 <span data-ttu-id="1c218-108">您可以呼叫[GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)方法，以判斷是否載入或卸載模組。</span><span class="sxs-lookup"><span data-stu-id="1c218-108">You can call the [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c218-109">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="1c218-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c218-110">需求</span><span class="sxs-lookup"><span data-stu-id="1c218-110">Requirements</span></span>  
 <span data-ttu-id="1c218-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c218-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c218-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c218-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c218-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c218-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c218-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c218-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c218-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c218-115">See also</span></span>
- [<span data-ttu-id="1c218-116">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="1c218-116">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="1c218-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1c218-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
