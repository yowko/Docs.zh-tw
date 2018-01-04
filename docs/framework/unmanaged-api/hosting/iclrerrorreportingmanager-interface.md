---
title: "ICLRErrorReportingManager 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager
helpviewer_keywords: ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ac362432a5d0c613f4ee1409ee15d92bfef3aeb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="5c4ad-102">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="5c4ad-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="5c4ad-103">提供方法，讓主應用程式設定錯誤報告的自訂堆疊傾印。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c4ad-104">方法</span><span class="sxs-lookup"><span data-stu-id="5c4ad-104">Methods</span></span>  
  
|<span data-ttu-id="5c4ad-105">方法</span><span class="sxs-lookup"><span data-stu-id="5c4ad-105">Method</span></span>|<span data-ttu-id="5c4ad-106">描述</span><span class="sxs-lookup"><span data-stu-id="5c4ad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c4ad-107">BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="5c4ad-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="5c4ad-108">指定錯誤報告的自訂堆疊傾印的組態。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="5c4ad-109">EndCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="5c4ad-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="5c4ad-110">清除之前呼叫所設定的自訂堆疊傾印組態`BeginCustomDump`。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="5c4ad-111">GetBucketParametersForCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="5c4ad-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="5c4ad-112">取得目前的例外狀況呼叫的執行緒上的 Watson 貯體。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c4ad-113">備註</span><span class="sxs-lookup"><span data-stu-id="5c4ad-113">Remarks</span></span>  
 <span data-ttu-id="5c4ad-114">`BeginCustomDump`方法設定自訂的堆疊傾印組態。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="5c4ad-115">`EndCustomDump`方法清除自訂堆疊傾印組態，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="5c4ad-116">它應該呼叫自訂的傾印完成後。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5c4ad-117">無法呼叫`EndCustomDump`會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c4ad-118">需求</span><span class="sxs-lookup"><span data-stu-id="5c4ad-118">Requirements</span></span>  
 <span data-ttu-id="5c4ad-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c4ad-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c4ad-120">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5c4ad-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5c4ad-121">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5c4ad-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c4ad-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c4ad-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4ad-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c4ad-123">See Also</span></span>  
 [<span data-ttu-id="5c4ad-124">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="5c4ad-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="5c4ad-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="5c4ad-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
