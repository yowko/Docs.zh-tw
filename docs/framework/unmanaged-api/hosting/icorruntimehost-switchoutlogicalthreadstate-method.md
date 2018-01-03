---
title: "ICorRuntimeHost::SwitchOutLogicalThreadState 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.SwitchOutLogicalThreadState
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6302a836168f38991c7c371789d4913a3c95c16d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="e2ca7-102">ICorRuntimeHost::SwitchOutLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="e2ca7-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="e2ca7-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="e2ca7-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ca7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2ca7-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2ca7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2ca7-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="e2ca7-106">[out]表示要切換移出之 fiber 的 cookie。</span><span class="sxs-lookup"><span data-stu-id="e2ca7-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2ca7-107">需求</span><span class="sxs-lookup"><span data-stu-id="e2ca7-107">Requirements</span></span>  
 <span data-ttu-id="e2ca7-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2ca7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2ca7-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e2ca7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2ca7-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e2ca7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2ca7-111">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="e2ca7-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ca7-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2ca7-112">See Also</span></span>  
 [<span data-ttu-id="e2ca7-113">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e2ca7-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
