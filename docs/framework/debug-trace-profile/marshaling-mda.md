---
title: 封送處理 MDA
description: 請參閱封送處理 managed 偵錯工具 (MDA) ，如果 CLR 為方法參數或結構欄位設定封送處理資訊，則會叫用此方法。
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, run-time errors
- marshaling MDA
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: 5433b1f8-b0e5-40c9-a49a-0e5bd213363d
ms.openlocfilehash: afe54a2104e05f8fad57c7cbba4988b013aff761
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271170"
---
# <a name="marshaling-mda"></a><span data-ttu-id="0aace-103">封送處理 MDA</span><span class="sxs-lookup"><span data-stu-id="0aace-103">marshaling MDA</span></span>

<span data-ttu-id="0aace-104">當 CLR 設定方法參數或結構之欄位的封送處理資訊時，會啟動 `marshaling` managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="0aace-104">The `marshaling` managed debugging assistant (MDA) is activated when the CLR sets up marshaling information for a method parameter or a field of a structure.</span></span> <span data-ttu-id="0aace-105">此 MDA 不適用於 JIT 編譯的組件。</span><span class="sxs-lookup"><span data-stu-id="0aace-105">This MDA does not work for JIT-compiled assemblies.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0aace-106">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="0aace-106">Effect on the Runtime</span></span>  

 <span data-ttu-id="0aace-107">此 MDA 對 CLR 沒有影響。</span><span class="sxs-lookup"><span data-stu-id="0aace-107">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0aace-108">輸出</span><span class="sxs-lookup"><span data-stu-id="0aace-108">Output</span></span>  

 <span data-ttu-id="0aace-109">MDA 會顯示在 managed 和 unmanaged 內容的參數或欄位類型，以及包含類型的結構或方法。</span><span class="sxs-lookup"><span data-stu-id="0aace-109">The MDA displays the type of the parameter or field in the managed and unmanaged contexts, and the structure or method containing the type.</span></span>  <span data-ttu-id="0aace-110">以下是欄位輸出的範例：</span><span class="sxs-lookup"><span data-stu-id="0aace-110">The following is an example of the output for a field:</span></span>  
  
```output
Marshaling from 'Char' to 'ANSI char'  
name="assembly!Namespace.Class::myChar  
```  
  
## <a name="configuration"></a><span data-ttu-id="0aace-111">設定</span><span class="sxs-lookup"><span data-stu-id="0aace-111">Configuration</span></span>  

 <span data-ttu-id="0aace-112">MDA 組態可讓您根據相關的欄位或方法名稱篩選報告的封送處理資訊。</span><span class="sxs-lookup"><span data-stu-id="0aace-112">The MDA configuration allows you to filter the reported marshaling information based on the involved field or method names.</span></span>  <span data-ttu-id="0aace-113">下列範例顯示如何使用 `methodFilter``fieldFilter` 和 `match` 項目以指定篩選條件。</span><span class="sxs-lookup"><span data-stu-id="0aace-113">The following example shows the use of the `methodFilter`, `fieldFilter`, and `match` elements to specify filters.</span></span>  <span data-ttu-id="0aace-114">將 `name` 屬性設定為星號 (\*) 將會符合所有專案。</span><span class="sxs-lookup"><span data-stu-id="0aace-114">Setting the `name` attribute to an asterisk (\*) will match everything.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0aace-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0aace-115">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0aace-116">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="0aace-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0aace-117">Interop 封送處理</span><span class="sxs-lookup"><span data-stu-id="0aace-117">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
