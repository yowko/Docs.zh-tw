---
title: ICorDebugVariableSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 172eea452442aa94ea010e2c434908ab8d040a93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790915"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="ea387-102">ICorDebugVariableSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="ea387-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="ea387-103">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea387-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea387-104">語法</span><span class="sxs-lookup"><span data-stu-id="ea387-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea387-105">參數</span><span class="sxs-lookup"><span data-stu-id="ea387-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ea387-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="ea387-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ea387-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="ea387-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ea387-108">包含變數名稱的字元陣列指標。</span><span class="sxs-lookup"><span data-stu-id="ea387-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea387-109">備註</span><span class="sxs-lookup"><span data-stu-id="ea387-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea387-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="ea387-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea387-111">需求</span><span class="sxs-lookup"><span data-stu-id="ea387-111">Requirements</span></span>  
 <span data-ttu-id="ea387-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea387-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea387-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea387-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea387-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea387-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea387-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea387-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea387-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea387-116">See also</span></span>

- [<span data-ttu-id="ea387-117">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="ea387-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="ea387-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ea387-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
