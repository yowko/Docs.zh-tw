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
ms.openlocfilehash: bd89db3fa0b1814a98b016fcf9d1aeeabfff718b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715845"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="1925e-102">ICorConfiguration::AddDebuggerSpecialThread 方法</span><span class="sxs-lookup"><span data-stu-id="1925e-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>

<span data-ttu-id="1925e-103">向偵錯工具表示，當偵錯工具在 managed 或非受控的偵測情節中停止應用程式時，應該允許特定執行緒繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1925e-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1925e-104">語法</span><span class="sxs-lookup"><span data-stu-id="1925e-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1925e-105">參數</span><span class="sxs-lookup"><span data-stu-id="1925e-105">Parameters</span></span>  

 `dwSpecialThreadId`  
 <span data-ttu-id="1925e-106">在應允許繼續執行的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="1925e-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1925e-107">備註</span><span class="sxs-lookup"><span data-stu-id="1925e-107">Remarks</span></span>  

 <span data-ttu-id="1925e-108">指定的執行緒將不允許執行 managed 程式碼，或以任何方式進入執行時間。</span><span class="sxs-lookup"><span data-stu-id="1925e-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="1925e-109">這類執行緒的範例就是支援舊版腳本偵錯工具的同進程執行緒。</span><span class="sxs-lookup"><span data-stu-id="1925e-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1925e-110">需求</span><span class="sxs-lookup"><span data-stu-id="1925e-110">Requirements</span></span>  

 <span data-ttu-id="1925e-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1925e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1925e-112">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1925e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1925e-113">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1925e-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1925e-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1925e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1925e-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1925e-115">See also</span></span>

- [<span data-ttu-id="1925e-116">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="1925e-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
