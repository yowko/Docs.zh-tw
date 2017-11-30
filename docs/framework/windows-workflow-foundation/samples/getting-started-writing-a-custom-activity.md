---
title: "撰寫自訂活動的使用者入門"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3902f5fa-8a43-4048-8a6a-6b15472f90f0
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 495cad6d672fd550024cc872bd3cff586326ccbc
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="getting-started-writing-a-custom-activity"></a><span data-ttu-id="792d8-102">撰寫自訂活動的使用者入門</span><span class="sxs-lookup"><span data-stu-id="792d8-102">Getting Started Writing a Custom Activity</span></span>
<span data-ttu-id="792d8-103">這個範例示範如何以 XAML 定義簡單的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="792d8-103">This sample demonstrates how to define a simple custom activity in XAML.</span></span> <span data-ttu-id="792d8-104">此活動名稱為 `Rhyme`，其邏輯為三個 <xref:System.Activities.Statements.WriteLine> 活動的序列。</span><span class="sxs-lookup"><span data-stu-id="792d8-104">The activity is given the name `Rhyme`, and its logic is a sequence of three <xref:System.Activities.Statements.WriteLine> activities.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="792d8-105">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="792d8-105">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="792d8-106">開啟**Simple.sln**範例方案中的[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="792d8-106">Open the **Simple.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="792d8-107">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="792d8-107">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="792d8-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="792d8-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="792d8-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="792d8-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="792d8-110">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="792d8-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="792d8-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="792d8-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\GettingStarted`