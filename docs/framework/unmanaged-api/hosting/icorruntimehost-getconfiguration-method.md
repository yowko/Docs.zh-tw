---
title: ICorRuntimeHost::GetConfiguration 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f435fc71c3b1eb610b57b60a71819a0f835d4189
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466436"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="31489-102">ICorRuntimeHost::GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="31489-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="31489-103">取得物件，可讓主機指定的 common language runtime (CLR) 的回撥設定。</span><span class="sxs-lookup"><span data-stu-id="31489-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31489-104">語法</span><span class="sxs-lookup"><span data-stu-id="31489-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31489-105">參數</span><span class="sxs-lookup"><span data-stu-id="31489-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="31489-106">[out]位址指標[ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)可用來設定 CLR 的物件。</span><span class="sxs-lookup"><span data-stu-id="31489-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31489-107">備註</span><span class="sxs-lookup"><span data-stu-id="31489-107">Remarks</span></span>  
 <span data-ttu-id="31489-108">CLR 必須由之前初始化;否則，`GetConfiguration`方法會傳回 HRESULT，指出錯誤。</span><span class="sxs-lookup"><span data-stu-id="31489-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31489-109">需求</span><span class="sxs-lookup"><span data-stu-id="31489-109">Requirements</span></span>  
 <span data-ttu-id="31489-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31489-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31489-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="31489-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="31489-112">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="31489-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31489-113">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="31489-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31489-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31489-114">See also</span></span>
- [<span data-ttu-id="31489-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="31489-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
