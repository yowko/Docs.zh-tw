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
ms.openlocfilehash: f0a03ecce49bbc3c1c03d037c9be31a8e994259d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732085"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="6dd62-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法</span><span class="sxs-lookup"><span data-stu-id="6dd62-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>

<span data-ttu-id="6dd62-103">將所有舊版 common language runtime 的目前執行時間系結 (CLR) 第2版啟用原則決策。</span><span class="sxs-lookup"><span data-stu-id="6dd62-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd62-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dd62-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6dd62-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="6dd62-105">Return Value</span></span>  

 <span data-ttu-id="6dd62-106">這個方法會傳回下列特定的 Hresult：</span><span class="sxs-lookup"><span data-stu-id="6dd62-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="6dd62-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6dd62-107">HRESULT</span></span>|<span data-ttu-id="6dd62-108">描述</span><span class="sxs-lookup"><span data-stu-id="6dd62-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6dd62-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6dd62-109">S_OK</span></span>|<span data-ttu-id="6dd62-110">系結成功，或此執行時間已系結為舊版 CLR 第2版啟用原則執行時間。</span><span class="sxs-lookup"><span data-stu-id="6dd62-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="6dd62-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="6dd62-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="6dd62-112">不同的執行時間已系結至舊版 CLR 第2版啟用原則。</span><span class="sxs-lookup"><span data-stu-id="6dd62-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6dd62-113">備註</span><span class="sxs-lookup"><span data-stu-id="6dd62-113">Remarks</span></span>  

 <span data-ttu-id="6dd62-114">如果目前的執行時間已系結至所有舊版 CLR 第2版啟用原則決策 (例如，在 `useLegacyV2RuntimeActivationPolicy` 設定檔) 中[ \<startup> ](../../configure-apps/file-schema/startup/startup-element.md)使用專案上的屬性，則這個方法不會傳回錯誤結果，而是會 S_OK 結果，就像是方法已成功系結舊版啟用原則一樣。</span><span class="sxs-lookup"><span data-stu-id="6dd62-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd62-115">需求</span><span class="sxs-lookup"><span data-stu-id="6dd62-115">Requirements</span></span>  

 <span data-ttu-id="6dd62-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6dd62-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dd62-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="6dd62-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6dd62-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6dd62-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6dd62-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd62-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd62-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd62-120">See also</span></span>

- [<span data-ttu-id="6dd62-121">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="6dd62-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="6dd62-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6dd62-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6dd62-123">裝載</span><span class="sxs-lookup"><span data-stu-id="6dd62-123">Hosting</span></span>](index.md)
- [<span data-ttu-id="6dd62-124">\<startup> 元素</span><span class="sxs-lookup"><span data-stu-id="6dd62-124">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
