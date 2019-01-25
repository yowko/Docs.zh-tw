---
title: ICorDebugAppDomain3::GetCachedWinRTTypes 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afbe368d58c96c8ddc97ccc3bb077ce768b229b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566108"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="264ba-102">ICorDebugAppDomain3::GetCachedWinRTTypes 方法</span><span class="sxs-lookup"><span data-stu-id="264ba-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="264ba-103">取得列舉值，所有快取[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型別。</span><span class="sxs-lookup"><span data-stu-id="264ba-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="264ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="264ba-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="264ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="264ba-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="264ba-106">[out]指標[ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)介面的物件可以列舉的受管理的表示法[!INCLUDE[wrt](../../../../includes/wrt-md.md)]目前載入的應用程式定義域中的類型。</span><span class="sxs-lookup"><span data-stu-id="264ba-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="264ba-107">需求</span><span class="sxs-lookup"><span data-stu-id="264ba-107">Requirements</span></span>  
 <span data-ttu-id="264ba-108">**平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="264ba-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="264ba-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="264ba-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="264ba-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="264ba-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="264ba-111">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="264ba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="264ba-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="264ba-112">See also</span></span>
- [<span data-ttu-id="264ba-113">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="264ba-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
