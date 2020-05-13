---
title: ICorDebugModuleDebugEvent::GetModule 方法
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 1df71ddbf1ee76cc8202d8f9e263b9d95b4aaa09
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213357"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="6637e-102">ICorDebugModuleDebugEvent::GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="6637e-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="6637e-103">取得剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="6637e-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6637e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6637e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6637e-105">參數</span><span class="sxs-lookup"><span data-stu-id="6637e-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="6637e-106">[out] ICorDebugModule 物件的位址指標，這個物件代表剛載入或卸載的合併模組。</span><span class="sxs-lookup"><span data-stu-id="6637e-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6637e-107">備註</span><span class="sxs-lookup"><span data-stu-id="6637e-107">Remarks</span></span>  
 <span data-ttu-id="6637e-108">您可以呼叫[GetEventKind](icordebugdebugevent-geteventkind-method.md)方法，以判斷模組是否已載入或卸載。</span><span class="sxs-lookup"><span data-stu-id="6637e-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6637e-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6637e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6637e-110">需求</span><span class="sxs-lookup"><span data-stu-id="6637e-110">Requirements</span></span>  
 <span data-ttu-id="6637e-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6637e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6637e-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6637e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6637e-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6637e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6637e-114">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6637e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6637e-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="6637e-115">See also</span></span>

- [<span data-ttu-id="6637e-116">ICorDebugModuleDebugEvent 介面</span><span class="sxs-lookup"><span data-stu-id="6637e-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="6637e-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6637e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
