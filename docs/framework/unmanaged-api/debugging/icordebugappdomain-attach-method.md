---
title: ICorDebugAppDomain::Attach 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.Attach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d30b6cb083cc2f92bcbe089bf8e990fedd8e8f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738089"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="0fbd3-102">ICorDebugAppDomain::Attach 方法</span><span class="sxs-lookup"><span data-stu-id="0fbd3-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="0fbd3-103">將偵錯工具附加至應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="0fbd3-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fbd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="0fbd3-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0fbd3-105">備註</span><span class="sxs-lookup"><span data-stu-id="0fbd3-105">Remarks</span></span>  
 <span data-ttu-id="0fbd3-106">偵錯工具必須連接到接收事件，並啟用偵錯之應用程式定義域的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="0fbd3-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fbd3-107">需求</span><span class="sxs-lookup"><span data-stu-id="0fbd3-107">Requirements</span></span>  
 <span data-ttu-id="0fbd3-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0fbd3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fbd3-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fbd3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fbd3-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fbd3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fbd3-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fbd3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
