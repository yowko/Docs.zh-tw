---
title: pInvokeLog MDA
description: 瞭解 pInvokeLog managed 偵錯工具 (MDA) ，其會針對在 .NET 中執行期間所使用的每個唯一平台叫用簽章啟用。
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: b8cb4805663a2b28a133f98503730199af695c4f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271456"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="cd792-103">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="cd792-103">pInvokeLog MDA</span></span>

<span data-ttu-id="cd792-104">針對執行期間所使用的每個唯一平台叫用簽章，啟用 `pInvokeLog` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="cd792-104">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="cd792-105">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="cd792-105">Effect on the Runtime</span></span>  

 <span data-ttu-id="cd792-106">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="cd792-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="cd792-107">輸出</span><span class="sxs-lookup"><span data-stu-id="cd792-107">Output</span></span>  

 <span data-ttu-id="cd792-108">指出在執行期間使用平台叫用簽章的訊息。</span><span class="sxs-lookup"><span data-stu-id="cd792-108">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="cd792-109">設定</span><span class="sxs-lookup"><span data-stu-id="cd792-109">Configuration</span></span>  

 <span data-ttu-id="cd792-110">每個 match 項目都會篩選要對其進行平台叫用呼叫的 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="cd792-110">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd792-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd792-111">See also</span></span>

- [<span data-ttu-id="cd792-112">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="cd792-112">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="cd792-113">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="cd792-113">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
