---
title: 取消可補償活動上的處理常式
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: ce4d67b26a2b4c6a9b507715b48e75e328c5b100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514997"
---
# <a name="cancellation-handler-on-compensable-activity"></a><span data-ttu-id="c1fcb-102">取消可補償活動上的處理常式</span><span class="sxs-lookup"><span data-stu-id="c1fcb-102">Cancellation Handler on Compensable Activity</span></span>
<span data-ttu-id="c1fcb-103">這個範例示範如何在 <xref:System.Activities.Statements.CompensableActivity> 上使用取消處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-103">This sample demonstrates the use of a cancellation handler on a <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 <span data-ttu-id="c1fcb-104">這個範例包含兩個示範 <xref:System.Activities.Statements.CompensableActivity> 取消用法的案例。第一個案例包含可補償的根活動，其中包含三個可補償的子活動。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-104">This sample contains two scenarios that demonstrate the use of <xref:System.Activities.Statements.CompensableActivity> cancellation.The first scenario contains a root compensable activity that contains three child compensable activities.</span></span> <span data-ttu-id="c1fcb-105">兩個子活動成功完成執行其活動主體。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-105">Two child activities finish running their activity bodies successfully.</span></span> <span data-ttu-id="c1fcb-106">當第三個子活動主體執行時，遇到例外狀況，該例外狀況的處理方式是取消第三個活動處理，在此之後，會觸發根活動取消。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-106">When the third child activity body runs, it encounters an exception that is handled by canceling the third activity processing, after which the cancellation of the root activity is triggered.</span></span> <span data-ttu-id="c1fcb-107">這個範例中根活動的邏輯是補償另外兩個稍早完成的子活動。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-107">The logic in the root activity in this example is to compensate the other two child activities that completed earlier.</span></span>  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 <span data-ttu-id="c1fcb-108">第二個案例示範如何平行執行 <xref:System.Activities.Statements.TryCatch> 與 <xref:System.Activities.Statements.Delay>，後者在 <xref:System.Activities.Statements.TryCatch> 分支之前完成。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-108">The second scenario demonstrates executing a <xref:System.Activities.Statements.TryCatch> in parallel with a <xref:System.Activities.Statements.Delay>, which finishes before the <xref:System.Activities.Statements.TryCatch> branch.</span></span> <span data-ttu-id="c1fcb-109">一旦第一個分支完成，完成條件會設為 `true`，導致另一個分支取消。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-109">The completion condition is set to `true` once the first branch finishes, causing the other branch to be canceled.</span></span>  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c1fcb-110">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="c1fcb-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c1fcb-111">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CompensationCancellation.sln。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open CompensationCancellation.sln.</span></span>  
  
2.  <span data-ttu-id="c1fcb-112">按 CTRL+SHIFT+B 或選取 [建置] 功能表中的 [建置方案]，以建置範例。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-112">Build the sample by pressing CTRL+SHIFT+B or select "Build Solution" from the Build menu..</span></span>  
  
3.  <span data-ttu-id="c1fcb-113">按 F5 或選取 [偵錯] 功能表中的 [開始偵錯]，執行範例。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-113">Run the sample by pressing F5 or select "Start Debugging" from the Debug menu.</span></span> <span data-ttu-id="c1fcb-114">或者，您可以按 Ctrl+F5 或選取 [偵錯] 功能表中的 [啟動但不偵錯]。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-114">Alternately you may press Ctrl+F5 or select "Start without Debugging" from the Debug menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c1fcb-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c1fcb-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c1fcb-117">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c1fcb-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c1fcb-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`