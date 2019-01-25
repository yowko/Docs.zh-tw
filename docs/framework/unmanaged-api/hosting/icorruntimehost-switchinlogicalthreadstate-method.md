---
title: ICorRuntimeHost::SwitchInLogicalThreadState 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eebfb98dfefd536998ef0c02d66b57d39414f0cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558731"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="7c317-102">ICorRuntimeHost::SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="7c317-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="7c317-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="7c317-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c317-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c317-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c317-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c317-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="7c317-106">[in]表示使用 fiber 的 cookie。</span><span class="sxs-lookup"><span data-stu-id="7c317-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c317-107">需求</span><span class="sxs-lookup"><span data-stu-id="7c317-107">Requirements</span></span>  
 <span data-ttu-id="7c317-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c317-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c317-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c317-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c317-110">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7c317-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c317-111">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="7c317-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c317-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c317-112">See also</span></span>
- [<span data-ttu-id="7c317-113">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="7c317-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
