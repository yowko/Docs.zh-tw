---
title: "ICLRMetaHost::ExitProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.ExitProcess
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10fb9bef99a90a76ea5bb1f4abe73cd756717285
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="8c78a-102">ICLRMetaHost::ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="8c78a-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="8c78a-103">嘗試關閉所有已載入的執行階段依正常程序，再終止處理序。</span><span class="sxs-lookup"><span data-stu-id="8c78a-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="8c78a-104">取代[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="8c78a-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c78a-105">語法</span><span class="sxs-lookup"><span data-stu-id="8c78a-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c78a-106">參數</span><span class="sxs-lookup"><span data-stu-id="8c78a-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="8c78a-107">[in]處理序結束代碼。</span><span class="sxs-lookup"><span data-stu-id="8c78a-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c78a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8c78a-108">Return Value</span></span>  
 <span data-ttu-id="8c78a-109">這個方法絕不會傳回，因此它的傳回值是未定義。</span><span class="sxs-lookup"><span data-stu-id="8c78a-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c78a-110">備註</span><span class="sxs-lookup"><span data-stu-id="8c78a-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c78a-111">需求</span><span class="sxs-lookup"><span data-stu-id="8c78a-111">Requirements</span></span>  
 <span data-ttu-id="8c78a-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c78a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c78a-113">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8c78a-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8c78a-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8c78a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c78a-115">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c78a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c78a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c78a-116">See Also</span></span>  
 [<span data-ttu-id="8c78a-117">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="8c78a-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="8c78a-118">裝載</span><span class="sxs-lookup"><span data-stu-id="8c78a-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
