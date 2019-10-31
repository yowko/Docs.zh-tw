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
ms.openlocfilehash: 49a60b6b9b076138d8ff1f8a15041e9a6bacfede
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129247"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="97ccc-102">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="97ccc-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="97ccc-103">提供的方法可讓主機設定錯誤報表的自訂堆疊傾印。</span><span class="sxs-lookup"><span data-stu-id="97ccc-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97ccc-104">方法</span><span class="sxs-lookup"><span data-stu-id="97ccc-104">Methods</span></span>  
  
|<span data-ttu-id="97ccc-105">方法</span><span class="sxs-lookup"><span data-stu-id="97ccc-105">Method</span></span>|<span data-ttu-id="97ccc-106">描述</span><span class="sxs-lookup"><span data-stu-id="97ccc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97ccc-107">BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="97ccc-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="97ccc-108">指定錯誤報表的自訂堆疊傾印設定。</span><span class="sxs-lookup"><span data-stu-id="97ccc-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="97ccc-109">EndCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="97ccc-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="97ccc-110">清除先前呼叫 `BeginCustomDump`所設定的自訂堆疊傾印設定。</span><span class="sxs-lookup"><span data-stu-id="97ccc-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="97ccc-111">GetBucketParametersForCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="97ccc-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="97ccc-112">取得呼叫執行緒上目前例外狀況的 Watson 值區。</span><span class="sxs-lookup"><span data-stu-id="97ccc-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97ccc-113">備註</span><span class="sxs-lookup"><span data-stu-id="97ccc-113">Remarks</span></span>  
 <span data-ttu-id="97ccc-114">`BeginCustomDump` 方法會設定自訂堆疊傾印設定。</span><span class="sxs-lookup"><span data-stu-id="97ccc-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="97ccc-115">`EndCustomDump` 方法會清除自訂堆疊傾印設定，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="97ccc-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="97ccc-116">它應該在自訂傾印完成後呼叫。</span><span class="sxs-lookup"><span data-stu-id="97ccc-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="97ccc-117">無法呼叫 `EndCustomDump` 會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="97ccc-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97ccc-118">需求</span><span class="sxs-lookup"><span data-stu-id="97ccc-118">Requirements</span></span>  
 <span data-ttu-id="97ccc-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97ccc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97ccc-120">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="97ccc-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97ccc-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="97ccc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97ccc-122">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97ccc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97ccc-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="97ccc-123">See also</span></span>

- [<span data-ttu-id="97ccc-124">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="97ccc-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="97ccc-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="97ccc-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
