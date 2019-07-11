---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols 方法
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9379a335130242918f6fe200eeda5e4c262fd020
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771296"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="8413f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="8413f-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="8413f-103">取得對應至 TypeSpec 簽章的靜態欄位符號。</span><span class="sxs-lookup"><span data-stu-id="8413f-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8413f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8413f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8413f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8413f-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="8413f-106">[in] `typeSig` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="8413f-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="8413f-107">[in] 包含 `typespec` 簽章的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="8413f-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="8413f-108">[in] 要求的符號數目。</span><span class="sxs-lookup"><span data-stu-id="8413f-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="8413f-109">[out] 方法所擷取之符號數的指標。</span><span class="sxs-lookup"><span data-stu-id="8413f-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="8413f-110">[out]指標[ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)陣列，其中包含所要求的靜態欄位符號。</span><span class="sxs-lookup"><span data-stu-id="8413f-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8413f-111">備註</span><span class="sxs-lookup"><span data-stu-id="8413f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8413f-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8413f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8413f-113">需求</span><span class="sxs-lookup"><span data-stu-id="8413f-113">Requirements</span></span>  
 <span data-ttu-id="8413f-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8413f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8413f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8413f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8413f-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8413f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8413f-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8413f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8413f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8413f-118">See also</span></span>

- [<span data-ttu-id="8413f-119">GetInstanceFieldSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="8413f-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="8413f-120">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="8413f-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8413f-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8413f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
