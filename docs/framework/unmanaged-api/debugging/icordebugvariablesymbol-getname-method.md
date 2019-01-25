---
title: ICorDebugVariableSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b414e1fa035a50cdcfd317592f69abdc40fb0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684093"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="048b3-102">ICorDebugVariableSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="048b3-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="048b3-103">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="048b3-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="048b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="048b3-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="048b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="048b3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="048b3-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="048b3-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="048b3-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="048b3-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="048b3-108">包含變數名稱的字元陣列指標。</span><span class="sxs-lookup"><span data-stu-id="048b3-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="048b3-109">備註</span><span class="sxs-lookup"><span data-stu-id="048b3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="048b3-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="048b3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="048b3-111">需求</span><span class="sxs-lookup"><span data-stu-id="048b3-111">Requirements</span></span>  
 <span data-ttu-id="048b3-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="048b3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="048b3-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="048b3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="048b3-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="048b3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="048b3-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="048b3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="048b3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="048b3-116">See also</span></span>
- [<span data-ttu-id="048b3-117">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="048b3-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="048b3-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="048b3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
