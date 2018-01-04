---
title: "搭配規則的 IfElse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4ad9bb2-9037-413a-8b14-59ed7b927a9e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bec818ca5492e9a49a602a4f7baef4b45cb073c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ifelse-with-rules"></a><span data-ttu-id="46014-102">搭配規則的 IfElse</span><span class="sxs-lookup"><span data-stu-id="46014-102">IfElse With Rules</span></span>
<span data-ttu-id="46014-103">這個範例會示範搭配 <xref:System.Workflow.Activities.IfElseActivity> 活動來使用規則條件。</span><span class="sxs-lookup"><span data-stu-id="46014-103">This sample shows the use of a rule condition with an <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span>  
  
 <span data-ttu-id="46014-104">此範例會從主機傳入 `OrderValue` 參數。</span><span class="sxs-lookup"><span data-stu-id="46014-104">The sample passes in an `OrderValue` parameter from the host.</span></span> <span data-ttu-id="46014-105">該參數的值會在 <xref:System.Workflow.Activities.IfElseActivity> 活動的第一個分支上的規則條件中使用。</span><span class="sxs-lookup"><span data-stu-id="46014-105">The value of the parameter is used in a rule condition on the first branch of the <xref:System.Workflow.Activities.IfElseActivity> activity.</span></span> <span data-ttu-id="46014-106">如果值小於 10000，第一個分支便會執行，而<xref:System.Workflow.Activities.CodeActivity>中的第一個分支的活動會列印**取得管理員核准**至主控台。</span><span class="sxs-lookup"><span data-stu-id="46014-106">If the value is less than 10,000, the first branch executes, and the <xref:System.Workflow.Activities.CodeActivity> activity in the first branch prints **Get Manager Approval** to the console.</span></span> <span data-ttu-id="46014-107">如果值大於 10000，<xref:System.Workflow.Activities.CodeActivity>執行第二個分支的活動，並列印**取得副總裁核准**。</span><span class="sxs-lookup"><span data-stu-id="46014-107">If the value is greater than 10,000, the <xref:System.Workflow.Activities.CodeActivity> activity in the second branch executes and prints **Get VP Approval**.</span></span>  
  
### <a name="to-build-the-sample"></a><span data-ttu-id="46014-108">若要建置範例</span><span class="sxs-lookup"><span data-stu-id="46014-108">To build the sample</span></span>  
  
1.  <span data-ttu-id="46014-109">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。</span><span class="sxs-lookup"><span data-stu-id="46014-109">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="46014-110">按 CTRL+SHIFT+B 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="46014-110">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="46014-111">按 CTRL+F5 執行方案，但不進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="46014-111">Run the solution without debugging by pressing CTRL+F5.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="46014-112">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="46014-112">To run the sample</span></span>  
  
-   <span data-ttu-id="46014-113">在 [SDK 命令提示字元] 視窗中，於 IfElseWithRules\bin\debug 資料夾 (若是 Visual Basic 版本的範例，則是 IfElseWithRules\bin 資料夾) 中執行此 .exe 檔案，該資料夾位於此範例的主要資料夾下方。</span><span class="sxs-lookup"><span data-stu-id="46014-113">In the SDK Command Prompt window, run the .exe file in the IfElseWithRules\bin\debug folder (or the IfElseWithRules\bin folder for the Visual Basic version of the sample), which is located below the main folder for the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46014-114">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="46014-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="46014-115">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="46014-115">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="46014-116">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="46014-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="46014-117">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="46014-117">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\IfElseWithRules`  
  
## <a name="see-also"></a><span data-ttu-id="46014-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="46014-118">See Also</span></span>  
 <xref:System.Workflow.Activities.Rules>  
 <xref:System.Workflow.Activities.IfElseActivity>  
 <xref:System.Workflow.Activities.CodeActivity>  
 <xref:System.Workflow.Activities.Rules.RuleDefinitions>
