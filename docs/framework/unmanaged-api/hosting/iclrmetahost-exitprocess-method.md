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
ms.openlocfilehash: bbf3c00eafe47556c6b46e1acb687a19df5a2b28
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601750"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="e1ac0-102">ICLRMetaHost::ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="e1ac0-102">ICLRMetaHost::ExitProcess Method</span></span>
<span data-ttu-id="e1ac0-103">嘗試先關閉所有已載入的執行階段依正常程序，然後終止處理序。</span><span class="sxs-lookup"><span data-stu-id="e1ac0-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="e1ac0-104">會取代[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="e1ac0-104">Supersedes the [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ac0-105">語法</span><span class="sxs-lookup"><span data-stu-id="e1ac0-105">Syntax</span></span>  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1ac0-106">參數</span><span class="sxs-lookup"><span data-stu-id="e1ac0-106">Parameters</span></span>  
 `iExitCode`  
 <span data-ttu-id="e1ac0-107">[in]處理序結束代碼。</span><span class="sxs-lookup"><span data-stu-id="e1ac0-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1ac0-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1ac0-108">Return Value</span></span>  
 <span data-ttu-id="e1ac0-109">這個方法永遠不會傳回，因此它的傳回值會是未定義。</span><span class="sxs-lookup"><span data-stu-id="e1ac0-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1ac0-110">備註</span><span class="sxs-lookup"><span data-stu-id="e1ac0-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1ac0-111">需求</span><span class="sxs-lookup"><span data-stu-id="e1ac0-111">Requirements</span></span>  
 <span data-ttu-id="e1ac0-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1ac0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1ac0-113">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e1ac0-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e1ac0-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e1ac0-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1ac0-115">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1ac0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ac0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1ac0-116">See also</span></span>
- [<span data-ttu-id="e1ac0-117">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="e1ac0-117">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="e1ac0-118">裝載</span><span class="sxs-lookup"><span data-stu-id="e1ac0-118">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
