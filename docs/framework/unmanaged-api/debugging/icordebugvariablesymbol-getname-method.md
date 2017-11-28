---
title: ICorDebugVariableSymbol::GetName Method
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aff18efb6781aee5b6a148fcd59863a2ce657023
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="61cfa-102">ICorDebugVariableSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="61cfa-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="61cfa-103">取得變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="61cfa-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61cfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="61cfa-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61cfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="61cfa-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="61cfa-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="61cfa-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="61cfa-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="61cfa-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="61cfa-108">包含變數名稱的字元陣列指標。</span><span class="sxs-lookup"><span data-stu-id="61cfa-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61cfa-109">備註</span><span class="sxs-lookup"><span data-stu-id="61cfa-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61cfa-110">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="61cfa-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61cfa-111">需求</span><span class="sxs-lookup"><span data-stu-id="61cfa-111">Requirements</span></span>  
 <span data-ttu-id="61cfa-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61cfa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61cfa-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61cfa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61cfa-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61cfa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61cfa-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61cfa-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cfa-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61cfa-116">See Also</span></span>  
 [<span data-ttu-id="61cfa-117">ICorDebugVariableSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="61cfa-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="61cfa-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="61cfa-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
