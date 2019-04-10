---
title: ICorConfiguration::AddDebuggerSpecialThread 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db1b19c1499f7e8a126933b4d0635a0ab73e72a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218585"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="6c656-102">ICorConfiguration::AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="6c656-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="6c656-103">表示特定的執行緒都應該可以繼續執行，而偵錯工具已在 managed 或 unmanaged 偵錯的情況下停止應用程式執行偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="6c656-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c656-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c656-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c656-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c656-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="6c656-106">[in]應該允許繼續執行的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="6c656-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c656-107">備註</span><span class="sxs-lookup"><span data-stu-id="6c656-107">Remarks</span></span>  
 <span data-ttu-id="6c656-108">指定的執行緒不會允許執行 managed 程式碼，或輸入以任何方式的執行階段。</span><span class="sxs-lookup"><span data-stu-id="6c656-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="6c656-109">在這類執行緒的範例是以支援舊版指令碼偵錯工具在處理序執行緒。</span><span class="sxs-lookup"><span data-stu-id="6c656-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c656-110">需求</span><span class="sxs-lookup"><span data-stu-id="6c656-110">Requirements</span></span>  
 <span data-ttu-id="6c656-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c656-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c656-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c656-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c656-113">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6c656-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6c656-114">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6c656-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6c656-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c656-115">See also</span></span>

- [<span data-ttu-id="6c656-116">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="6c656-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
