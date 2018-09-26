---
title: 與外部資料交換服務互通使用
ms.date: 03/30/2017
ms.assetid: 96f6fe26-5305-494f-9119-7748e0c4b3fa
ms.openlocfilehash: 534321e5b5568e0dd0988333dc98ccc18ff33df8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195962"
---
# <a name="using-interop-with-external-data-exchange"></a><span data-ttu-id="11d7d-102">與外部資料交換服務互通使用</span><span class="sxs-lookup"><span data-stu-id="11d7d-102">Using Interop with External Data Exchange</span></span>
<span data-ttu-id="11d7d-103"><xref:System.Activities.Statements.Interop>活動可用來從 Windows Workflow Foundation (WF) 中執行的活動[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]並[!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)](WF3)，和工作流程中的 Windows Workflow Foundation 內[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)](WF4)。</span><span class="sxs-lookup"><span data-stu-id="11d7d-103">The <xref:System.Activities.Statements.Interop> activity can be used to execute activities from Windows Workflow Foundation (WF) in [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] and [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (WF3), and workflows within Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF4).</span></span> <span data-ttu-id="11d7d-104">此範例示範如何使用 WF4 工作流程服務中的 <xref:System.Workflow.Activities.ExternalDataExchangeService> 活動，以設定及執行 WF3 工作流程來使用 <xref:System.Activities.Statements.Interop> (以及用來呼叫方法和處理事件的對應自訂活動)。</span><span class="sxs-lookup"><span data-stu-id="11d7d-104">This sample shows how to configure and run a WF3 workflow that uses <xref:System.Workflow.Activities.ExternalDataExchangeService> (and corresponding custom activities for calling methods and handling events) by using the <xref:System.Activities.Statements.Interop> activity in a WF4 workflow service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11d7d-105">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="11d7d-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="11d7d-106">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="11d7d-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11d7d-107">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="11d7d-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11d7d-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="11d7d-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\ExternalDataExchange`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="11d7d-109">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="11d7d-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="11d7d-110">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 ExternalDataExchange.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="11d7d-110">Open the ExternalDataExchange.sln file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="11d7d-111">若要建置範例，請按下 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="11d7d-111">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="11d7d-112">若要執行範例，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="11d7d-112">To run the sample, press F5.</span></span>
