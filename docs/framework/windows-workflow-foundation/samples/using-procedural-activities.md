---
title: 使用程序性活動
ms.date: 03/30/2017
ms.assetid: 1c67f739-3878-48ad-806c-b2ce0d6733a0
ms.openlocfilehash: bd83f1a0fa9f3af7c22cee73fbc4f984a9ebf53c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43804746"
---
# <a name="using-procedural-activities"></a><span data-ttu-id="e8875-102">使用程序性活動</span><span class="sxs-lookup"><span data-stu-id="e8875-102">Using Procedural Activities</span></span>
<span data-ttu-id="e8875-103">這個範例會使用 <xref:System.Activities.Statements.Sequence>、<xref:System.Activities.Statements.Assign>、<xref:System.Activities.Statements.If>、<xref:System.Activities.Statements.While>、<xref:System.Activities.Statements.Switch%601>、<xref:System.Activities.Statements.TryCatch> 和 <xref:System.Activities.Statements.WriteLine> 活動實作猜測遊戲。</span><span class="sxs-lookup"><span data-stu-id="e8875-103">The sample uses the <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Assign>, <xref:System.Activities.Statements.If>, <xref:System.Activities.Statements.While>, <xref:System.Activities.Statements.Switch%601>, <xref:System.Activities.Statements.TryCatch>, and <xref:System.Activities.Statements.WriteLine> activities to implement a guessing game.</span></span> <span data-ttu-id="e8875-104">猜測遊戲會選取一個隨機數字，而玩家必須猜測該數字。</span><span class="sxs-lookup"><span data-stu-id="e8875-104">The guessing game selects a random number and the player has to guess that number.</span></span> <span data-ttu-id="e8875-105">當玩家送出不正確的猜測時，工作流程會提供一個提示，告訴玩家應該猜大一點或小一點的數字。</span><span class="sxs-lookup"><span data-stu-id="e8875-105">When the player submits an incorrect guess, the workflow provides a hint whether to guess higher or lower.</span></span> <span data-ttu-id="e8875-106">如果玩家在 7 次內猜到數字，則會對使用者顯示特別的恭賀畫面。</span><span class="sxs-lookup"><span data-stu-id="e8875-106">If the player guesses the number in less than 7 attempts, a special congratulations is displayed to the user.</span></span>  
  
## <a name="custom-activities-in-this-sample"></a><span data-ttu-id="e8875-107">這個範例中的自訂活動</span><span class="sxs-lookup"><span data-stu-id="e8875-107">Custom Activities in this Sample</span></span>  
  
### <a name="readline"></a><span data-ttu-id="e8875-108">ReadLine</span><span class="sxs-lookup"><span data-stu-id="e8875-108">ReadLine</span></span>  
 <span data-ttu-id="e8875-109">從主控台讀取一行文字。</span><span class="sxs-lookup"><span data-stu-id="e8875-109">Reads a line of text from the console.</span></span> <span data-ttu-id="e8875-110">這個活動衍生自 <xref:System.Activities.NativeActivity> 類別，並且會建立書籤，主控台應用程式會在讀取一行之後繼續執行該書籤。</span><span class="sxs-lookup"><span data-stu-id="e8875-110">This activity derives from the <xref:System.Activities.NativeActivity> class and creates a bookmark that is resumed by the console application when a line is read.</span></span>  
  
### <a name="promptint"></a><span data-ttu-id="e8875-111">PromptInt</span><span class="sxs-lookup"><span data-stu-id="e8875-111">PromptInt</span></span>  
 <span data-ttu-id="e8875-112">提示使用者輸入數字，然後從主控台視窗讀取該數字。</span><span class="sxs-lookup"><span data-stu-id="e8875-112">Prompts the user to type in a number and then reads it from a console window.</span></span> <span data-ttu-id="e8875-113">此活動衍生自 <xref:System.Activities.Activity%601>，並且會使用 <xref:System.Activities.Statements.WriteLine> 和 `ReadLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="e8875-113">The activity derives from <xref:System.Activities.Activity%601> and uses the <xref:System.Activities.Statements.WriteLine> and `ReadLine` activities.</span></span>  
  
##### <a name="to-use-this-sample"></a><span data-ttu-id="e8875-114">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="e8875-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="e8875-115">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [GuessingGame.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="e8875-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the GuessingGame.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e8875-116">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="e8875-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e8875-117">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="e8875-117">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8875-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e8875-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8875-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e8875-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e8875-120">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="e8875-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8875-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e8875-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Procedurals`