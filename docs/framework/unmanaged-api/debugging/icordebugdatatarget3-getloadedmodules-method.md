---
title: "ICorDebugDataTarget3::GetLoadedModules 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3db6449abee4eed4a8e5d6c691834c52dc0717e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="bbff1-102">ICorDebugDataTarget3::GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="bbff1-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="bbff1-103">取得到目前為止已載入的模組清單。</span><span class="sxs-lookup"><span data-stu-id="bbff1-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbff1-104">語法</span><span class="sxs-lookup"><span data-stu-id="bbff1-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbff1-105">參數</span><span class="sxs-lookup"><span data-stu-id="bbff1-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="bbff1-106">[in] 要求該模組資訊的模組數目。</span><span class="sxs-lookup"><span data-stu-id="bbff1-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="bbff1-107">[out] 傳回該模組資訊之模組數目的指標。</span><span class="sxs-lookup"><span data-stu-id="bbff1-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="bbff1-108">[out]陣列的指標[ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)提供下列資訊的物件載入的模組。</span><span class="sxs-lookup"><span data-stu-id="bbff1-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbff1-109">備註</span><span class="sxs-lookup"><span data-stu-id="bbff1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbff1-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="bbff1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbff1-111">需求</span><span class="sxs-lookup"><span data-stu-id="bbff1-111">Requirements</span></span>  
 <span data-ttu-id="bbff1-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bbff1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbff1-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbff1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbff1-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbff1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbff1-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbff1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbff1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="bbff1-116">See Also</span></span>  
 [<span data-ttu-id="bbff1-117">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="bbff1-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [<span data-ttu-id="bbff1-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bbff1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
