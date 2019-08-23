---
title: ICorDebugDataTarget3::GetLoadedModules 方法
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 120b839b2b11c85f42bb1a0ae4701de0dea33879
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912827"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="3f52c-102">ICorDebugDataTarget3::GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="3f52c-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="3f52c-103">取得到目前為止已載入的模組清單。</span><span class="sxs-lookup"><span data-stu-id="3f52c-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f52c-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f52c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f52c-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f52c-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="3f52c-106">[in] 要求該模組資訊的模組數目。</span><span class="sxs-lookup"><span data-stu-id="3f52c-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="3f52c-107">[out] 傳回該模組資訊之模組數目的指標。</span><span class="sxs-lookup"><span data-stu-id="3f52c-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="3f52c-108">脫銷[ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)物件陣列的指標, 提供已載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3f52c-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f52c-109">備註</span><span class="sxs-lookup"><span data-stu-id="3f52c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3f52c-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="3f52c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f52c-111">需求</span><span class="sxs-lookup"><span data-stu-id="3f52c-111">Requirements</span></span>  
 <span data-ttu-id="3f52c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3f52c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f52c-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3f52c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3f52c-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f52c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f52c-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f52c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f52c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f52c-116">See also</span></span>

- [<span data-ttu-id="3f52c-117">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="3f52c-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="3f52c-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3f52c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
