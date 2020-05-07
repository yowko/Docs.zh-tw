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
ms.openlocfilehash: a2f6df7647ffe9f2adff963b6629ed29ece053c0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895155"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="dff4b-102">ICorDebugAppDomain::IsAttached 方法</span><span class="sxs-lookup"><span data-stu-id="dff4b-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="dff4b-103">取得值，指出偵錯工具是否附加至應用程式域。</span><span class="sxs-lookup"><span data-stu-id="dff4b-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="dff4b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dff4b-105">參數</span><span class="sxs-lookup"><span data-stu-id="dff4b-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="dff4b-106">脫銷`true`如果偵錯工具附加至應用程式域，則為，否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="dff4b-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dff4b-107">備註</span><span class="sxs-lookup"><span data-stu-id="dff4b-107">Remarks</span></span>  
 <span data-ttu-id="dff4b-108">在偵錯工具附加至應用程式域之前，無法使用 ICorDebugController 方法。</span><span class="sxs-lookup"><span data-stu-id="dff4b-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dff4b-109">需求</span><span class="sxs-lookup"><span data-stu-id="dff4b-109">Requirements</span></span>  
 <span data-ttu-id="dff4b-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dff4b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dff4b-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dff4b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dff4b-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dff4b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dff4b-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dff4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
