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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa9576f568ef1f6da3eef812abb9674aa0d81dfb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496374"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="47aa7-102">ICorDebugAppDomain::IsAttached 方法</span><span class="sxs-lookup"><span data-stu-id="47aa7-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="47aa7-103">取得值，指出是否要將偵錯工具附加至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="47aa7-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47aa7-104">語法</span><span class="sxs-lookup"><span data-stu-id="47aa7-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47aa7-105">參數</span><span class="sxs-lookup"><span data-stu-id="47aa7-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="47aa7-106">[out]`true`偵錯工具附加至應用程式定義域，否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="47aa7-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47aa7-107">備註</span><span class="sxs-lookup"><span data-stu-id="47aa7-107">Remarks</span></span>  
 <span data-ttu-id="47aa7-108">ICorDebugController 方法無法使用，直到偵錯工具附加至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="47aa7-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47aa7-109">需求</span><span class="sxs-lookup"><span data-stu-id="47aa7-109">Requirements</span></span>  
 <span data-ttu-id="47aa7-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="47aa7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47aa7-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47aa7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47aa7-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47aa7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47aa7-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47aa7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
