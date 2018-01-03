---
title: "ICorDebugStaticFieldSymbol::GetSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67cbe6858e91e089c36047d6ed83743e45e1d1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="38418-102">ICorDebugStaticFieldSymbol::GetSize 方法</span><span class="sxs-lookup"><span data-stu-id="38418-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="38418-103">取得靜態欄位的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="38418-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38418-104">語法</span><span class="sxs-lookup"><span data-stu-id="38418-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38418-105">參數</span><span class="sxs-lookup"><span data-stu-id="38418-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="38418-106">[out] 欄位長度的指標。</span><span class="sxs-lookup"><span data-stu-id="38418-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38418-107">備註</span><span class="sxs-lookup"><span data-stu-id="38418-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38418-108">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="38418-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38418-109">需求</span><span class="sxs-lookup"><span data-stu-id="38418-109">Requirements</span></span>  
 <span data-ttu-id="38418-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38418-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38418-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38418-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38418-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38418-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38418-113">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38418-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38418-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="38418-114">See Also</span></span>  
 [<span data-ttu-id="38418-115">ICorDebugStaticFieldSymbol 介面</span><span class="sxs-lookup"><span data-stu-id="38418-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="38418-116">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="38418-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
