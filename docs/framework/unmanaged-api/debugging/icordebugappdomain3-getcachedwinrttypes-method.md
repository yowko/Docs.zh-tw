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
ms.openlocfilehash: 4ba981d86f90af449820ce13aa847169ca877429
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737768"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="fa8a9-102">ICorDebugAppDomain3::GetCachedWinRTTypes 方法</span><span class="sxs-lookup"><span data-stu-id="fa8a9-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="fa8a9-103">取得所有快取的 Windows 執行階段類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="fa8a9-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa8a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa8a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa8a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa8a9-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="fa8a9-106">[out]指標[ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)應用程式定義域中載入的可列舉的受控的 Windows 執行階段類型表示目前的介面物件。</span><span class="sxs-lookup"><span data-stu-id="fa8a9-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa8a9-107">需求</span><span class="sxs-lookup"><span data-stu-id="fa8a9-107">Requirements</span></span>  
 <span data-ttu-id="fa8a9-108">**平台：** Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="fa8a9-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="fa8a9-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa8a9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa8a9-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa8a9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa8a9-111">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa8a9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa8a9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa8a9-112">See also</span></span>

- [<span data-ttu-id="fa8a9-113">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="fa8a9-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
