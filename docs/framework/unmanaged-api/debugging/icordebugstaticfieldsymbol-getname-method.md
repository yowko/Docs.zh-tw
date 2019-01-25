---
title: ICorDebugStaticFieldSymbol::GetName 方法
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6da390fb7de3c248fa5389f133d65f9914d5260a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714685"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="e37bb-102">ICorDebugStaticFieldSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="e37bb-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="e37bb-103">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="e37bb-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="e37bb-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e37bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="e37bb-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e37bb-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="e37bb-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e37bb-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="e37bb-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e37bb-108">[out] 會儲存傳回的名稱之字元陣列。</span><span class="sxs-lookup"><span data-stu-id="e37bb-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e37bb-109">備註</span><span class="sxs-lookup"><span data-stu-id="e37bb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e37bb-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="e37bb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e37bb-111">需求</span><span class="sxs-lookup"><span data-stu-id="e37bb-111">Requirements</span></span>  
 <span data-ttu-id="e37bb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e37bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e37bb-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e37bb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e37bb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e37bb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e37bb-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e37bb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37bb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e37bb-116">See also</span></span>
- [<span data-ttu-id="e37bb-117">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="e37bb-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e37bb-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e37bb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
