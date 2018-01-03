---
title: "封送處理 MDA"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83b621f78e3ba4641540f6125ed14d600cc292d1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-mda"></a><span data-ttu-id="81eed-102">封送處理 MDA</span><span class="sxs-lookup"><span data-stu-id="81eed-102">marshaling MDA</span></span>
<span data-ttu-id="81eed-103">當 CLR 設定方法參數或結構之欄位的封送處理資訊時，會啟動 `marshaling` managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="81eed-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="81eed-104">此 MDA 不適用於 JIT 編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="81eed-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="81eed-105">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="81eed-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="81eed-106">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="81eed-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="81eed-107">輸出</span><span class="sxs-lookup"><span data-stu-id="81eed-107">Output</span></span>  
 <span data-ttu-id="81eed-108">MDA 會顯示在 managed 和 unmanaged 內容的參數或欄位類型，以及包含類型的結構或方法。</span><span class="sxs-lookup"><span data-stu-id="81eed-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="81eed-109">以下是欄位輸出的範例：</span><span class="sxs-lookup"><span data-stu-id="81eed-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="81eed-110">組態</span><span class="sxs-lookup"><span data-stu-id="81eed-110">Configuration</span></span>  
 <span data-ttu-id="81eed-111">MDA 組態可讓您根據相關的欄位或方法名稱篩選報告的封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="81eed-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="81eed-112">下列範例顯示如何使用 `methodFilter``fieldFilter` 和 `match` 項目以指定篩選條件。</span><span class="sxs-lookup"><span data-stu-id="81eed-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="81eed-113">將 `name` 屬性設定為星號 (*) 會比對所有項目。</span><span class="sxs-lookup"><span data-stu-id="81eed-113">Setting the `name` attribute to an asterisk (*) will match everything.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshaling>  
      <methodFilter>  
        <match name="Method1"/>  
        <match name="Method2"/>  
      </methodFilter>  
      <fieldFilter>  
        <match name="Field1"/>  
        <match name="Field2"/>  
       </fieldFilter>  
    </marshaling>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81eed-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="81eed-114">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="81eed-115">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="81eed-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="81eed-116">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="81eed-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
