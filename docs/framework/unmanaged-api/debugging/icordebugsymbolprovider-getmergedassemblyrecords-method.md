---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 502e7e0b52bb147b5fe37dcc6e4f6d13d642b6f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417540"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="58db9-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法</span><span class="sxs-lookup"><span data-stu-id="58db9-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="58db9-103">取得所有合併組件的符號記錄。</span><span class="sxs-lookup"><span data-stu-id="58db9-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58db9-104">語法</span><span class="sxs-lookup"><span data-stu-id="58db9-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58db9-105">參數</span><span class="sxs-lookup"><span data-stu-id="58db9-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="58db9-106">[in] 要求的符號記錄數目。</span><span class="sxs-lookup"><span data-stu-id="58db9-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="58db9-107">[out] 方法所擷取之符號記錄數的指標。</span><span class="sxs-lookup"><span data-stu-id="58db9-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="58db9-108">陣列的指標[ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="58db9-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58db9-109">備註</span><span class="sxs-lookup"><span data-stu-id="58db9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58db9-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="58db9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58db9-111">需求</span><span class="sxs-lookup"><span data-stu-id="58db9-111">Requirements</span></span>  
 <span data-ttu-id="58db9-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58db9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58db9-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58db9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58db9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58db9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58db9-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58db9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58db9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58db9-116">See Also</span></span>  
 [<span data-ttu-id="58db9-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="58db9-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="58db9-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="58db9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
