---
title: "工作流程服務中的格式化訊息"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be200882b59af3604a88c33ad1b3a99687ded860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="c444f-102">工作流程服務中的格式化訊息</span><span class="sxs-lookup"><span data-stu-id="c444f-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="c444f-103">這個範例示範不同使用者類型在訊息活動中的使用方式 (WF 服務)。</span><span class="sxs-lookup"><span data-stu-id="c444f-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="c444f-104">範例服務是簡單的經費支出核准服務，會公開三個作業。</span><span class="sxs-lookup"><span data-stu-id="c444f-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="c444f-105">`ApproveExpense` 採用資料合約型別，並示範如何使用已知的型別。</span><span class="sxs-lookup"><span data-stu-id="c444f-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="c444f-106">作業會根據支出金額傳回 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="c444f-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="c444f-107">`ApprovePO`會採用 XmlSerializer 型別並傳回`true`或`false`根據支出金額。`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="c444f-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="c444f-108">採用訊息合約型別，並傳回`true`或`false`如果廠商在核准廠商清單中，或者要求來自財務部門 （財務部門可以使用任何廠商）。</span><span class="sxs-lookup"><span data-stu-id="c444f-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="c444f-109">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="c444f-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="c444f-110">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。</span><span class="sxs-lookup"><span data-stu-id="c444f-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="c444f-111">首先，執行 [方案基底目錄]\FormatterService\bin\debug\ 中產生的服務。</span><span class="sxs-lookup"><span data-stu-id="c444f-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="c444f-112">接著，執行 [方案基底目錄]\FormatterClient\bin\debug 中產生的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="c444f-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="c444f-113">這個用戶端會在服務上呼叫三個作業並列印結果。</span><span class="sxs-lookup"><span data-stu-id="c444f-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="c444f-114">完成時，按下 ENTER 結束用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="c444f-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c444f-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c444f-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c444f-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c444f-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c444f-117">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="c444f-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c444f-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c444f-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`