---
title: ICorDebugStaticFieldSymbol::GetAddress 方法
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a45f233fdec23a504a71a68370e9da8e38ac0bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760868"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="923e2-102">ICorDebugStaticFieldSymbol::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="923e2-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="923e2-103">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="923e2-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="923e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="923e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="923e2-105">參數</span><span class="sxs-lookup"><span data-stu-id="923e2-105">Parameters</span></span>  
 <span data-ttu-id="923e2-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="923e2-106">pRVA</span></span>  
 <span data-ttu-id="923e2-107">[out] 靜態欄位的相對虛擬位址 (RVA) 指標。</span><span class="sxs-lookup"><span data-stu-id="923e2-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="923e2-108">備註</span><span class="sxs-lookup"><span data-stu-id="923e2-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="923e2-109">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="923e2-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="923e2-110">需求</span><span class="sxs-lookup"><span data-stu-id="923e2-110">Requirements</span></span>  
 <span data-ttu-id="923e2-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="923e2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="923e2-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="923e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="923e2-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="923e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="923e2-114">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="923e2-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="923e2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="923e2-115">See also</span></span>

- [<span data-ttu-id="923e2-116">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="923e2-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="923e2-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="923e2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
