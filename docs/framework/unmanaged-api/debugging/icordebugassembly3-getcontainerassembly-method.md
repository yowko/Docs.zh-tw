---
title: "ICorDebugAssembly3::GetContainerAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c7bf800c75083fa81ab2bb14d4ad13f08050dc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="ce2ef-102">ICorDebugAssembly3::GetContainerAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="ce2ef-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="ce2ef-103">傳回這個 `ICorDebugAssembly3` 物件的容器組件。</span><span class="sxs-lookup"><span data-stu-id="ce2ef-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce2ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce2ef-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce2ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce2ef-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="ce2ef-106">ICorDebugAssembly 物件，代表容器組件的位址指標或**null**如果方法呼叫失敗。</span><span class="sxs-lookup"><span data-stu-id="ce2ef-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce2ef-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="ce2ef-107">Return Value</span></span>  
 <span data-ttu-id="ce2ef-108">`S_OK`如果方法呼叫成功。否則， `S_FALSE`，和`ppAssembly`是**null**。</span><span class="sxs-lookup"><span data-stu-id="ce2ef-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce2ef-109">備註</span><span class="sxs-lookup"><span data-stu-id="ce2ef-109">Remarks</span></span>  
 <span data-ttu-id="ce2ef-110">如果這個組件與其他組件已合併到單一容器組件內，這個方法會傳回該容器組件。</span><span class="sxs-lookup"><span data-stu-id="ce2ef-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="ce2ef-111">如需詳細資訊和術語，請參閱[icordebugprocess6:: Enablevirtualmodulesplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)主題。</span><span class="sxs-lookup"><span data-stu-id="ce2ef-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce2ef-112">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="ce2ef-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce2ef-113">需求</span><span class="sxs-lookup"><span data-stu-id="ce2ef-113">Requirements</span></span>  
 <span data-ttu-id="ce2ef-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce2ef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce2ef-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce2ef-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce2ef-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce2ef-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce2ef-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce2ef-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce2ef-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce2ef-118">See Also</span></span>  
 [<span data-ttu-id="ce2ef-119">ICorDebugAssembly3 介面</span><span class="sxs-lookup"><span data-stu-id="ce2ef-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="ce2ef-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ce2ef-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
