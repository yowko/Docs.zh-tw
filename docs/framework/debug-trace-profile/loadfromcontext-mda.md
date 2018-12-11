---
title: loadFromContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ee575cacbc51fc910770cca145a4280f97b66db
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144428"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="17375-102">loadFromContext MDA</span><span class="sxs-lookup"><span data-stu-id="17375-102">loadFromContext MDA</span></span>
<span data-ttu-id="17375-103">如果組件載入到 `LoadFrom` 內容中，就會啟動 `loadFromContext` Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="17375-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="17375-104">這種情況可能是因為呼叫 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 或其他類似方法而發生。</span><span class="sxs-lookup"><span data-stu-id="17375-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="17375-105">徵兆 </span><span class="sxs-lookup"><span data-stu-id="17375-105">Symptoms</span></span>  
 <span data-ttu-id="17375-106">使用某些載入器方法可能會將組件載入到 `LoadFrom` 內容中。</span><span class="sxs-lookup"><span data-stu-id="17375-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="17375-107">使用這個內容可能會導致序列化、轉型和相依性解析的未預期行為。</span><span class="sxs-lookup"><span data-stu-id="17375-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="17375-108">一般情況下，建議將組件載入至 `Load` 內容，以避免這些問題發生。</span><span class="sxs-lookup"><span data-stu-id="17375-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="17375-109">無此 MDA，難以判斷哪些內容已載入組件。</span><span class="sxs-lookup"><span data-stu-id="17375-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="17375-110">原因</span><span class="sxs-lookup"><span data-stu-id="17375-110">Cause</span></span>  
 <span data-ttu-id="17375-111">一般而言，如果組件是從 `Load` 內容的外部路徑載入，例如全域組件快取或 <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> 屬性，就會載入至 `LoadFrom` 內容。</span><span class="sxs-lookup"><span data-stu-id="17375-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="17375-112">解決方式</span><span class="sxs-lookup"><span data-stu-id="17375-112">Resolution</span></span>  
 <span data-ttu-id="17375-113">設定應用程式，因此不再需要 <xref:System.Reflection.Assembly.LoadFrom%2A> 呼叫。</span><span class="sxs-lookup"><span data-stu-id="17375-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="17375-114">您可以使用下列技巧執行該作業：</span><span class="sxs-lookup"><span data-stu-id="17375-114">You can use the following techniques for doing so:</span></span>  
  
-   <span data-ttu-id="17375-115">在全域組件快取中安裝組件。</span><span class="sxs-lookup"><span data-stu-id="17375-115">Install assemblies in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="17375-116">將組件放置在 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A>目錄中。</span><span class="sxs-lookup"><span data-stu-id="17375-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="17375-117">如果是預設網域，<xref:System.AppDomainSetup.ApplicationBase%2A> 目錄會包含啟動處理序的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="17375-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="17375-118">如果移動組件不方便，可能也需要建立新的 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="17375-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
-   <span data-ttu-id="17375-119">如果相依組件位在可執行檔的相對子目錄中，請將探查路徑新增至應用程式組態檔 (.config) 或次要應用程式網域。</span><span class="sxs-lookup"><span data-stu-id="17375-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="17375-120">每個案例都可以變更程式碼，以使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="17375-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="17375-121">對執行階段的影響</span><span class="sxs-lookup"><span data-stu-id="17375-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="17375-122">MDA 對 CLR 不會產生任何影響。</span><span class="sxs-lookup"><span data-stu-id="17375-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="17375-123">它報告的內容，過去用為載入要求的結果。</span><span class="sxs-lookup"><span data-stu-id="17375-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="17375-124">輸出</span><span class="sxs-lookup"><span data-stu-id="17375-124">Output</span></span>  
 <span data-ttu-id="17375-125">MDA 會報告組件已載入至 `LoadFrom` 內容。</span><span class="sxs-lookup"><span data-stu-id="17375-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="17375-126">它會指定組件和路徑的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="17375-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="17375-127">也會建議降低風險，避免使用 `LoadFrom` 內容。</span><span class="sxs-lookup"><span data-stu-id="17375-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="17375-128">組態</span><span class="sxs-lookup"><span data-stu-id="17375-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="17375-129">範例</span><span class="sxs-lookup"><span data-stu-id="17375-129">Example</span></span>  
 <span data-ttu-id="17375-130">下列程式碼範例示範可啟用此 MDA 的情況：</span><span class="sxs-lookup"><span data-stu-id="17375-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17375-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17375-131">See Also</span></span>  
 [<span data-ttu-id="17375-132">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="17375-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
