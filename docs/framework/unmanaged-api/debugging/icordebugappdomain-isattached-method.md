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
ms.openlocfilehash: 30e0b0c4ed9bac4abd1dc185031e41c1e3ed014a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134666"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="a1ca4-102">ICorDebugAppDomain::IsAttached 方法</span><span class="sxs-lookup"><span data-stu-id="a1ca4-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="a1ca4-103">取得值，指出偵錯工具是否附加至應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a1ca4-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ca4-104">語法</span><span class="sxs-lookup"><span data-stu-id="a1ca4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ca4-105">參數</span><span class="sxs-lookup"><span data-stu-id="a1ca4-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="a1ca4-106">[out] `true` 如果偵錯工具附加至應用程式域，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="a1ca4-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1ca4-107">備註</span><span class="sxs-lookup"><span data-stu-id="a1ca4-107">Remarks</span></span>  
 <span data-ttu-id="a1ca4-108">在偵錯工具附加至應用程式域之前，無法使用 ICorDebugController 方法。</span><span class="sxs-lookup"><span data-stu-id="a1ca4-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ca4-109">需求</span><span class="sxs-lookup"><span data-stu-id="a1ca4-109">Requirements</span></span>  
 <span data-ttu-id="a1ca4-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1ca4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ca4-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1ca4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1ca4-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1ca4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1ca4-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ca4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
