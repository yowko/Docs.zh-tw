---
title: "ICorRuntimeHost::GetConfiguration 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61c0a95df2140d2eaf771fcd8f50cd733b9133e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="c979e-102">ICorRuntimeHost::GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="c979e-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="c979e-103">取得物件，可讓主機指定的 common language runtime (CLR) 回呼組態。</span><span class="sxs-lookup"><span data-stu-id="c979e-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c979e-104">語法</span><span class="sxs-lookup"><span data-stu-id="c979e-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c979e-105">參數</span><span class="sxs-lookup"><span data-stu-id="c979e-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="c979e-106">[out]位址指標[ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)可以用來設定 CLR 物件。</span><span class="sxs-lookup"><span data-stu-id="c979e-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c979e-107">備註</span><span class="sxs-lookup"><span data-stu-id="c979e-107">Remarks</span></span>  
 <span data-ttu-id="c979e-108">初始化; 之前，必須設定 CLR否則，`GetConfiguration`方法會傳回 HRESULT，指出錯誤。</span><span class="sxs-lookup"><span data-stu-id="c979e-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c979e-109">需求</span><span class="sxs-lookup"><span data-stu-id="c979e-109">Requirements</span></span>  
 <span data-ttu-id="c979e-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c979e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c979e-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c979e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c979e-112">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c979e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c979e-113">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="c979e-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c979e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c979e-114">See Also</span></span>  
 [<span data-ttu-id="c979e-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="c979e-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
