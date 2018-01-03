---
title: "ICorRuntimeHost::SwitchInLogicalThreadState 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.SwitchInLogicalThreadState
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 065a2347be2587265471d707988e90a01482c5a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="41dcd-102">ICorRuntimeHost::SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="41dcd-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="41dcd-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="41dcd-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41dcd-104">語法</span><span class="sxs-lookup"><span data-stu-id="41dcd-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41dcd-105">參數</span><span class="sxs-lookup"><span data-stu-id="41dcd-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="41dcd-106">[in]表示要使用 fiber 的 cookie。</span><span class="sxs-lookup"><span data-stu-id="41dcd-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41dcd-107">需求</span><span class="sxs-lookup"><span data-stu-id="41dcd-107">Requirements</span></span>  
 <span data-ttu-id="41dcd-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41dcd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41dcd-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41dcd-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41dcd-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="41dcd-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41dcd-111">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="41dcd-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41dcd-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="41dcd-112">See Also</span></span>  
 [<span data-ttu-id="41dcd-113">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="41dcd-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
