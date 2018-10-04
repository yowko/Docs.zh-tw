---
title: 流速控制平行 ForEach
ms.date: 03/30/2017
ms.assetid: f2855b5f-e9a7-433d-96a4-40fc31025215
ms.openlocfilehash: 8691edb8a5a61204b187be8def553f2f06be0f0d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581858"
---
# <a name="throttled-parallel-foreach"></a><span data-ttu-id="0440f-102">流速控制平行 ForEach</span><span class="sxs-lookup"><span data-stu-id="0440f-102">Throttled Parallel ForEach</span></span>
<span data-ttu-id="0440f-103">`ThrottleParallelForEach`活動十分類似<!--zz <xref:System.Activities.Statements.ParallelForEach>-->`System.Activities.Statements.ParallelForEach`有一個例外狀況的活動它允許設定並行因數來限制同時執行的分支數目。</span><span class="sxs-lookup"><span data-stu-id="0440f-103">The `ThrottleParallelForEach` activity is similar to the <!--zz <xref:System.Activities.Statements.ParallelForEach>--> `System.Activities.Statements.ParallelForEach` activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span> <span data-ttu-id="0440f-104">`ThrottleParallelForEach` 活動衍生自 <xref:System.Activities.NativeActivity>，因為它必須排程其他活動 (子活動)，而且這只能透過 <xref:System.Activities.NativeActivityContext> 類別存取。</span><span class="sxs-lookup"><span data-stu-id="0440f-104">The `ThrottleParallelForEach` activity derives from <xref:System.Activities.NativeActivity>, because it needs to schedule other activities (the child activities) and this is only accessible through the <xref:System.Activities.NativeActivityContext> class.</span></span>

## <a name="projects"></a><span data-ttu-id="0440f-105">專案</span><span class="sxs-lookup"><span data-stu-id="0440f-105">Projects</span></span>

|<span data-ttu-id="0440f-106">**ProjectName**</span><span class="sxs-lookup"><span data-stu-id="0440f-106">**ProjectName**</span></span>|<span data-ttu-id="0440f-107">**描述**</span><span class="sxs-lookup"><span data-stu-id="0440f-107">**Description**</span></span>|<span data-ttu-id="0440f-108">**主要的檔案**</span><span class="sxs-lookup"><span data-stu-id="0440f-108">**Main Files**</span></span>|
|-|-|-|
|<span data-ttu-id="0440f-109">ThrottledParallelForEach</span><span class="sxs-lookup"><span data-stu-id="0440f-109">ThrottledParallelForEach</span></span>|<span data-ttu-id="0440f-110">包含 `ThrottledParallelForEach` 活動和其設計工具</span><span class="sxs-lookup"><span data-stu-id="0440f-110">Contains `ThrottledParallelForEach` activity and its designer.</span></span>|<span data-ttu-id="0440f-111">ThrottledParallelForEach.cs</span><span class="sxs-lookup"><span data-stu-id="0440f-111">ThrottledParallelForEach.cs</span></span><br /><br /> <span data-ttu-id="0440f-112">`ThrottledParallelForEach` 活動定義。</span><span class="sxs-lookup"><span data-stu-id="0440f-112">The `ThrottledParallelForEach` activity definition.</span></span>|
|<span data-ttu-id="0440f-113">CodeTestClient</span><span class="sxs-lookup"><span data-stu-id="0440f-113">CodeTestClient</span></span>|<span data-ttu-id="0440f-114">範例用戶端應用程式，可透過使用命令式程式碼的 `ThrottledParallelForEach` 來設定及執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="0440f-114">Sample client application that configures and runs a workflow with a `ThrottledParallelForEach` using imperative code.</span></span>|<span data-ttu-id="0440f-115">Program.cs</span><span class="sxs-lookup"><span data-stu-id="0440f-115">Program.cs</span></span><br /><br /> <span data-ttu-id="0440f-116">定義及執行範例工作流程的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0440f-116">Defines and runs an instance of the sample workflow.</span></span>|

#### <a name="to-use-this-sample"></a><span data-ttu-id="0440f-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="0440f-117">To use this sample</span></span>

1.  <span data-ttu-id="0440f-118">使用 Visual Studio 2010 開啟 ThrottledParallelForEach.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="0440f-118">Using Visual Studio 2010, open the ThrottledParallelForEach.sln file.</span></span>

2.  <span data-ttu-id="0440f-119">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="0440f-119">To build the solution, press CTRL+SHIFT+B.</span></span>

3.  <span data-ttu-id="0440f-120">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="0440f-120">To run the solution, press F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="0440f-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0440f-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0440f-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0440f-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0440f-123">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0440f-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0440f-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0440f-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\ThrottledParallelForEach`