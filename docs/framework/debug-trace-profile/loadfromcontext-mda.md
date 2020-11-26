---
title: loadFromContext MDA
description: 瞭解 .NET 中的 loadFromCoNtext managed 偵錯工具 (MDA) ，如果將元件載入至 LoadFrom 內容，則會啟用此功能。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 631939b38ace4d26d0deb5b104cc5de0df3d9f3a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247352"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="fe819-103">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="fe819-103">loadFromContext MDA</span></span>

<span data-ttu-id="fe819-104">如果組件載入到 `LoadFrom` 內容中，就會啟動 `loadFromContext` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="fe819-104">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="fe819-105">這種情況可能是因為呼叫 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 或其他類似方法而發生。</span><span class="sxs-lookup"><span data-stu-id="fe819-105">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fe819-106">徵狀</span><span class="sxs-lookup"><span data-stu-id="fe819-106">Symptoms</span></span>  

 <span data-ttu-id="fe819-107">使用某些載入器方法可能會將組件載入到 `LoadFrom` 內容中。</span><span class="sxs-lookup"><span data-stu-id="fe819-107">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="fe819-108">使用這個內容可能會導致序列化、轉型和相依性解析的未預期行為。</span><span class="sxs-lookup"><span data-stu-id="fe819-108">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="fe819-109">一般情況下，建議將組件載入至 `Load` 內容，以避免這些問題發生。</span><span class="sxs-lookup"><span data-stu-id="fe819-109">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="fe819-110">無此 MDA，難以判斷哪些內容已載入組件。</span><span class="sxs-lookup"><span data-stu-id="fe819-110">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fe819-111">原因</span><span class="sxs-lookup"><span data-stu-id="fe819-111">Cause</span></span>  

 <span data-ttu-id="fe819-112">一般而言，如果組件是從 `Load` 內容的外部路徑載入，例如全域組件快取或 <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> 屬性，就會載入至 `LoadFrom` 內容。</span><span class="sxs-lookup"><span data-stu-id="fe819-112">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fe819-113">解決方法</span><span class="sxs-lookup"><span data-stu-id="fe819-113">Resolution</span></span>  

 <span data-ttu-id="fe819-114">設定應用程式，因此不再需要 <xref:System.Reflection.Assembly.LoadFrom%2A> 呼叫。</span><span class="sxs-lookup"><span data-stu-id="fe819-114">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="fe819-115">您可以使用下列技巧執行該作業：</span><span class="sxs-lookup"><span data-stu-id="fe819-115">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="fe819-116">在全域組件快取中安裝組件。</span><span class="sxs-lookup"><span data-stu-id="fe819-116">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="fe819-117">將組件放置在 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A>目錄中。</span><span class="sxs-lookup"><span data-stu-id="fe819-117">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="fe819-118">如果是預設網域，<xref:System.AppDomainSetup.ApplicationBase%2A> 目錄會包含啟動處理序的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="fe819-118">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="fe819-119">如果移動組件不方便，可能也需要建立新的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="fe819-119">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="fe819-120">如果相依組件位在可執行檔的相對子目錄中，請將探查路徑新增至應用程式組態檔 (.config) 或次要應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="fe819-120">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="fe819-121">每個案例都可以變更程式碼，以使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="fe819-121">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fe819-122">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="fe819-122">Effect on the Runtime</span></span>  

 <span data-ttu-id="fe819-123">MDA 對 CLR 不會產生任何影響。</span><span class="sxs-lookup"><span data-stu-id="fe819-123">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="fe819-124">它報告的內容，過去用為載入要求的結果。</span><span class="sxs-lookup"><span data-stu-id="fe819-124">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fe819-125">輸出</span><span class="sxs-lookup"><span data-stu-id="fe819-125">Output</span></span>  

 <span data-ttu-id="fe819-126">MDA 會報告組件已載入至 `LoadFrom` 內容。</span><span class="sxs-lookup"><span data-stu-id="fe819-126">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="fe819-127">它會指定組件和路徑的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="fe819-127">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="fe819-128">也會建議降低風險，避免使用 `LoadFrom` 內容。</span><span class="sxs-lookup"><span data-stu-id="fe819-128">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="fe819-129">設定</span><span class="sxs-lookup"><span data-stu-id="fe819-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="fe819-130">範例</span><span class="sxs-lookup"><span data-stu-id="fe819-130">Example</span></span>  

 <span data-ttu-id="fe819-131">下列程式碼範例示範可以啟動此 MDA 的情況：</span><span class="sxs-lookup"><span data-stu-id="fe819-131">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is
            // located outside of the Load context probing path.
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe819-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe819-132">See also</span></span>

- [<span data-ttu-id="fe819-133">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="fe819-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
