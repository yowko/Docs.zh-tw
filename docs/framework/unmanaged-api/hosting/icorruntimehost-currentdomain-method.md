---
title: ICorRuntimeHost::CurrentDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
ms.openlocfilehash: 33d56354a560949b2f451df9ef82d4f433951195
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715559"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="a0d19-102">ICorRuntimeHost::CurrentDomain 方法</span><span class="sxs-lookup"><span data-stu-id="a0d19-102">ICorRuntimeHost::CurrentDomain Method</span></span>

<span data-ttu-id="a0d19-103">取得型別的介面指標 <xref:System.AppDomain?displayProperty=nameWithType> ，代表在目前線程上載入的網域。</span><span class="sxs-lookup"><span data-stu-id="a0d19-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0d19-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0d19-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0d19-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0d19-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="a0d19-106">擴展型別的指標 <xref:System.AppDomain?displayProperty=nameWithType> ，表示執行緒目前的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="a0d19-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="a0d19-107">這個指標是輸入的 `IUnknown` ，因此呼叫端通常應該呼叫 `QueryInterface` 以取得型別的指標 <xref:System._AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="a0d19-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0d19-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a0d19-108">Return Value</span></span>  
  
|<span data-ttu-id="a0d19-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0d19-109">HRESULT</span></span>|<span data-ttu-id="a0d19-110">描述</span><span class="sxs-lookup"><span data-stu-id="a0d19-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0d19-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0d19-111">S_OK</span></span>|<span data-ttu-id="a0d19-112">作業成功。</span><span class="sxs-lookup"><span data-stu-id="a0d19-112">The operation was successful.</span></span>|  
|<span data-ttu-id="a0d19-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a0d19-113">S_FALSE</span></span>|<span data-ttu-id="a0d19-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="a0d19-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a0d19-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a0d19-115">E_FAIL</span></span>|<span data-ttu-id="a0d19-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a0d19-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a0d19-117">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="a0d19-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a0d19-118">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a0d19-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a0d19-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a0d19-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a0d19-120">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a0d19-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0d19-121">需求</span><span class="sxs-lookup"><span data-stu-id="a0d19-121">Requirements</span></span>  

 <span data-ttu-id="a0d19-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0d19-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0d19-123">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a0d19-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0d19-124">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a0d19-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0d19-125">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="a0d19-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d19-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0d19-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="a0d19-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a0d19-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
