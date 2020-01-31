---
title: ICorDebugDataTarget3::GetLoadedModules 方法
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: d4c22146422085daa4dc9d90ae5b3735a12500c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793560"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="7cdc8-102">ICorDebugDataTarget3::GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="7cdc8-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="7cdc8-103">取得到目前為止已載入的模組清單。</span><span class="sxs-lookup"><span data-stu-id="7cdc8-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cdc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="7cdc8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cdc8-105">參數</span><span class="sxs-lookup"><span data-stu-id="7cdc8-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="7cdc8-106">[in] 要求該模組資訊的模組數目。</span><span class="sxs-lookup"><span data-stu-id="7cdc8-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="7cdc8-107">[out] 傳回該模組資訊之模組數目的指標。</span><span class="sxs-lookup"><span data-stu-id="7cdc8-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="7cdc8-108">脫銷[ICorDebugLoadedModule](icordebugloadedmodule-interface.md)物件陣列的指標，提供已載入模組的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7cdc8-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cdc8-109">備註</span><span class="sxs-lookup"><span data-stu-id="7cdc8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cdc8-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="7cdc8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cdc8-111">需求</span><span class="sxs-lookup"><span data-stu-id="7cdc8-111">Requirements</span></span>  
 <span data-ttu-id="7cdc8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7cdc8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cdc8-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cdc8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cdc8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cdc8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cdc8-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cdc8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdc8-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="7cdc8-116">See also</span></span>

- [<span data-ttu-id="7cdc8-117">ICorDebugDataTarget3 介面</span><span class="sxs-lookup"><span data-stu-id="7cdc8-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="7cdc8-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7cdc8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
