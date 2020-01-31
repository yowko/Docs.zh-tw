---
title: ICorDebugModuleDebugEvent::GetModule 方法
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 4d9eea8fb5c42002763a0ae52a186bf2c1e6d2ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792911"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="1ff62-102">ICorDebugModuleDebugEvent::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="1ff62-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="1ff62-103">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="1ff62-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff62-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ff62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ff62-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ff62-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="1ff62-106">[out] ICorDebugModule 物件的位址指標，這個物件代表剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="1ff62-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ff62-107">備註</span><span class="sxs-lookup"><span data-stu-id="1ff62-107">Remarks</span></span>  
 <span data-ttu-id="1ff62-108">您可以呼叫[GetEventKind](icordebugdebugevent-geteventkind-method.md)方法，以判斷模組是否已載入或卸載。</span><span class="sxs-lookup"><span data-stu-id="1ff62-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ff62-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="1ff62-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ff62-110">需求</span><span class="sxs-lookup"><span data-stu-id="1ff62-110">Requirements</span></span>  
 <span data-ttu-id="1ff62-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ff62-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ff62-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ff62-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ff62-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ff62-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ff62-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ff62-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ff62-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ff62-115">See also</span></span>

- [<span data-ttu-id="1ff62-116">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="1ff62-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="1ff62-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1ff62-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
