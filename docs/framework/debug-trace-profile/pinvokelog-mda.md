---
title: pInvokeLog MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0883849eee12922601e50c2337bb0048d77cab68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052369"
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="9368e-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="9368e-102">pInvokeLog MDA</span></span>
<span data-ttu-id="9368e-103">針對執行期間所使用的每個唯一平台叫用簽章，啟用 `pInvokeLog` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="9368e-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="9368e-104">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="9368e-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="9368e-105">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="9368e-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="9368e-106">Output</span><span class="sxs-lookup"><span data-stu-id="9368e-106">Output</span></span>  
 <span data-ttu-id="9368e-107">指出在執行期間使用平台叫用簽章的訊息。</span><span class="sxs-lookup"><span data-stu-id="9368e-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9368e-108">組態</span><span class="sxs-lookup"><span data-stu-id="9368e-108">Configuration</span></span>  
 <span data-ttu-id="9368e-109">每個 match 項目都會篩選要對其進行平台叫用呼叫的 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="9368e-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9368e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9368e-110">See also</span></span>

- [<span data-ttu-id="9368e-111">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="9368e-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="9368e-112">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="9368e-112">Consuming Unmanaged DLL Functions</span></span>](../interop/consuming-unmanaged-dll-functions.md)
