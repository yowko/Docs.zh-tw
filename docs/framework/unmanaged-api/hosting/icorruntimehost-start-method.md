---
title: ICorRuntimeHost::Start 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: bc647ad025b5e22187b476383ed0128761cb632f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721032"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="29d34-102">ICorRuntimeHost::Start 方法</span><span class="sxs-lookup"><span data-stu-id="29d34-102">ICorRuntimeHost::Start Method</span></span>

<span data-ttu-id="29d34-103">啟動 common language runtime (CLR) 。</span><span class="sxs-lookup"><span data-stu-id="29d34-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d34-104">語法</span><span class="sxs-lookup"><span data-stu-id="29d34-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="29d34-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="29d34-105">Return Value</span></span>  
  
|<span data-ttu-id="29d34-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29d34-106">HRESULT</span></span>|<span data-ttu-id="29d34-107">描述</span><span class="sxs-lookup"><span data-stu-id="29d34-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29d34-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="29d34-108">S_OK</span></span>|<span data-ttu-id="29d34-109">作業成功。</span><span class="sxs-lookup"><span data-stu-id="29d34-109">The operation was successful.</span></span>|  
|<span data-ttu-id="29d34-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="29d34-110">S_FALSE</span></span>|<span data-ttu-id="29d34-111">作業無法完成。</span><span class="sxs-lookup"><span data-stu-id="29d34-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="29d34-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29d34-112">E_FAIL</span></span>|<span data-ttu-id="29d34-113">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="29d34-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="29d34-114">如果方法傳回 E_FAIL，則 CLR 在進程中已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="29d34-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="29d34-115">對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="29d34-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="29d34-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29d34-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29d34-117">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="29d34-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29d34-118">備註</span><span class="sxs-lookup"><span data-stu-id="29d34-118">Remarks</span></span>  

 <span data-ttu-id="29d34-119">通常不需要呼叫 `Start` 方法，因為 CLR 會在第一次執行 managed 程式碼的要求時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="29d34-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d34-120">需求</span><span class="sxs-lookup"><span data-stu-id="29d34-120">Requirements</span></span>  

 <span data-ttu-id="29d34-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29d34-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29d34-122">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="29d34-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29d34-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="29d34-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29d34-124">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="29d34-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d34-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29d34-125">See also</span></span>

- [<span data-ttu-id="29d34-126">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="29d34-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
