---
title: ICLRMetaHostPolicy 介面
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: 515b73b019c683bd3e5aa3b895ee5623e75e4ad0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707603"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="94c96-102">ICLRMetaHostPolicy 介面</span><span class="sxs-lookup"><span data-stu-id="94c96-102">ICLRMetaHostPolicy Interface</span></span>

<span data-ttu-id="94c96-103">提供 [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) 方法，此方法會根據原則準則、managed 元件、版本和設定檔案，將指標傳回給 common language RUNTIME (CLR) 介面。</span><span class="sxs-lookup"><span data-stu-id="94c96-103">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94c96-104">方法</span><span class="sxs-lookup"><span data-stu-id="94c96-104">Methods</span></span>  
  
|<span data-ttu-id="94c96-105">方法</span><span class="sxs-lookup"><span data-stu-id="94c96-105">Method</span></span>|<span data-ttu-id="94c96-106">描述</span><span class="sxs-lookup"><span data-stu-id="94c96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94c96-107">GetRequestedRuntime 方法</span><span class="sxs-lookup"><span data-stu-id="94c96-107">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="94c96-108">根據原則準則、managed 元件、版本和設定檔提供慣用的 CLR 介面。</span><span class="sxs-lookup"><span data-stu-id="94c96-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94c96-109">備註</span><span class="sxs-lookup"><span data-stu-id="94c96-109">Remarks</span></span>  

 <span data-ttu-id="94c96-110">您可以藉由呼叫 [CLRCreateInstance](clrcreateinstance-function.md) 函數來取得此介面的參考，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="94c96-110">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="94c96-111">這個介面不會實際載入或啟用 CLR，而只會根據已安裝或載入的可用版本傳回慣用的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="94c96-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="94c96-112">.NET Framework 4 裝載 API 會合並原則，讓具有特定需求的主機可以使用基本功能，而不會產生非預期的懲罰。</span><span class="sxs-lookup"><span data-stu-id="94c96-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="94c96-113">例如，許多 MSCorEE.dll 的匯出都會系結至特定的 CLR，雖然方法可能不會以邏輯方式要求它。</span><span class="sxs-lookup"><span data-stu-id="94c96-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="94c96-114">[METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md)列舉會提供大多數主機通用的系結原則。</span><span class="sxs-lookup"><span data-stu-id="94c96-114">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c96-115">需求</span><span class="sxs-lookup"><span data-stu-id="94c96-115">Requirements</span></span>  

 <span data-ttu-id="94c96-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94c96-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94c96-117">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="94c96-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="94c96-118">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="94c96-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94c96-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94c96-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c96-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94c96-120">See also</span></span>

- [<span data-ttu-id="94c96-121">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="94c96-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="94c96-122">裝載介面</span><span class="sxs-lookup"><span data-stu-id="94c96-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="94c96-123">裝載</span><span class="sxs-lookup"><span data-stu-id="94c96-123">Hosting</span></span>](index.md)
