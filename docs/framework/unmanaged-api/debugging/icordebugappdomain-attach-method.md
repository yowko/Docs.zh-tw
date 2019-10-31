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
ms.openlocfilehash: 66ec64b1a855a3d31f14f3ef29dde0b82361f5d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133976"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="b0806-102">ICorDebugAppDomain::Attach 方法</span><span class="sxs-lookup"><span data-stu-id="b0806-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="b0806-103">將偵錯工具附加至應用程式域。</span><span class="sxs-lookup"><span data-stu-id="b0806-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0806-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0806-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b0806-105">備註</span><span class="sxs-lookup"><span data-stu-id="b0806-105">Remarks</span></span>  
 <span data-ttu-id="b0806-106">偵錯工具必須附加至應用程式域，才能接收事件和啟用應用程式域的偵測。</span><span class="sxs-lookup"><span data-stu-id="b0806-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0806-107">需求</span><span class="sxs-lookup"><span data-stu-id="b0806-107">Requirements</span></span>  
 <span data-ttu-id="b0806-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0806-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0806-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0806-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0806-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0806-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0806-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0806-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
