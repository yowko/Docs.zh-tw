---
title: UriTemplate 表發送器範例
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 4a4f725e88e014da241e1042c27bfee270e13268
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45648508"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="ef704-102">UriTemplate 表發送器範例</span><span class="sxs-lookup"><span data-stu-id="ef704-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="ef704-103"><xref:System.UriTemplateTable> 類別會提供可用來處理 <xref:System.UriTemplate> 執行個體集合的字典式關聯表結構。</span><span class="sxs-lookup"><span data-stu-id="ef704-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="ef704-104">這個範例示範使用 `UriTemplateTable` 建置的基本分派引擎，這是 `UriTemplateTable` 類別的常用案例。</span><span class="sxs-lookup"><span data-stu-id="ef704-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="ef704-105">這個範例會示範 `UriTemplateTable` 類別的下列主要概念：</span><span class="sxs-lookup"><span data-stu-id="ef704-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="ef704-106">在 `UriTemplates` 中將委派與 `UriTemplateTable` 加以關聯。</span><span class="sxs-lookup"><span data-stu-id="ef704-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="ef704-107">使用 <xref:System.UriTemplateTable.MatchSingle%2A> 取得特定 URI 的正確處理常式委派。</span><span class="sxs-lookup"><span data-stu-id="ef704-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="ef704-108">叫用處理常式委派以處理要求。</span><span class="sxs-lookup"><span data-stu-id="ef704-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef704-109">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ef704-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ef704-110">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="ef704-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="ef704-111">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="ef704-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef704-112">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ef704-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ef704-113">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ef704-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ef704-114">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="ef704-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef704-115">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ef704-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="ef704-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef704-116">See Also</span></span>  
 [<span data-ttu-id="ef704-117">UriTemplate 資料表</span><span class="sxs-lookup"><span data-stu-id="ef704-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="ef704-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ef704-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
