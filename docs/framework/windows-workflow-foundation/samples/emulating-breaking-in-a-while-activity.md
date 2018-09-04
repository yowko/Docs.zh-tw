---
title: While 活動中的模擬中斷
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 4938e07364609520f6528688877bce112be26d3f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560421"
---
# <a name="emulating-breaking-in-a-while-activity"></a><span data-ttu-id="a62ec-102">While 活動中的模擬中斷</span><span class="sxs-lookup"><span data-stu-id="a62ec-102">Emulating breaking in a While activity</span></span>
<span data-ttu-id="a62ec-103">這個範例會示範如何中斷下列活動的迴圈機制：<xref:System.Activities.Statements.DoWhile>、<xref:System.Activities.Statements.ForEach%601>、<xref:System.Activities.Statements.While> 和 <xref:System.Activities.Statements.ParallelForEach%601>。</span><span class="sxs-lookup"><span data-stu-id="a62ec-103">This sample demonstrates how to break the looping mechanism of the following activities: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span>  
  
 <span data-ttu-id="a62ec-104">這是很有用，因為 Windows Workflow Foundation (WF) 不包含任何可中斷這些迴圈執行的活動。</span><span class="sxs-lookup"><span data-stu-id="a62ec-104">This is useful because Windows Workflow Foundation (WF) does not include any activity to break the execution of these loops.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="a62ec-105">情節</span><span class="sxs-lookup"><span data-stu-id="a62ec-105">Scenario</span></span>  
 <span data-ttu-id="a62ec-106">此範例會從廠商清單中尋找第一家可靠的廠商 (`Vendor` 類別的執行個體)。</span><span class="sxs-lookup"><span data-stu-id="a62ec-106">The sample finds the first reliable vendor from a list of vendors (instances of the `Vendor` class).</span></span> <span data-ttu-id="a62ec-107">每一家廠商都有 `ID`、`Name` 以及數值信賴值 (可決定廠商的信賴度)。</span><span class="sxs-lookup"><span data-stu-id="a62ec-107">Each vendor has an `ID`, a `Name` and a numeric reliability value that determines how dependable the vendor is.</span></span> <span data-ttu-id="a62ec-108">此範例會建立一個名為 `FindReliableVendor` 的自訂活動，此活動會接收兩個輸入參數 (廠商清單及最低信賴值)，並傳回清單中符合提供之準則的第一家廠商。</span><span class="sxs-lookup"><span data-stu-id="a62ec-108">The sample creates a custom activity called `FindReliableVendor` that receives two input parameters (a list of vendors and a minimum reliability value) and returns the first vendor of the list that matches the supplied criteria.</span></span>  
  
## <a name="breaking-a-loop"></a><span data-ttu-id="a62ec-109">中斷迴圈</span><span class="sxs-lookup"><span data-stu-id="a62ec-109">Breaking a Loop</span></span>  
 <span data-ttu-id="a62ec-110">Windows Workflow Foundation (WF) 不包含用來中斷迴圈的活動。</span><span class="sxs-lookup"><span data-stu-id="a62ec-110">Windows Workflow Foundation (WF) does not include an activity to break a loop.</span></span> <span data-ttu-id="a62ec-111">此程式碼範例會使用 <xref:System.Activities.Statements.If> 活動和幾個變數來完成中斷迴圈的工作。</span><span class="sxs-lookup"><span data-stu-id="a62ec-111">The code sample accomplishes breaking a loop by using an <xref:System.Activities.Statements.If> activity and several variables.</span></span> <span data-ttu-id="a62ec-112">在範例中，一旦 <xref:System.Activities.Statements.While> 變數指派了 `reliableVendor` 以外的值，`null` 活動就會中斷。</span><span class="sxs-lookup"><span data-stu-id="a62ec-112">In the sample, the <xref:System.Activities.Statements.While> activity is broken once the `reliableVendor` variable is assigned a value other than `null`.</span></span>  
  
 <span data-ttu-id="a62ec-113">下列程式碼範例示範此範例如何中斷 while 迴圈。</span><span class="sxs-lookup"><span data-stu-id="a62ec-113">The following code example demonstrates how the sample breaks a while loop.</span></span>  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a62ec-114">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="a62ec-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="a62ec-115">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 EmulatingBreakInWhile.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="a62ec-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the EmulatingBreakInWhile.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a62ec-116">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="a62ec-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a62ec-117">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="a62ec-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a62ec-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a62ec-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a62ec-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a62ec-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a62ec-120">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a62ec-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a62ec-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a62ec-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`