---
title: "ICorDebugSymbolProvider::GetStaticFieldSymbols 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3871a74ee2844835c09a6e395fd63536c7442261
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="21a0b-102">ICorDebugSymbolProvider::GetStaticFieldSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="21a0b-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="21a0b-103">取得對應至 TypeSpec 簽章的靜態欄位符號。</span><span class="sxs-lookup"><span data-stu-id="21a0b-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a0b-104">語法</span><span class="sxs-lookup"><span data-stu-id="21a0b-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21a0b-105">參數</span><span class="sxs-lookup"><span data-stu-id="21a0b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="21a0b-106">[in] `typeSig` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="21a0b-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="21a0b-107">[in] 包含 `typespec` 簽章的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="21a0b-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="21a0b-108">[in] 要求的符號數目。</span><span class="sxs-lookup"><span data-stu-id="21a0b-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="21a0b-109">[out] 方法所擷取之符號數的指標。</span><span class="sxs-lookup"><span data-stu-id="21a0b-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="21a0b-110">[out]指標[ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)陣列，其中包含所要求的靜態欄位符號。</span><span class="sxs-lookup"><span data-stu-id="21a0b-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a0b-111">備註</span><span class="sxs-lookup"><span data-stu-id="21a0b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21a0b-112">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="21a0b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a0b-113">需求</span><span class="sxs-lookup"><span data-stu-id="21a0b-113">Requirements</span></span>  
 <span data-ttu-id="21a0b-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21a0b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a0b-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21a0b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21a0b-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21a0b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21a0b-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a0b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a0b-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="21a0b-118">See Also</span></span>  
 [<span data-ttu-id="21a0b-119">GetInstanceFieldSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="21a0b-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)  
 [<span data-ttu-id="21a0b-120">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="21a0b-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="21a0b-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="21a0b-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
