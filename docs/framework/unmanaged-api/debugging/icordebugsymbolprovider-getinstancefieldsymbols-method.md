---
title: 'Icordebugsymbolprovider:: Getinstancefieldsymbols 方法'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea9afdd2c032e99d7feee6b2935161c70c56787
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187690"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="4f30d-102">Icordebugsymbolprovider:: Getinstancefieldsymbols 方法</span><span class="sxs-lookup"><span data-stu-id="4f30d-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="4f30d-103">取得對應 TypeSpec 簽章的執行個體欄位符號。</span><span class="sxs-lookup"><span data-stu-id="4f30d-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f30d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f30d-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f30d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f30d-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="4f30d-106">[in] `typeSig` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="4f30d-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="4f30d-107">[in] 包含 `typespec` 簽章的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="4f30d-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="4f30d-108">[in] 要求的符號數目。</span><span class="sxs-lookup"><span data-stu-id="4f30d-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="4f30d-109">[out] 方法所擷取之符號數的指標。</span><span class="sxs-lookup"><span data-stu-id="4f30d-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="4f30d-110">[out]指標[ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)陣列，其中包含所要求的執行個體欄位符號。</span><span class="sxs-lookup"><span data-stu-id="4f30d-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f30d-111">備註</span><span class="sxs-lookup"><span data-stu-id="4f30d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f30d-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="4f30d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f30d-113">需求</span><span class="sxs-lookup"><span data-stu-id="4f30d-113">Requirements</span></span>  
 <span data-ttu-id="4f30d-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f30d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f30d-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f30d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f30d-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f30d-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="4f30d-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="4f30d-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4f30d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f30d-118">See also</span></span>

- [<span data-ttu-id="4f30d-119">GetStaticFieldSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="4f30d-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="4f30d-120">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="4f30d-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4f30d-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4f30d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
