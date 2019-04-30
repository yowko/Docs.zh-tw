---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9003482860e554049c39ea9ffed4c52345bfeff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953305"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="dc53a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords 方法</span><span class="sxs-lookup"><span data-stu-id="dc53a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="dc53a-103">取得所有合併組件的符號記錄。</span><span class="sxs-lookup"><span data-stu-id="dc53a-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc53a-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc53a-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc53a-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc53a-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="dc53a-106">[in] 要求的符號記錄數目。</span><span class="sxs-lookup"><span data-stu-id="dc53a-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="dc53a-107">[out] 方法所擷取之符號記錄數的指標。</span><span class="sxs-lookup"><span data-stu-id="dc53a-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="dc53a-108">陣列的指標[ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)物件。</span><span class="sxs-lookup"><span data-stu-id="dc53a-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc53a-109">備註</span><span class="sxs-lookup"><span data-stu-id="dc53a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc53a-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="dc53a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc53a-111">需求</span><span class="sxs-lookup"><span data-stu-id="dc53a-111">Requirements</span></span>  
 <span data-ttu-id="dc53a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc53a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc53a-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc53a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc53a-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc53a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc53a-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc53a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc53a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc53a-116">See also</span></span>

- [<span data-ttu-id="dc53a-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="dc53a-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="dc53a-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="dc53a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
