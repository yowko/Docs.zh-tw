---
title: "ICorDebugStaticFieldSymbol::GetName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: af3cea14e29c987d2d24d5adc803afd5b9084651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="f8462-102">ICorDebugStaticFieldSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="f8462-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="f8462-103">取得靜態欄位的名稱。</span><span class="sxs-lookup"><span data-stu-id="f8462-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8462-104">語法</span><span class="sxs-lookup"><span data-stu-id="f8462-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8462-105">參數</span><span class="sxs-lookup"><span data-stu-id="f8462-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f8462-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="f8462-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f8462-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="f8462-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f8462-108">[out] 會儲存傳回的名稱之字元陣列。</span><span class="sxs-lookup"><span data-stu-id="f8462-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8462-109">備註</span><span class="sxs-lookup"><span data-stu-id="f8462-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8462-110">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="f8462-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8462-111">需求</span><span class="sxs-lookup"><span data-stu-id="f8462-111">Requirements</span></span>  
 <span data-ttu-id="f8462-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8462-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8462-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8462-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8462-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8462-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8462-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8462-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8462-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8462-116">See Also</span></span>  
 [<span data-ttu-id="f8462-117">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="f8462-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="f8462-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f8462-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
