---
title: ICorDebugVariableSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f514acbd772c9d33ec4372cfaccb778d6bb41eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170166"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="8c330-102">ICorDebugVariableSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="8c330-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="8c330-103">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c330-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c330-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c330-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c330-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c330-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8c330-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="8c330-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8c330-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="8c330-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c330-108">包含變數名稱的字元陣列指標。</span><span class="sxs-lookup"><span data-stu-id="8c330-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c330-109">備註</span><span class="sxs-lookup"><span data-stu-id="8c330-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c330-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8c330-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c330-111">需求</span><span class="sxs-lookup"><span data-stu-id="8c330-111">Requirements</span></span>  
 <span data-ttu-id="8c330-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c330-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c330-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c330-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c330-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c330-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8c330-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="8c330-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8c330-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c330-116">See also</span></span>

- [<span data-ttu-id="8c330-117">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="8c330-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="8c330-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8c330-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
