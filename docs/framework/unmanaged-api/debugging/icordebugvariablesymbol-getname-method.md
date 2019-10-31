---
title: ICorDebugVariableSymbol：： GetName 方法
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 9bc32d3372710b4c4e92aa89df5e6e7839ad3078
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121020"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="e0002-102">ICorDebugVariableSymbol：： GetName 方法</span><span class="sxs-lookup"><span data-stu-id="e0002-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="e0002-103">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="e0002-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0002-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0002-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0002-105">參數</span><span class="sxs-lookup"><span data-stu-id="e0002-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e0002-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="e0002-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e0002-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="e0002-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e0002-108">包含變數名稱的字元陣列指標。</span><span class="sxs-lookup"><span data-stu-id="e0002-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0002-109">備註</span><span class="sxs-lookup"><span data-stu-id="e0002-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0002-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e0002-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0002-111">需求</span><span class="sxs-lookup"><span data-stu-id="e0002-111">Requirements</span></span>  
 <span data-ttu-id="e0002-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0002-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0002-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0002-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0002-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0002-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0002-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0002-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0002-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e0002-116">See also</span></span>

- [<span data-ttu-id="e0002-117">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="e0002-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="e0002-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e0002-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
