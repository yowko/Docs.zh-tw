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
ms.openlocfilehash: ca33c8eb5e214cdaaa49905c311fd62042285d4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569281"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="409c0-102">ICorConfiguration::AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="409c0-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="409c0-103">表示特定的執行緒都應該可以繼續執行，而偵錯工具已在 managed 或 unmanaged 偵錯的情況下停止應用程式執行偵錯服務。</span><span class="sxs-lookup"><span data-stu-id="409c0-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="409c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="409c0-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="409c0-105">參數</span><span class="sxs-lookup"><span data-stu-id="409c0-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="409c0-106">[in]應該允許繼續執行的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="409c0-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="409c0-107">備註</span><span class="sxs-lookup"><span data-stu-id="409c0-107">Remarks</span></span>  
 <span data-ttu-id="409c0-108">指定的執行緒不會允許執行 managed 程式碼，或輸入以任何方式的執行階段。</span><span class="sxs-lookup"><span data-stu-id="409c0-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="409c0-109">在這類執行緒的範例是以支援舊版指令碼偵錯工具在處理序執行緒。</span><span class="sxs-lookup"><span data-stu-id="409c0-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="409c0-110">需求</span><span class="sxs-lookup"><span data-stu-id="409c0-110">Requirements</span></span>  
 <span data-ttu-id="409c0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="409c0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="409c0-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="409c0-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="409c0-113">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="409c0-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="409c0-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="409c0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="409c0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="409c0-115">See also</span></span>
- [<span data-ttu-id="409c0-116">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="409c0-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
