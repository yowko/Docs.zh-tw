---
title: ICorDebugStaticFieldSymbol::GetName 方法
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 0e4c52ff1ae6113ee2c3990a9d91682e10141902
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791835"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="988e6-102">ICorDebugStaticFieldSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="988e6-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="988e6-103">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="988e6-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="988e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="988e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="988e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="988e6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="988e6-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="988e6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="988e6-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="988e6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="988e6-108">[out] 會儲存傳回的名稱之字元陣列。</span><span class="sxs-lookup"><span data-stu-id="988e6-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="988e6-109">備註</span><span class="sxs-lookup"><span data-stu-id="988e6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="988e6-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="988e6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="988e6-111">需求</span><span class="sxs-lookup"><span data-stu-id="988e6-111">Requirements</span></span>  
 <span data-ttu-id="988e6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="988e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="988e6-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="988e6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="988e6-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="988e6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="988e6-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="988e6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988e6-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="988e6-116">See also</span></span>

- [<span data-ttu-id="988e6-117">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="988e6-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="988e6-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="988e6-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
