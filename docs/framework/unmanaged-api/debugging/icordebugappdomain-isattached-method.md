---
title: "ICorDebugAppDomain::IsAttached 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a1af550de7198041a885a788d6b36349c8e1c091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="90408-102">ICorDebugAppDomain::IsAttached 方法</span><span class="sxs-lookup"><span data-stu-id="90408-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="90408-103">取得值，指出是否要將偵錯工具附加至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="90408-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90408-104">語法</span><span class="sxs-lookup"><span data-stu-id="90408-104">Syntax</span></span>  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90408-105">參數</span><span class="sxs-lookup"><span data-stu-id="90408-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="90408-106">[out]`true`偵錯工具是否附加至應用程式定義域，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="90408-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90408-107">備註</span><span class="sxs-lookup"><span data-stu-id="90408-107">Remarks</span></span>  
 <span data-ttu-id="90408-108">ICorDebugController 方法無法使用，直到偵錯工具附加至應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="90408-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90408-109">需求</span><span class="sxs-lookup"><span data-stu-id="90408-109">Requirements</span></span>  
 <span data-ttu-id="90408-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90408-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90408-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90408-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90408-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90408-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90408-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90408-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
