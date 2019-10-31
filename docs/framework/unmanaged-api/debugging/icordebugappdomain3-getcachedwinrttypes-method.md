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
ms.openlocfilehash: 89f45208550d49f214e763728ddc9eb1bfcd9800
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088967"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="e314e-102">ICorDebugAppDomain3::GetCachedWinRTTypes 方法</span><span class="sxs-lookup"><span data-stu-id="e314e-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="e314e-103">取得所有快取 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="e314e-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e314e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e314e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e314e-105">參數</span><span class="sxs-lookup"><span data-stu-id="e314e-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="e314e-106">脫銷[ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)介面物件的指標，可列舉目前載入應用程式域之 Windows 執行階段類型的 managed 標記法。</span><span class="sxs-lookup"><span data-stu-id="e314e-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e314e-107">需求</span><span class="sxs-lookup"><span data-stu-id="e314e-107">Requirements</span></span>  
 <span data-ttu-id="e314e-108">**平臺：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="e314e-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="e314e-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e314e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e314e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e314e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e314e-111">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e314e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e314e-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e314e-112">See also</span></span>

- [<span data-ttu-id="e314e-113">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="e314e-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
