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
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703899"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="84816-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime 方法</span><span class="sxs-lookup"><span data-stu-id="84816-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="84816-103">將目前的執行時間系結至所有舊版 common language runtime （CLR）第2版啟用原則決策。</span><span class="sxs-lookup"><span data-stu-id="84816-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84816-104">語法</span><span class="sxs-lookup"><span data-stu-id="84816-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="84816-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="84816-105">Return Value</span></span>  
 <span data-ttu-id="84816-106">這個方法會傳回下列特定的 Hresult：</span><span class="sxs-lookup"><span data-stu-id="84816-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="84816-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84816-107">HRESULT</span></span>|<span data-ttu-id="84816-108">說明</span><span class="sxs-lookup"><span data-stu-id="84816-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="84816-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="84816-109">S_OK</span></span>|<span data-ttu-id="84816-110">任一系結成功，或此執行時間已系結為舊版 CLR 版本2啟用原則執行時間。</span><span class="sxs-lookup"><span data-stu-id="84816-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="84816-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="84816-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="84816-112">不同的執行時間已系結至舊版 CLR 第2版啟用原則。</span><span class="sxs-lookup"><span data-stu-id="84816-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84816-113">備註</span><span class="sxs-lookup"><span data-stu-id="84816-113">Remarks</span></span>  
 <span data-ttu-id="84816-114">如果目前的執行時間已系結至所有舊版 CLR 版本2啟用原則決策（例如，藉由在 `useLegacyV2RuntimeActivationPolicy` 設定檔中使用[ \< 啟動>](../../configure-apps/file-schema/startup/startup-element.md)專案上的屬性），則這個方法不會傳回錯誤結果，而是會 S_OK 結果，就像方法已成功系結舊版啟用原則一樣。</span><span class="sxs-lookup"><span data-stu-id="84816-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84816-115">需求</span><span class="sxs-lookup"><span data-stu-id="84816-115">Requirements</span></span>  
 <span data-ttu-id="84816-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84816-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84816-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="84816-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="84816-118">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="84816-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84816-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84816-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84816-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84816-120">See also</span></span>

- [<span data-ttu-id="84816-121">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="84816-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="84816-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="84816-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="84816-123">裝載</span><span class="sxs-lookup"><span data-stu-id="84816-123">Hosting</span></span>](index.md)
- [<span data-ttu-id="84816-124">\<啟動> 元素</span><span class="sxs-lookup"><span data-stu-id="84816-124">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
