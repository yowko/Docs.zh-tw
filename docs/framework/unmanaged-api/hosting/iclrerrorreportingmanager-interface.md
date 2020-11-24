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
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677835"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="577dc-102">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="577dc-102">ICLRErrorReportingManager Interface</span></span>

<span data-ttu-id="577dc-103">提供可讓主機針對錯誤報表設定自訂堆疊傾印的方法。</span><span class="sxs-lookup"><span data-stu-id="577dc-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="577dc-104">方法</span><span class="sxs-lookup"><span data-stu-id="577dc-104">Methods</span></span>  
  
|<span data-ttu-id="577dc-105">方法</span><span class="sxs-lookup"><span data-stu-id="577dc-105">Method</span></span>|<span data-ttu-id="577dc-106">描述</span><span class="sxs-lookup"><span data-stu-id="577dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="577dc-107">BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="577dc-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="577dc-108">針對錯誤報表，指定自訂堆疊傾印的設定。</span><span class="sxs-lookup"><span data-stu-id="577dc-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="577dc-109">EndCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="577dc-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="577dc-110">清除先前呼叫所設定的自訂堆疊傾印設定 `BeginCustomDump` 。</span><span class="sxs-lookup"><span data-stu-id="577dc-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="577dc-111">GetBucketParametersForCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="577dc-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="577dc-112">取得目前例外狀況在呼叫執行緒上的 Watson 值區。</span><span class="sxs-lookup"><span data-stu-id="577dc-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="577dc-113">備註</span><span class="sxs-lookup"><span data-stu-id="577dc-113">Remarks</span></span>  

 <span data-ttu-id="577dc-114">`BeginCustomDump`方法會設定自訂堆疊傾印設定。</span><span class="sxs-lookup"><span data-stu-id="577dc-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="577dc-115">`EndCustomDump`方法會清除自訂堆疊傾印設定，並釋出任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="577dc-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="577dc-116">它應該在自訂傾印完成後呼叫。</span><span class="sxs-lookup"><span data-stu-id="577dc-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="577dc-117">呼叫失敗 `EndCustomDump` 會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="577dc-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="577dc-118">需求</span><span class="sxs-lookup"><span data-stu-id="577dc-118">Requirements</span></span>  

 <span data-ttu-id="577dc-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="577dc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="577dc-120">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="577dc-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="577dc-121">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="577dc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="577dc-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="577dc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="577dc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="577dc-123">See also</span></span>

- [<span data-ttu-id="577dc-124">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="577dc-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="577dc-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="577dc-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
