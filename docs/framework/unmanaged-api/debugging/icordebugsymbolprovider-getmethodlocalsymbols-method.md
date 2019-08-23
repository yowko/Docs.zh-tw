---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols 方法
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24671c371ae8a0a9f3c7ca650a71298c69e2fae1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955667"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="2a58c-102">ICorDebugSymbolProvider::GetMethodLocalSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="2a58c-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="2a58c-103">提供方法的相對虛擬位址 (RVA)，取得該方法的本機符號。</span><span class="sxs-lookup"><span data-stu-id="2a58c-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a58c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a58c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a58c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a58c-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="2a58c-106">[in] 方法的原生相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="2a58c-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="2a58c-107">[in] 要求的本機符號數目。</span><span class="sxs-lookup"><span data-stu-id="2a58c-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2a58c-108">[out] 方法所擷取之符號數的指標。</span><span class="sxs-lookup"><span data-stu-id="2a58c-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2a58c-109">脫銷[ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)陣列的指標, 其中包含方法的本機符號。</span><span class="sxs-lookup"><span data-stu-id="2a58c-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a58c-110">備註</span><span class="sxs-lookup"><span data-stu-id="2a58c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a58c-111">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="2a58c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a58c-112">需求</span><span class="sxs-lookup"><span data-stu-id="2a58c-112">Requirements</span></span>  
 <span data-ttu-id="2a58c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a58c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a58c-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a58c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a58c-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a58c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a58c-116">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a58c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a58c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a58c-117">See also</span></span>

- [<span data-ttu-id="2a58c-118">GetMethodParameterSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="2a58c-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="2a58c-119">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="2a58c-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2a58c-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2a58c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
