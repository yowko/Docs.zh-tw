---
title: ICorDebugVariableSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: aa3f335516f7fa22a77b786cd870f2a5064aeff5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727623"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="bebac-102">ICorDebugVariableSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="bebac-102">ICorDebugVariableSymbol::GetName Method</span></span>

<span data-ttu-id="bebac-103">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bebac-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bebac-104">語法</span><span class="sxs-lookup"><span data-stu-id="bebac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bebac-105">參數</span><span class="sxs-lookup"><span data-stu-id="bebac-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="bebac-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="bebac-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bebac-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="bebac-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="bebac-108">包含變數名稱的字元陣列指標。</span><span class="sxs-lookup"><span data-stu-id="bebac-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bebac-109">備註</span><span class="sxs-lookup"><span data-stu-id="bebac-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bebac-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="bebac-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bebac-111">需求</span><span class="sxs-lookup"><span data-stu-id="bebac-111">Requirements</span></span>  

 <span data-ttu-id="bebac-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bebac-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bebac-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bebac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bebac-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bebac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bebac-115">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bebac-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bebac-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bebac-116">See also</span></span>

- [<span data-ttu-id="bebac-117">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="bebac-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="bebac-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bebac-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
