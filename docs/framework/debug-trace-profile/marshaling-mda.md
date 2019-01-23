---
title: 封送處理 MDA
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37351dadf941e3512249dd8a9f433b63065ae1fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626884"
---
# <a name="marshaling-mda"></a><span data-ttu-id="1c667-102">封送處理 MDA</span><span class="sxs-lookup"><span data-stu-id="1c667-102">marshaling MDA</span></span>
<span data-ttu-id="1c667-103">當 CLR 設定方法參數或結構之欄位的封送處理資訊時，會啟動 `marshaling` managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="1c667-103">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="1c667-104">此 MDA 不適用於 JIT 編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="1c667-104">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1c667-105">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="1c667-105">Effect on the Runtime</span></span>  
 <span data-ttu-id="1c667-106">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="1c667-106">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1c667-107">輸出</span><span class="sxs-lookup"><span data-stu-id="1c667-107">Output</span></span>  
 <span data-ttu-id="1c667-108">MDA 會顯示在 managed 和 unmanaged 內容的參數或欄位類型，以及包含類型的結構或方法。</span><span class="sxs-lookup"><span data-stu-id="1c667-108">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="1c667-109">以下是欄位輸出的範例：</span><span class="sxs-lookup"><span data-stu-id="1c667-109">The following is an example of the output for a field:</span></span>  
  
```  
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="1c667-110">組態</span><span class="sxs-lookup"><span data-stu-id="1c667-110">Configuration</span></span>  
 <span data-ttu-id="1c667-111">MDA 組態可讓您根據相關的欄位或方法名稱篩選報告的封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="1c667-111">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="1c667-112">下列範例顯示如何使用 `methodFilter``fieldFilter` 和 `match` 項目以指定篩選條件。</span><span class="sxs-lookup"><span data-stu-id="1c667-112">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="1c667-113">將 `name` 屬性設定為星號 (\*) 會比對所有項目。</span><span class="sxs-lookup"><span data-stu-id="1c667-113">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c667-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c667-114">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="1c667-115">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="1c667-115">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="1c667-116">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="1c667-116">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
