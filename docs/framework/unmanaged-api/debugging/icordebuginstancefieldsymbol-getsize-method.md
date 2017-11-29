---
title: "ICorDebugInstanceFieldSymbol::GetSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 364144dcef21e7e9c058cb0317970a273aa8ecac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="e7790-102">ICorDebugInstanceFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="e7790-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="e7790-103">取得執行個體欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="e7790-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7790-104">語法</span><span class="sxs-lookup"><span data-stu-id="e7790-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7790-105">參數</span><span class="sxs-lookup"><span data-stu-id="e7790-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="e7790-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="e7790-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7790-107">備註</span><span class="sxs-lookup"><span data-stu-id="e7790-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7790-108">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="e7790-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7790-109">需求</span><span class="sxs-lookup"><span data-stu-id="e7790-109">Requirements</span></span>  
 <span data-ttu-id="e7790-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7790-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7790-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7790-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7790-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7790-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7790-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7790-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7790-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7790-114">See Also</span></span>  
 [<span data-ttu-id="e7790-115">ICorDebugInstanceFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="e7790-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="e7790-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e7790-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
