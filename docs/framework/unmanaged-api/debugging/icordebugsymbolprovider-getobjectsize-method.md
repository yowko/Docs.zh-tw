---
title: ICorDebugSymbolProvider::GetObjectSize 方法
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59054d7b939ab29cb08c30961601a323529ce06b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955634"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="b9b57-102">ICorDebugSymbolProvider::GetObjectSize 方法</span><span class="sxs-lookup"><span data-stu-id="b9b57-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="b9b57-103">傳回根據某物件之 typespec 簽章的該物件大小。</span><span class="sxs-lookup"><span data-stu-id="b9b57-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9b57-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9b57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9b57-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9b57-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="b9b57-106">[in] Typespec 簽章中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="b9b57-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="b9b57-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="b9b57-107">typeSig</span></span>  
 <span data-ttu-id="b9b57-108">[in] Typespec 簽章。</span><span class="sxs-lookup"><span data-stu-id="b9b57-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="b9b57-109">[out] 物件大小的指標。</span><span class="sxs-lookup"><span data-stu-id="b9b57-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9b57-110">備註</span><span class="sxs-lookup"><span data-stu-id="b9b57-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9b57-111">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="b9b57-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b57-112">需求</span><span class="sxs-lookup"><span data-stu-id="b9b57-112">Requirements</span></span>  
 <span data-ttu-id="b9b57-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9b57-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b57-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9b57-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9b57-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9b57-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9b57-116">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b57-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b57-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9b57-117">See also</span></span>

- [<span data-ttu-id="b9b57-118">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="b9b57-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b9b57-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b9b57-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
