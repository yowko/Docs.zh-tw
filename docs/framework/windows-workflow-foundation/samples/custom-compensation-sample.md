---
title: "自訂補償範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2bc76267cf4b3fe5f4e792ee185733e51185872f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="27252-102">自訂補償範例</span><span class="sxs-lookup"><span data-stu-id="27252-102">Custom Compensation Sample</span></span>
<span data-ttu-id="27252-103">這個範例示範如何使用 <xref:System.Activities.Statements.CompensableActivity> 及其補償處理常式，定義自訂的補償邏輯。</span><span class="sxs-lookup"><span data-stu-id="27252-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="27252-104">這個範例中的模型案例為卡車租賃業者。</span><span class="sxs-lookup"><span data-stu-id="27252-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="27252-105">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="27252-105">Sample Details</span></span>  
 <span data-ttu-id="27252-106">模擬的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="27252-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="27252-107">使用者要求給定日期的卡車租賃報價。</span><span class="sxs-lookup"><span data-stu-id="27252-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="27252-108">連絡三家卡車公司，並提供三份報價。</span><span class="sxs-lookup"><span data-stu-id="27252-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="27252-109">使用者選取一份卡車報價，開始著手用信用卡訂購。</span><span class="sxs-lookup"><span data-stu-id="27252-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="27252-110">應用程式取消其他兩份卡車報價。</span><span class="sxs-lookup"><span data-stu-id="27252-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="27252-111">如果在預定日期前 10 天 (含) 內取消，應用程式針對非尊榮客戶收取不退費的服務費。</span><span class="sxs-lookup"><span data-stu-id="27252-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="27252-112">應用程式收取卡車租賃費用。</span><span class="sxs-lookup"><span data-stu-id="27252-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="27252-113">應用程式等候，直到預定日期或客戶決定取消預定為止，依先到日期為準。</span><span class="sxs-lookup"><span data-stu-id="27252-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="27252-114">如果客戶取消預定，<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> 自訂補償邏輯會依據下列邏輯執行：</span><span class="sxs-lookup"><span data-stu-id="27252-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="27252-115">如果客戶不是尊榮客戶，而且在預定日期前 10 天內，仍會收取服務費，否則應用程式會針對服務費全額退費。</span><span class="sxs-lookup"><span data-stu-id="27252-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="27252-116">其餘可補償活動 (卡車租車 + 卡車租車費) 會依據預設補償邏輯執行，也就是反向執行的補償。</span><span class="sxs-lookup"><span data-stu-id="27252-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="27252-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="27252-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="27252-118">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CustomCompensation.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="27252-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="27252-119">此檔案位於 \WF\Basic\Compensation\CustomCompensation 目錄中。</span><span class="sxs-lookup"><span data-stu-id="27252-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="27252-120">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="27252-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="27252-121">按 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="27252-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="27252-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="27252-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="27252-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="27252-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="27252-124">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="27252-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27252-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="27252-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`