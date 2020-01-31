---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6a537a88bd4ab666eff8b5dda994da96bfcc5e52
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791617"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="e48f5-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法</span><span class="sxs-lookup"><span data-stu-id="e48f5-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="e48f5-103">取得所有合併組件的符號記錄。</span><span class="sxs-lookup"><span data-stu-id="e48f5-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e48f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="e48f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e48f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="e48f5-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="e48f5-106">[in] 要求的符號記錄數目。</span><span class="sxs-lookup"><span data-stu-id="e48f5-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="e48f5-107">[out] 方法所擷取之符號記錄數的指標。</span><span class="sxs-lookup"><span data-stu-id="e48f5-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="e48f5-108">[ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)物件陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="e48f5-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e48f5-109">備註</span><span class="sxs-lookup"><span data-stu-id="e48f5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e48f5-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e48f5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e48f5-111">需求</span><span class="sxs-lookup"><span data-stu-id="e48f5-111">Requirements</span></span>  
 <span data-ttu-id="e48f5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e48f5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e48f5-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e48f5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e48f5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e48f5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e48f5-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e48f5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e48f5-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e48f5-116">See also</span></span>

- [<span data-ttu-id="e48f5-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="e48f5-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e48f5-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e48f5-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
