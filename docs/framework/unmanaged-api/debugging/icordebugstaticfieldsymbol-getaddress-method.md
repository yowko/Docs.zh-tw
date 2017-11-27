---
title: "ICorDebugStaticFieldSymbol::GetAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20c0c934772625d27057957d00e53fb4b485c4fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="92e17-102">ICorDebugStaticFieldSymbol::GetAddress 方法</span><span class="sxs-lookup"><span data-stu-id="92e17-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="92e17-103">取得靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="92e17-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e17-104">語法</span><span class="sxs-lookup"><span data-stu-id="92e17-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92e17-105">參數</span><span class="sxs-lookup"><span data-stu-id="92e17-105">Parameters</span></span>  
 <span data-ttu-id="92e17-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="92e17-106">pRVA</span></span>  
 <span data-ttu-id="92e17-107">[out] 靜態欄位的相對虛擬位址 (RVA) 指標。</span><span class="sxs-lookup"><span data-stu-id="92e17-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92e17-108">備註</span><span class="sxs-lookup"><span data-stu-id="92e17-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92e17-109">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="92e17-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92e17-110">需求</span><span class="sxs-lookup"><span data-stu-id="92e17-110">Requirements</span></span>  
 <span data-ttu-id="92e17-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92e17-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e17-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92e17-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92e17-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92e17-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92e17-114">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e17-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e17-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92e17-115">See Also</span></span>  
 [<span data-ttu-id="92e17-116">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="92e17-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="92e17-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="92e17-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
