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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616992"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="05ddd-102">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="05ddd-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="05ddd-103">提供的方法可讓主機設定錯誤報表的自訂堆疊傾印。</span><span class="sxs-lookup"><span data-stu-id="05ddd-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05ddd-104">方法</span><span class="sxs-lookup"><span data-stu-id="05ddd-104">Methods</span></span>  
  
|<span data-ttu-id="05ddd-105">方法</span><span class="sxs-lookup"><span data-stu-id="05ddd-105">Method</span></span>|<span data-ttu-id="05ddd-106">描述</span><span class="sxs-lookup"><span data-stu-id="05ddd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05ddd-107">BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="05ddd-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="05ddd-108">指定錯誤報表的自訂堆疊傾印設定。</span><span class="sxs-lookup"><span data-stu-id="05ddd-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="05ddd-109">EndCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="05ddd-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="05ddd-110">清除先前呼叫所設定的自訂堆疊傾印設定 `BeginCustomDump` 。</span><span class="sxs-lookup"><span data-stu-id="05ddd-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="05ddd-111">GetBucketParametersForCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="05ddd-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="05ddd-112">取得呼叫執行緒上目前例外狀況的 Watson 值區。</span><span class="sxs-lookup"><span data-stu-id="05ddd-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05ddd-113">備註</span><span class="sxs-lookup"><span data-stu-id="05ddd-113">Remarks</span></span>  
 <span data-ttu-id="05ddd-114">`BeginCustomDump`方法會設定自訂堆疊傾印設定。</span><span class="sxs-lookup"><span data-stu-id="05ddd-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="05ddd-115">`EndCustomDump`方法會清除自訂堆疊傾印設定，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="05ddd-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="05ddd-116">它應該在自訂傾印完成後呼叫。</span><span class="sxs-lookup"><span data-stu-id="05ddd-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="05ddd-117">呼叫失敗 `EndCustomDump` 會造成記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="05ddd-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ddd-118">需求</span><span class="sxs-lookup"><span data-stu-id="05ddd-118">Requirements</span></span>  
 <span data-ttu-id="05ddd-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="05ddd-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ddd-120">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="05ddd-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05ddd-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="05ddd-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05ddd-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ddd-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ddd-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05ddd-123">See also</span></span>

- [<span data-ttu-id="05ddd-124">ECustomDumpItemKind 列舉</span><span class="sxs-lookup"><span data-stu-id="05ddd-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="05ddd-125">裝載介面</span><span class="sxs-lookup"><span data-stu-id="05ddd-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
