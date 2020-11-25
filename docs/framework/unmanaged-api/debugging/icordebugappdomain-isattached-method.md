---
title: ICorDebugAppDomain::IsAttached 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
ms.openlocfilehash: 898398b731832e698a43eb270bbdc63bb3867bb8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702169"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="7abf3-102">ICorDebugAppDomain::IsAttached 方法</span><span class="sxs-lookup"><span data-stu-id="7abf3-102">ICorDebugAppDomain::IsAttached Method</span></span>

<span data-ttu-id="7abf3-103">取得值，這個值會指出偵錯工具是否附加至應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7abf3-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abf3-104">語法</span><span class="sxs-lookup"><span data-stu-id="7abf3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7abf3-105">參數</span><span class="sxs-lookup"><span data-stu-id="7abf3-105">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="7abf3-106">[out] `true` 如果偵錯工具已附加至應用程式域，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="7abf3-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7abf3-107">備註</span><span class="sxs-lookup"><span data-stu-id="7abf3-107">Remarks</span></span>  

 <span data-ttu-id="7abf3-108">在偵錯工具附加至應用程式域之前，無法使用 ICorDebugController 方法。</span><span class="sxs-lookup"><span data-stu-id="7abf3-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7abf3-109">需求</span><span class="sxs-lookup"><span data-stu-id="7abf3-109">Requirements</span></span>  

 <span data-ttu-id="7abf3-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7abf3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abf3-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7abf3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7abf3-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7abf3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7abf3-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abf3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
