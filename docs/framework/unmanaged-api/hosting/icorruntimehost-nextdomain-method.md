---
title: ICorRuntimeHost::NextDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 598c46d50d7b4a67c1b2c0d844c9b12deb12a428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671365"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="19f85-102">ICorRuntimeHost::NextDomain 方法</span><span class="sxs-lookup"><span data-stu-id="19f85-102">ICorRuntimeHost::NextDomain Method</span></span>

<span data-ttu-id="19f85-103">取得列舉中下一個網域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="19f85-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f85-104">語法</span><span class="sxs-lookup"><span data-stu-id="19f85-104">Syntax</span></span>  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19f85-105">參數</span><span class="sxs-lookup"><span data-stu-id="19f85-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="19f85-106">在透過呼叫 [EnumDomains](icorruntimehost-enumdomains-method.md)取得的列舉值。</span><span class="sxs-lookup"><span data-stu-id="19f85-106">[in] The enumerator that was obtained through a call to [EnumDomains](icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="19f85-107">擴展型別的介面指標 <xref:System._AppDomain?displayProperty=nameWithType> ，表示列舉中的下一個定義域，如果沒有其他定義域存在，則為 null。</span><span class="sxs-lookup"><span data-stu-id="19f85-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19f85-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="19f85-108">Return Value</span></span>  
  
|<span data-ttu-id="19f85-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19f85-109">HRESULT</span></span>|<span data-ttu-id="19f85-110">描述</span><span class="sxs-lookup"><span data-stu-id="19f85-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19f85-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="19f85-111">S_OK</span></span>|<span data-ttu-id="19f85-112">作業成功。</span><span class="sxs-lookup"><span data-stu-id="19f85-112">The operation was successful.</span></span>|  
|<span data-ttu-id="19f85-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="19f85-113">S_FALSE</span></span>|<span data-ttu-id="19f85-114">作業無法完成，或列舉中沒有其他網域。</span><span class="sxs-lookup"><span data-stu-id="19f85-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="19f85-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19f85-115">E_FAIL</span></span>|<span data-ttu-id="19f85-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="19f85-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="19f85-117">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="19f85-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="19f85-118">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="19f85-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="19f85-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19f85-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19f85-120">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="19f85-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19f85-121">需求</span><span class="sxs-lookup"><span data-stu-id="19f85-121">Requirements</span></span>  

 <span data-ttu-id="19f85-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19f85-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19f85-123">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="19f85-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19f85-124">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="19f85-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19f85-125">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="19f85-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f85-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19f85-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="19f85-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="19f85-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
