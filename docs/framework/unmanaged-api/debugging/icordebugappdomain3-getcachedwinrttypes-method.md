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
ms.openlocfilehash: e5fd1730bbe5b6f2905691dce41a7f503227534a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179075"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="67599-102">ICorDebugAppDomain3::GetCachedWinRTTypes 方法</span><span class="sxs-lookup"><span data-stu-id="67599-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="67599-103">獲取所有緩存的 Windows 運行時類型的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="67599-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67599-104">語法</span><span class="sxs-lookup"><span data-stu-id="67599-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="67599-105">參數</span><span class="sxs-lookup"><span data-stu-id="67599-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="67599-106">[出]指向[ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md)介面物件的指標，該物件可以枚舉當前在應用程式域中載入的 Windows 運行時類型的託管表示形式。</span><span class="sxs-lookup"><span data-stu-id="67599-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67599-107">需求</span><span class="sxs-lookup"><span data-stu-id="67599-107">Requirements</span></span>  
 <span data-ttu-id="67599-108">**平臺：** 視窗運行時</span><span class="sxs-lookup"><span data-stu-id="67599-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="67599-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67599-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67599-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67599-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67599-111">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67599-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67599-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67599-112">See also</span></span>

- [<span data-ttu-id="67599-113">ICorDebugAppDomain3 介面</span><span class="sxs-lookup"><span data-stu-id="67599-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
