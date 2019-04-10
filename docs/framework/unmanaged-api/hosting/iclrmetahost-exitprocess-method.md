---
title: ICLRMetaHost::ExitProcess 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64c212d064ad658678926690d1e680afe27c7c99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219235"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="1fab5-102">ICLRMetaHost::ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="1fab5-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="1fab5-103">嘗試先關閉所有已載入的執行階段依正常程序，然後終止處理序。</span><span class="sxs-lookup"><span data-stu-id="1fab5-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="1fab5-104">會取代[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="1fab5-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fab5-105">語法</span><span class="sxs-lookup"><span data-stu-id="1fab5-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fab5-106">參數</span><span class="sxs-lookup"><span data-stu-id="1fab5-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="1fab5-107">[in]處理序結束代碼。</span><span class="sxs-lookup"><span data-stu-id="1fab5-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1fab5-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1fab5-108">Return Value</span></span>  
 <span data-ttu-id="1fab5-109">這個方法永遠不會傳回，因此它的傳回值會是未定義。</span><span class="sxs-lookup"><span data-stu-id="1fab5-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fab5-110">備註</span><span class="sxs-lookup"><span data-stu-id="1fab5-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fab5-111">需求</span><span class="sxs-lookup"><span data-stu-id="1fab5-111">Requirements</span></span>  
 <span data-ttu-id="1fab5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1fab5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fab5-113">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1fab5-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1fab5-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1fab5-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1fab5-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="1fab5-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1fab5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fab5-116">See also</span></span>

- [<span data-ttu-id="1fab5-117">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="1fab5-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="1fab5-118">裝載</span><span class="sxs-lookup"><span data-stu-id="1fab5-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
