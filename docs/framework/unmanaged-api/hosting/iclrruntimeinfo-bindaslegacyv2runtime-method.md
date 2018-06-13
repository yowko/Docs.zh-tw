---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690287bf54f98c19298504ee3058a59ef88a87f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433157"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="1b698-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法</span><span class="sxs-lookup"><span data-stu-id="1b698-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="1b698-103">將所有舊版 common language runtime (CLR) 第 2 版啟用原則決策的目前執行階段的繫結。</span><span class="sxs-lookup"><span data-stu-id="1b698-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b698-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b698-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1b698-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b698-105">Return Value</span></span>  
 <span data-ttu-id="1b698-106">這個方法會傳回下列特定的 Hresult:</span><span class="sxs-lookup"><span data-stu-id="1b698-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="1b698-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b698-107">HRESULT</span></span>|<span data-ttu-id="1b698-108">描述</span><span class="sxs-lookup"><span data-stu-id="1b698-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b698-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b698-109">S_OK</span></span>|<span data-ttu-id="1b698-110">繫結成功，或是此執行階段已繫結為舊版 CLR 版本 2 的啟用原則執行階段。</span><span class="sxs-lookup"><span data-stu-id="1b698-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="1b698-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="1b698-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="1b698-112">不同的執行階段已經繫結到舊版的 CLR 版本 2 的啟用原則。</span><span class="sxs-lookup"><span data-stu-id="1b698-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b698-113">備註</span><span class="sxs-lookup"><span data-stu-id="1b698-113">Remarks</span></span>  
 <span data-ttu-id="1b698-114">如果目前的執行階段已繫結的所有舊版 CLR 版本 2 啟用原則決策 (例如，藉由使用`useLegacyV2RuntimeActivationPolicy`屬性[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔中)，這個方法不會傳回錯誤結果;相反地，結果是 S_OK 時，就如同它是如果該方法必須成功繫結舊版啟用原則。</span><span class="sxs-lookup"><span data-stu-id="1b698-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b698-115">需求</span><span class="sxs-lookup"><span data-stu-id="1b698-115">Requirements</span></span>  
 <span data-ttu-id="1b698-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b698-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b698-117">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1b698-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1b698-118">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1b698-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b698-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b698-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b698-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b698-120">See Also</span></span>  
 [<span data-ttu-id="1b698-121">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="1b698-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="1b698-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1b698-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="1b698-123">裝載</span><span class="sxs-lookup"><span data-stu-id="1b698-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="1b698-124">\<startup> 項目</span><span class="sxs-lookup"><span data-stu-id="1b698-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
