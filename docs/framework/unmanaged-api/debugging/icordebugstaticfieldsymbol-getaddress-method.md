---
title: ICorDebugStaticFieldSymbol::GetAddress 方法
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d41b99d7410333cb6a22443271c1fcbc41c3594
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962705"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="94c18-102">ICorDebugStaticFieldSymbol::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="94c18-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="94c18-103">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="94c18-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c18-104">語法</span><span class="sxs-lookup"><span data-stu-id="94c18-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94c18-105">參數</span><span class="sxs-lookup"><span data-stu-id="94c18-105">Parameters</span></span>  
 <span data-ttu-id="94c18-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="94c18-106">pRVA</span></span>  
 <span data-ttu-id="94c18-107">[out] 靜態欄位的相對虛擬位址 (RVA) 指標。</span><span class="sxs-lookup"><span data-stu-id="94c18-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94c18-108">備註</span><span class="sxs-lookup"><span data-stu-id="94c18-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94c18-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="94c18-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c18-110">需求</span><span class="sxs-lookup"><span data-stu-id="94c18-110">Requirements</span></span>  
 <span data-ttu-id="94c18-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94c18-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94c18-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94c18-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94c18-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94c18-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94c18-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94c18-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c18-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94c18-115">See also</span></span>

- [<span data-ttu-id="94c18-116">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="94c18-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="94c18-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="94c18-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
