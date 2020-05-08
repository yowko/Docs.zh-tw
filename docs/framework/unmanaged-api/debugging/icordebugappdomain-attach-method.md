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
ms.openlocfilehash: 92cc6c3ce15d8391a43ff130a82476a4363ff5bd
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895303"
---
# <a name="icordebugappdomainattach-method"></a><span data-ttu-id="a3293-102">ICorDebugAppDomain::Attach 方法</span><span class="sxs-lookup"><span data-stu-id="a3293-102">ICorDebugAppDomain::Attach Method</span></span>
<span data-ttu-id="a3293-103">將偵錯工具附加至應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a3293-103">Attaches the debugger to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3293-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3293-104">Syntax</span></span>  
  
```cpp  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3293-105">備註</span><span class="sxs-lookup"><span data-stu-id="a3293-105">Remarks</span></span>  
 <span data-ttu-id="a3293-106">偵錯工具必須附加至應用程式域，才能接收事件和啟用應用程式域的偵測。</span><span class="sxs-lookup"><span data-stu-id="a3293-106">The debugger must be attached to the application domain to receive events and to enable debugging of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3293-107">需求</span><span class="sxs-lookup"><span data-stu-id="a3293-107">Requirements</span></span>  
 <span data-ttu-id="a3293-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3293-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3293-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3293-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3293-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3293-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3293-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3293-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
