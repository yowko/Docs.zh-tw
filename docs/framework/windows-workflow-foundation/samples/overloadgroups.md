---
title: OverloadGroups
ms.date: 03/30/2017
ms.assetid: d1d547d2-f5fb-4de3-a959-ee6139a4f1ad
ms.openlocfilehash: 0773e76d36b25ad5485cc8912c7012815412de9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43469865"
---
# <a name="overloadgroups"></a><span data-ttu-id="d69d9-102">OverloadGroups</span><span class="sxs-lookup"><span data-stu-id="d69d9-102">OverloadGroups</span></span>
<span data-ttu-id="d69d9-103">這個範例是由 (`CreateLocation`) 活動所組成，這個活動有兩個有趣的特性：</span><span class="sxs-lookup"><span data-stu-id="d69d9-103">This sample consists of an activity (`CreateLocation`), which has two interesting characteristics:</span></span>  
  
1.  <span data-ttu-id="d69d9-104">它有一些必要的引數及一些選擇性的引數。</span><span class="sxs-lookup"><span data-stu-id="d69d9-104">It has some required arguments and some optional ones.</span></span>  
  
2.  <span data-ttu-id="d69d9-105">它可讓使用者選擇提供兩組不同引數的其中一組。</span><span class="sxs-lookup"><span data-stu-id="d69d9-105">It allows the user to choose to provide one of two different sets of arguments.</span></span>  
  
 <span data-ttu-id="d69d9-106">這些行為是使用下列兩個功能所完成：</span><span class="sxs-lookup"><span data-stu-id="d69d9-106">These behaviors are accomplished by using these two features:</span></span>  
  
-   <span data-ttu-id="d69d9-107">`[isRequired]` 會驗證特定活動的屬性已指派，如果未指派則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d69d9-107">`[isRequired]` validates that a property of a specific activity is assign, and if not, it throws an exception.</span></span>  
  
-   <span data-ttu-id="d69d9-108">`[OverloadGroup]` 會將一組引數放在一起，好讓活動的使用者可以選擇使用某一組或另一組。</span><span class="sxs-lookup"><span data-stu-id="d69d9-108">`[OverloadGroup]` puts together a set of arguments, so that the user of the activity can choose between using one set or another.</span></span> <span data-ttu-id="d69d9-109">使用者不能在相同執行個體中使用不同多載群組內的引數。</span><span class="sxs-lookup"><span data-stu-id="d69d9-109">The user cannot use arguments from different Overload Groups in the same instance.</span></span>  
  
 <span data-ttu-id="d69d9-110">在設定不同的工作流程之後，請呼叫 <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>，它會傳回 <xref:System.Activities.Validation.ValidationResults> 的 <xref:System.Activities.Validation.Constraint> 集合。</span><span class="sxs-lookup"><span data-stu-id="d69d9-110">After setting up different workflows, call <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> which returns a <xref:System.Activities.Validation.ValidationResults> collection of <xref:System.Activities.Validation.Constraint>.</span></span> <span data-ttu-id="d69d9-111">請將 <xref:System.Activities.Validation.Constraint> 物件列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="d69d9-111">Print the <xref:System.Activities.Validation.Constraint> objects to the console.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d69d9-112">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="d69d9-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d69d9-113">開啟**OverloadGroups.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d69d9-113">Open the **OverloadGroups.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d69d9-114">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="d69d9-114">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d69d9-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d69d9-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d69d9-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d69d9-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d69d9-117">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="d69d9-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d69d9-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d69d9-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Validation\OverloadGroups`
