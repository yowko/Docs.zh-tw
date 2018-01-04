---
title: "UriTemplate 表範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8d8b05bcb897cfb7371b1d5353b6fd0e7949b08
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="d41e1-102">UriTemplate 表範例</span><span class="sxs-lookup"><span data-stu-id="d41e1-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="d41e1-103"><xref:System.UriTemplateTable> 類別會提供可用來處理 `UriTemplate` 執行個體集合的字典式關聯表結構。</span><span class="sxs-lookup"><span data-stu-id="d41e1-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="d41e1-104">這樣便可有效地針對表中的所有樣板比對特定的統一資源識別元 (URI)，並且擷取與符合樣板相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="d41e1-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="d41e1-105">這個範例會示範與 `UriTemplateTable` 類別有關的下列主要概念：</span><span class="sxs-lookup"><span data-stu-id="d41e1-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="d41e1-106">具現化 `UriTemplateTable` 時的語法。</span><span class="sxs-lookup"><span data-stu-id="d41e1-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="d41e1-107">將索引鍵/值組集合填入 `UriTemplateTable`。</span><span class="sxs-lookup"><span data-stu-id="d41e1-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="d41e1-108">使用 <xref:System.UriTemplateTable.MatchSingle%2A>，比對候選 URI 和此表。</span><span class="sxs-lookup"><span data-stu-id="d41e1-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d41e1-109">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="d41e1-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d41e1-110">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="d41e1-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="d41e1-111">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d41e1-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d41e1-112">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d41e1-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d41e1-113">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d41e1-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d41e1-114">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="d41e1-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d41e1-115">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d41e1-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="d41e1-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="d41e1-116">See Also</span></span>  
 [<span data-ttu-id="d41e1-117">UriTemplate 資料表發送器</span><span class="sxs-lookup"><span data-stu-id="d41e1-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="d41e1-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d41e1-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
