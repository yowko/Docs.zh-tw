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
ms.openlocfilehash: 6d601ac3ece801353b630c74ed852c2657f25d7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730458"
---
# <a name="iclrmetahostexitprocess-method"></a><span data-ttu-id="afb0d-102">ICLRMetaHost::ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="afb0d-102">ICLRMetaHost::ExitProcess Method</span></span>

<span data-ttu-id="afb0d-103">嘗試正常關閉所有載入的執行時間，然後終止進程。</span><span class="sxs-lookup"><span data-stu-id="afb0d-103">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="afb0d-104">取代 [CorExitProcess](corexitprocess-function.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="afb0d-104">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb0d-105">語法</span><span class="sxs-lookup"><span data-stu-id="afb0d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afb0d-106">參數</span><span class="sxs-lookup"><span data-stu-id="afb0d-106">Parameters</span></span>  

 `iExitCode`  
 <span data-ttu-id="afb0d-107">在進程的結束代碼。</span><span class="sxs-lookup"><span data-stu-id="afb0d-107">[in] The exit code for the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afb0d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="afb0d-108">Return Value</span></span>  

 <span data-ttu-id="afb0d-109">這個方法永遠不會傳回，因此它的傳回值是未定義的。</span><span class="sxs-lookup"><span data-stu-id="afb0d-109">This method never returns, so its return value is undefined.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afb0d-110">備註</span><span class="sxs-lookup"><span data-stu-id="afb0d-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb0d-111">需求</span><span class="sxs-lookup"><span data-stu-id="afb0d-111">Requirements</span></span>  

 <span data-ttu-id="afb0d-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="afb0d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb0d-113">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="afb0d-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="afb0d-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="afb0d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afb0d-115">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb0d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb0d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afb0d-116">See also</span></span>

- [<span data-ttu-id="afb0d-117">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="afb0d-117">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="afb0d-118">裝載</span><span class="sxs-lookup"><span data-stu-id="afb0d-118">Hosting</span></span>](index.md)
