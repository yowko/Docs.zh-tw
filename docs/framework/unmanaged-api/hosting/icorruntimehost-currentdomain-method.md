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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cb5ff5300a7fd2577e602b3077dd816cf7dfbe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181375"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="80e4e-102">ICorRuntimeHost::CurrentDomain 方法</span><span class="sxs-lookup"><span data-stu-id="80e4e-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="80e4e-103">取得類型的介面指標<xref:System.AppDomain?displayProperty=nameWithType>，代表目前執行緒上所載入的網域。</span><span class="sxs-lookup"><span data-stu-id="80e4e-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e4e-104">語法</span><span class="sxs-lookup"><span data-stu-id="80e4e-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80e4e-105">參數</span><span class="sxs-lookup"><span data-stu-id="80e4e-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="80e4e-106">[out]型別的指標<xref:System.AppDomain?displayProperty=nameWithType>表示執行緒的目前應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="80e4e-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="80e4e-107">這個指標型別`IUnknown`，所以通常應該呼叫的呼叫端`QueryInterface`若要取得類型的指標<xref:System._AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="80e4e-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80e4e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="80e4e-108">Return Value</span></span>  
  
|<span data-ttu-id="80e4e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80e4e-109">HRESULT</span></span>|<span data-ttu-id="80e4e-110">描述</span><span class="sxs-lookup"><span data-stu-id="80e4e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80e4e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="80e4e-111">S_OK</span></span>|<span data-ttu-id="80e4e-112">此作業成功。</span><span class="sxs-lookup"><span data-stu-id="80e4e-112">The operation was successful.</span></span>|  
|<span data-ttu-id="80e4e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="80e4e-113">S_FALSE</span></span>|<span data-ttu-id="80e4e-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="80e4e-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="80e4e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80e4e-115">E_FAIL</span></span>|<span data-ttu-id="80e4e-116">發生不明、 重大失敗。</span><span class="sxs-lookup"><span data-stu-id="80e4e-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="80e4e-117">如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。</span><span class="sxs-lookup"><span data-stu-id="80e4e-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="80e4e-118">任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="80e4e-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="80e4e-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80e4e-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80e4e-120">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="80e4e-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80e4e-121">需求</span><span class="sxs-lookup"><span data-stu-id="80e4e-121">Requirements</span></span>  
 <span data-ttu-id="80e4e-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80e4e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e4e-123">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80e4e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80e4e-124">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80e4e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80e4e-125">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="80e4e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e4e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e4e-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="80e4e-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="80e4e-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
