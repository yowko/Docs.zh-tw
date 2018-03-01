---
title: "ICorDebugAppDomain3::GetCachedWinRTTypes 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49b36b907df514873815ac28565c5796d997c191
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="db327-102">ICorDebugAppDomain3::GetCachedWinRTTypes 方法</span><span class="sxs-lookup"><span data-stu-id="db327-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="db327-103">取得列舉值，所有快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="db327-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db327-104">語法</span><span class="sxs-lookup"><span data-stu-id="db327-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db327-105">參數</span><span class="sxs-lookup"><span data-stu-id="db327-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="db327-106">[out]指標[ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)介面物件的可列舉的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]目前載入的應用程式定義域中的類型。</span><span class="sxs-lookup"><span data-stu-id="db327-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db327-107">需求</span><span class="sxs-lookup"><span data-stu-id="db327-107">Requirements</span></span>  
 <span data-ttu-id="db327-108">**平台：**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db327-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="db327-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db327-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db327-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db327-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db327-111">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db327-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db327-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="db327-112">See Also</span></span>  
 [<span data-ttu-id="db327-113">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="db327-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
