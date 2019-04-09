---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9003482860e554049c39ea9ffed4c52345bfeff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183205"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="613e1-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法</span><span class="sxs-lookup"><span data-stu-id="613e1-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="613e1-103">取得所有合併組件的符號記錄。</span><span class="sxs-lookup"><span data-stu-id="613e1-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="613e1-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="613e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="613e1-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="613e1-106">[in] 要求的符號記錄數目。</span><span class="sxs-lookup"><span data-stu-id="613e1-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="613e1-107">[out] 方法所擷取之符號記錄數的指標。</span><span class="sxs-lookup"><span data-stu-id="613e1-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="613e1-108">陣列的指標[ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="613e1-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="613e1-109">備註</span><span class="sxs-lookup"><span data-stu-id="613e1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="613e1-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="613e1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="613e1-111">需求</span><span class="sxs-lookup"><span data-stu-id="613e1-111">Requirements</span></span>  
 <span data-ttu-id="613e1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="613e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="613e1-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="613e1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="613e1-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="613e1-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="613e1-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="613e1-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="613e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="613e1-116">See also</span></span>

- [<span data-ttu-id="613e1-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="613e1-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="613e1-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="613e1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
