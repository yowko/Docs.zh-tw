---
title: 'Icordebugsymbolprovider:: Gettypeprops 方法'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f9867dbdc244ed22948dbe9a07a7ea06292d6a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079080"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="b23e0-102">Icordebugsymbolprovider:: Gettypeprops 方法</span><span class="sxs-lookup"><span data-stu-id="b23e0-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="b23e0-103">根據 vtable 中指定的相對虛擬位址 (RVA)，傳回類型之屬性的相關資訊，例如其泛型參數的簽章數目。</span><span class="sxs-lookup"><span data-stu-id="b23e0-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b23e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="b23e0-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b23e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="b23e0-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="b23e0-106">[in] vtable 中的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="b23e0-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="b23e0-107">[in] `signature` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="b23e0-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="b23e0-108">請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="b23e0-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="b23e0-109">[out] [out] 所傳回 `signature` 陣列的大小指標。</span><span class="sxs-lookup"><span data-stu-id="b23e0-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="b23e0-110">[out] 保留所有泛型參數之 TypeSpec 簽章的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b23e0-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b23e0-111">備註</span><span class="sxs-lookup"><span data-stu-id="b23e0-111">Remarks</span></span>  
 <span data-ttu-id="b23e0-112">若要取得類型的所需的大小`signature`陣列中，設定`cbSignature`引數為 0 並`signature`來**null**。</span><span class="sxs-lookup"><span data-stu-id="b23e0-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="b23e0-113">當這個方法傳回時，`pcbSignature` 會包含 `signature` 陣列所需的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b23e0-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b23e0-114">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="b23e0-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b23e0-115">需求</span><span class="sxs-lookup"><span data-stu-id="b23e0-115">Requirements</span></span>  
 <span data-ttu-id="b23e0-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b23e0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b23e0-117">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b23e0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b23e0-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b23e0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b23e0-119">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b23e0-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b23e0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b23e0-120">See also</span></span>

- [<span data-ttu-id="b23e0-121">GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="b23e0-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="b23e0-122">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="b23e0-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b23e0-123">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b23e0-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
