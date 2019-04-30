---
title: UriTemplate 範例
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 5f8a969a9ddea633d12ebe2d922c152dbb0d7241
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007613"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="386d3-102">UriTemplate 範例</span><span class="sxs-lookup"><span data-stu-id="386d3-102">UriTemplate Sample</span></span>
<span data-ttu-id="386d3-103"><xref:System.UriTemplate> 類別提供可使用一組共用通用結構之 URI 的方法。</span><span class="sxs-lookup"><span data-stu-id="386d3-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="386d3-104">本範例會示範下列與 `UriTemplate` 有關的主要概念：</span><span class="sxs-lookup"><span data-stu-id="386d3-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="386d3-105">建立範本的語法。</span><span class="sxs-lookup"><span data-stu-id="386d3-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="386d3-106">從使用 `UriTemplate` 和 <xref:System.UriTemplate.BindByName%2A> 的 <xref:System.UriTemplate.BindByPosition%2A> 產生 URI。</span><span class="sxs-lookup"><span data-stu-id="386d3-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="386d3-107"><xref:System.UriTemplateTable.Match%2A> 是 `BindByName` 和 `BindByPosition` 的反向作業。</span><span class="sxs-lookup"><span data-stu-id="386d3-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="386d3-108">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="386d3-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="386d3-109">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="386d3-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="386d3-110">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="386d3-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="386d3-111">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="386d3-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="386d3-112">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="386d3-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="386d3-113">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="386d3-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="386d3-114">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="386d3-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="386d3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="386d3-115">See also</span></span>

- [<span data-ttu-id="386d3-116">UriTemplate 資料表</span><span class="sxs-lookup"><span data-stu-id="386d3-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="386d3-117">UriTemplate 資料表發送器</span><span class="sxs-lookup"><span data-stu-id="386d3-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
