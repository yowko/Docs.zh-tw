---
title: ICorRuntimeHost::GetDefaultDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 673c32c86c808c36db6454b8a9f0d8e68f9b1258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720629"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="2c445-102">ICorRuntimeHost::GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2c445-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="2c445-103">取得型別的介面指標 <xref:System._AppDomain?displayProperty=nameWithType> ，表示目前進程的預設網域。</span><span class="sxs-lookup"><span data-stu-id="2c445-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c445-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c445-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c445-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c445-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="2c445-106">擴展實例的型別介面指標 <xref:System._AppDomain?displayProperty=nameWithType> <xref:System.AppDomain> ，表示進程的預設應用程式域。</span><span class="sxs-lookup"><span data-stu-id="2c445-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="2c445-107">這個指標是輸入的 `IUnknown` ，因此呼叫端通常應該呼叫 `QueryInterface` 以取得型別的介面指標 <xref:System._AppDomain?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2c445-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c445-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2c445-108">Return Value</span></span>  
  
|<span data-ttu-id="2c445-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c445-109">HRESULT</span></span>|<span data-ttu-id="2c445-110">描述</span><span class="sxs-lookup"><span data-stu-id="2c445-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c445-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c445-111">S_OK</span></span>|<span data-ttu-id="2c445-112">作業成功。</span><span class="sxs-lookup"><span data-stu-id="2c445-112">The operation was successful.</span></span>|  
|<span data-ttu-id="2c445-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2c445-113">S_FALSE</span></span>|<span data-ttu-id="2c445-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="2c445-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="2c445-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c445-115">E_FAIL</span></span>|<span data-ttu-id="2c445-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="2c445-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="2c445-117">如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="2c445-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="2c445-118">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="2c445-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2c445-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c445-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c445-120">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="2c445-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c445-121">需求</span><span class="sxs-lookup"><span data-stu-id="2c445-121">Requirements</span></span>  

 <span data-ttu-id="2c445-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c445-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c445-123">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2c445-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c445-124">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2c445-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c445-125">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="2c445-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c445-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c445-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="2c445-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2c445-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
