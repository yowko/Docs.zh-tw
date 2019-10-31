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
ms.openlocfilehash: c5d6cfa3826667514eb70f9bb0df118d9ba0d07c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127825"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="a74a0-102">ICorConfiguration::AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="a74a0-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="a74a0-103">向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測案例中停止時，應該允許特定執行緒繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a74a0-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a74a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a74a0-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a74a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="a74a0-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="a74a0-106">在應允許繼續執行之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a74a0-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a74a0-107">備註</span><span class="sxs-lookup"><span data-stu-id="a74a0-107">Remarks</span></span>  
 <span data-ttu-id="a74a0-108">指定的執行緒將不允許執行 managed 程式碼，或以任何方式進入執行時間。</span><span class="sxs-lookup"><span data-stu-id="a74a0-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="a74a0-109">這類執行緒的範例就是支援舊版腳本偵錯工具的同進程執行緒。</span><span class="sxs-lookup"><span data-stu-id="a74a0-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a74a0-110">需求</span><span class="sxs-lookup"><span data-stu-id="a74a0-110">Requirements</span></span>  
 <span data-ttu-id="a74a0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a74a0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a74a0-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a74a0-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a74a0-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a74a0-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a74a0-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a74a0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a74a0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a74a0-115">See also</span></span>

- [<span data-ttu-id="a74a0-116">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="a74a0-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
