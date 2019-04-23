---
title: ICorDebugDataTarget3::GetLoadedModules 方法
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 464fd9ac44d6ba5717dbc4ecfbe03b6e6ad52276
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138654"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="6425a-102">ICorDebugDataTarget3::GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="6425a-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="6425a-103">取得到目前為止已載入的模組清單。</span><span class="sxs-lookup"><span data-stu-id="6425a-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6425a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6425a-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6425a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6425a-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="6425a-106">[in] 要求該模組資訊的模組數目。</span><span class="sxs-lookup"><span data-stu-id="6425a-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="6425a-107">[out] 傳回該模組資訊之模組數目的指標。</span><span class="sxs-lookup"><span data-stu-id="6425a-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="6425a-108">[out]陣列的指標[ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)提供相關資訊的物件載入的模組。</span><span class="sxs-lookup"><span data-stu-id="6425a-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6425a-109">備註</span><span class="sxs-lookup"><span data-stu-id="6425a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6425a-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6425a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6425a-111">需求</span><span class="sxs-lookup"><span data-stu-id="6425a-111">Requirements</span></span>  
 <span data-ttu-id="6425a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6425a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6425a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6425a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6425a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6425a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6425a-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6425a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6425a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6425a-116">See also</span></span>

- [<span data-ttu-id="6425a-117">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="6425a-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="6425a-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6425a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
