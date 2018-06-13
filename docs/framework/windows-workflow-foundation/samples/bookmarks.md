---
title: Bookmarks2
ms.date: 03/30/2017
ms.assetid: 035fadb2-49fa-4ac7-b398-daf138f66e87
ms.openlocfilehash: 61abc1d1a5084018511975e27fa96311c168eb69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514152"
---
# <a name="bookmarks"></a><span data-ttu-id="5d647-102">書籤</span><span class="sxs-lookup"><span data-stu-id="5d647-102">Bookmarks</span></span>
<span data-ttu-id="5d647-103">這個範例示範如何撰寫自訂活動，建立可接收外部輸入的書籤。</span><span class="sxs-lookup"><span data-stu-id="5d647-103">This sample demonstrates how to write a custom activity that creates a bookmark to receive external input.</span></span> <span data-ttu-id="5d647-104">範例中還包括在工作流程中使用自訂活動的基本主控台應用程式，並且示範如何探索和繼續與執行中工作流程執行個體相關聯的書籤。</span><span class="sxs-lookup"><span data-stu-id="5d647-104">The sample also includes a basic console application that uses the custom activity in a workflow and shows how to discover and resume bookmarks associated with a running workflow instance.</span></span> <span data-ttu-id="5d647-105">如需書籤的詳細資訊，請參閱[書籤](../../../../docs/framework/windows-workflow-foundation/bookmarks.md)。</span><span class="sxs-lookup"><span data-stu-id="5d647-105">For more information about bookmarks, see [Bookmarks](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5d647-106">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5d647-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5d647-107">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [Bookmarks.sln] 範例方案。</span><span class="sxs-lookup"><span data-stu-id="5d647-107">Open the Bookmarks.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d647-108">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="5d647-108">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5d647-109">若要執行範例，請按 CTRLl + F5。</span><span class="sxs-lookup"><span data-stu-id="5d647-109">To run the sample, press CTRLl + F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5d647-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5d647-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d647-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5d647-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5d647-112">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="5d647-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d647-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5d647-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CodeBodied\Bookmarks`