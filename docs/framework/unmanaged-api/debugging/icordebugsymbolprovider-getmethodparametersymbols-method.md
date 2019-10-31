---
title: ICorDebugSymbolProvider：： GetMethodParameterSymbols 方法
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: 1f7da156e5a164dc753e2283bc7ab24d18983173
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138848"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="4e5f3-102">ICorDebugSymbolProvider：： GetMethodParameterSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="4e5f3-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="4e5f3-103">提供方法的相對虛擬位址 (RVA)，取得該方法的參數符號。</span><span class="sxs-lookup"><span data-stu-id="4e5f3-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e5f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e5f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e5f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e5f3-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="4e5f3-106">[in] 方法的原生相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="4e5f3-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="4e5f3-107">[in] 要求的本機符號數目。</span><span class="sxs-lookup"><span data-stu-id="4e5f3-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="4e5f3-108">[out] 方法所擷取之符號數的指標。</span><span class="sxs-lookup"><span data-stu-id="4e5f3-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="4e5f3-109">脫銷[ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)陣列的指標，其中包含方法的本機符號。</span><span class="sxs-lookup"><span data-stu-id="4e5f3-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e5f3-110">備註</span><span class="sxs-lookup"><span data-stu-id="4e5f3-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e5f3-111">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="4e5f3-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e5f3-112">需求</span><span class="sxs-lookup"><span data-stu-id="4e5f3-112">Requirements</span></span>  
 <span data-ttu-id="4e5f3-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e5f3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e5f3-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e5f3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e5f3-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e5f3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e5f3-116">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e5f3-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e5f3-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e5f3-117">See also</span></span>

- [<span data-ttu-id="4e5f3-118">GetMethodLocalSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="4e5f3-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="4e5f3-119">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="4e5f3-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="4e5f3-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4e5f3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
