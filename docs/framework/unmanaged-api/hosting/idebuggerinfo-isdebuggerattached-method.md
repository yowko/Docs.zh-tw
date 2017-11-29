---
title: "IDebuggerInfo::IsDebuggerAttached 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerInfo.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a6e1f11939bc4f11b1fb49dc44f129176143fbca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="db1ae-102">IDebuggerInfo::IsDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="db1ae-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="db1ae-103">取得值，指出是否要將受管理的偵錯工具附加至這個處理程序。</span><span class="sxs-lookup"><span data-stu-id="db1ae-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db1ae-104">語法</span><span class="sxs-lookup"><span data-stu-id="db1ae-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db1ae-105">參數</span><span class="sxs-lookup"><span data-stu-id="db1ae-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="db1ae-106">[out]值的指標`true`managed 偵錯工具是否附加至處理程序，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="db1ae-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db1ae-107">需求</span><span class="sxs-lookup"><span data-stu-id="db1ae-107">Requirements</span></span>  
 <span data-ttu-id="db1ae-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db1ae-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db1ae-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="db1ae-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db1ae-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="db1ae-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db1ae-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db1ae-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1ae-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db1ae-112">See Also</span></span>  
 [<span data-ttu-id="db1ae-113">IDebuggerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="db1ae-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
