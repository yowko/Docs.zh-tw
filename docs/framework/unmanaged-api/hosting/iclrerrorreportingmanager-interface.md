---
title: ICLRErrorReportingManager 介面
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d10fe0240073464e3c2677343288e5379840885d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732787"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="dab2a-102">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="dab2a-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="dab2a-103">提供方法，可讓主應用程式設定錯誤報告的自訂堆疊傾印。</span><span class="sxs-lookup"><span data-stu-id="dab2a-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dab2a-104">方法</span><span class="sxs-lookup"><span data-stu-id="dab2a-104">Methods</span></span>  
  
|<span data-ttu-id="dab2a-105">方法</span><span class="sxs-lookup"><span data-stu-id="dab2a-105">Method</span></span>|<span data-ttu-id="dab2a-106">描述</span><span class="sxs-lookup"><span data-stu-id="dab2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dab2a-107">BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="dab2a-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="dab2a-108">指定錯誤報告的自訂的堆疊傾印的組態。</span><span class="sxs-lookup"><span data-stu-id="dab2a-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="dab2a-109">EndCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="dab2a-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="dab2a-110">清除先前呼叫所設定的自訂堆疊傾印組態`BeginCustomDump`。</span><span class="sxs-lookup"><span data-stu-id="dab2a-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="dab2a-111">GetBucketParametersForCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="dab2a-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="dab2a-112">取得目前的例外狀況，在呼叫執行緒上的 Watson 值區。</span><span class="sxs-lookup"><span data-stu-id="dab2a-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dab2a-113">備註</span><span class="sxs-lookup"><span data-stu-id="dab2a-113">Remarks</span></span>  
 <span data-ttu-id="dab2a-114">`BeginCustomDump`方法會設定自訂的堆疊傾印組態。</span><span class="sxs-lookup"><span data-stu-id="dab2a-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="dab2a-115">`EndCustomDump`方法會清除自訂堆疊傾印組態，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="dab2a-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="dab2a-116">自訂的傾印完成之後，應該會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="dab2a-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dab2a-117">無法呼叫`EndCustomDump`會造成記憶體遺漏。</span><span class="sxs-lookup"><span data-stu-id="dab2a-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab2a-118">需求</span><span class="sxs-lookup"><span data-stu-id="dab2a-118">Requirements</span></span>  
 <span data-ttu-id="dab2a-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dab2a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab2a-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dab2a-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dab2a-121">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dab2a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dab2a-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab2a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab2a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dab2a-123">See also</span></span>
- [<span data-ttu-id="dab2a-124">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="dab2a-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="dab2a-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="dab2a-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
