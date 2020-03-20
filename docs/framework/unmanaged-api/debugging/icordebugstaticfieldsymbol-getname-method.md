---
title: ICorDebugStaticFieldSymbol::GetName 方法
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178518"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="e4f8e-102">ICorDebugStaticFieldSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="e4f8e-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="e4f8e-103">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="e4f8e-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4f8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4f8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4f8e-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4f8e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e4f8e-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="e4f8e-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e4f8e-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="e4f8e-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e4f8e-108">[out] 會儲存傳回的名稱之字元陣列。</span><span class="sxs-lookup"><span data-stu-id="e4f8e-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4f8e-109">備註</span><span class="sxs-lookup"><span data-stu-id="e4f8e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4f8e-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e4f8e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4f8e-111">需求</span><span class="sxs-lookup"><span data-stu-id="e4f8e-111">Requirements</span></span>  
 <span data-ttu-id="e4f8e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4f8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4f8e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4f8e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4f8e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4f8e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4f8e-115">**.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4f8e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f8e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4f8e-116">See also</span></span>

- [<span data-ttu-id="e4f8e-117">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="e4f8e-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e4f8e-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e4f8e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
