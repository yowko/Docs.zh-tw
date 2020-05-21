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
ms.openlocfilehash: a23083777d0cd5965511f3689578a60220008420
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762226"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="75262-102">ICorRuntimeHost::GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="75262-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="75262-103">取得類型的介面指標 <xref:System._AppDomain?displayProperty=nameWithType> ，表示目前進程的預設網域。</span><span class="sxs-lookup"><span data-stu-id="75262-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75262-104">語法</span><span class="sxs-lookup"><span data-stu-id="75262-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75262-105">參數</span><span class="sxs-lookup"><span data-stu-id="75262-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="75262-106">脫銷實例類型的介面指標， <xref:System._AppDomain?displayProperty=nameWithType> <xref:System.AppDomain> 表示進程的預設應用程式域。</span><span class="sxs-lookup"><span data-stu-id="75262-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="75262-107">這個指標具有類型 `IUnknown` ，因此呼叫端通常會呼叫 `QueryInterface` 來取得類型的介面指標 <xref:System._AppDomain?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="75262-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75262-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="75262-108">Return Value</span></span>  
  
|<span data-ttu-id="75262-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75262-109">HRESULT</span></span>|<span data-ttu-id="75262-110">Description</span><span class="sxs-lookup"><span data-stu-id="75262-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75262-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="75262-111">S_OK</span></span>|<span data-ttu-id="75262-112">作業成功。</span><span class="sxs-lookup"><span data-stu-id="75262-112">The operation was successful.</span></span>|  
|<span data-ttu-id="75262-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="75262-113">S_FALSE</span></span>|<span data-ttu-id="75262-114">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="75262-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="75262-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="75262-115">E_FAIL</span></span>|<span data-ttu-id="75262-116">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="75262-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="75262-117">如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。</span><span class="sxs-lookup"><span data-stu-id="75262-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="75262-118">後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="75262-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="75262-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="75262-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="75262-120">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="75262-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75262-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="75262-121">Requirements</span></span>  
 <span data-ttu-id="75262-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75262-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75262-123">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="75262-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75262-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="75262-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75262-125">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="75262-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75262-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75262-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="75262-127">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="75262-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
