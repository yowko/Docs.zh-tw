---
title: pInvokeLog MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 343ec424105d1c775592aba316b50da4010f7c8b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="pinvokelog-mda"></a><span data-ttu-id="3a8d9-102">pInvokeLog MDA</span><span class="sxs-lookup"><span data-stu-id="3a8d9-102">pInvokeLog MDA</span></span>
<span data-ttu-id="3a8d9-103">針對執行期間所使用的每個唯一平台叫用簽章，啟用 `pInvokeLog` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="3a8d9-103">The `pInvokeLog` managed debugging assistant (MDA) is activated for each unique platform invoke signature used during execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3a8d9-104">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="3a8d9-104">Effect on the Runtime</span></span>  
 <span data-ttu-id="3a8d9-105">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="3a8d9-105">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3a8d9-106">輸出</span><span class="sxs-lookup"><span data-stu-id="3a8d9-106">Output</span></span>  
 <span data-ttu-id="3a8d9-107">指出在執行期間使用平台叫用簽章的訊息。</span><span class="sxs-lookup"><span data-stu-id="3a8d9-107">A message indicating the platform invoke signature used during execution.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3a8d9-108">組態</span><span class="sxs-lookup"><span data-stu-id="3a8d9-108">Configuration</span></span>  
 <span data-ttu-id="3a8d9-109">每個 match 項目都會篩選要對其進行平台叫用呼叫的 .dll 檔案。</span><span class="sxs-lookup"><span data-stu-id="3a8d9-109">Each match element filters the .dll files to which platform invoke calls are made.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a8d9-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a8d9-110">See Also</span></span>  
 [<span data-ttu-id="3a8d9-111">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="3a8d9-111">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="3a8d9-112">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="3a8d9-112">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
