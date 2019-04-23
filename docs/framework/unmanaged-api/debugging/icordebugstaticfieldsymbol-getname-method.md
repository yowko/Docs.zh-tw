---
title: ICorDebugStaticFieldSymbol::GetName 方法
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5f52999c3f680fbccefe4681f83d473cdb86306
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206482"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="5451d-102">ICorDebugStaticFieldSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="5451d-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="5451d-103">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="5451d-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5451d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5451d-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5451d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5451d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5451d-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="5451d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5451d-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="5451d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5451d-108">[out] 會儲存傳回的名稱之字元陣列。</span><span class="sxs-lookup"><span data-stu-id="5451d-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5451d-109">備註</span><span class="sxs-lookup"><span data-stu-id="5451d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5451d-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="5451d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5451d-111">需求</span><span class="sxs-lookup"><span data-stu-id="5451d-111">Requirements</span></span>  
 <span data-ttu-id="5451d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5451d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5451d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5451d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5451d-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5451d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5451d-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5451d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5451d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5451d-116">See also</span></span>

- [<span data-ttu-id="5451d-117">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="5451d-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="5451d-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5451d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
