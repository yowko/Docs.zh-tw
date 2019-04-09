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
ms.openlocfilehash: fc6cd8d2d0ab4648ad20392ef0968907917677e9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209485"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="9e7d4-102">ICorRuntimeHost::SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="9e7d4-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="9e7d4-103">此方法支援 .NET Framework 結構而且並非設計直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e7d4-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e7d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e7d4-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="9e7d4-106">[in]表示使用 fiber 的 cookie。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e7d4-107">需求</span><span class="sxs-lookup"><span data-stu-id="9e7d4-107">Requirements</span></span>  
 <span data-ttu-id="9e7d4-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e7d4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e7d4-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e7d4-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e7d4-110">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9e7d4-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e7d4-111">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9e7d4-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7d4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e7d4-112">See also</span></span>

- [<span data-ttu-id="9e7d4-113">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="9e7d4-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
