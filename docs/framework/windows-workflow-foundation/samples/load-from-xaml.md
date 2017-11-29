---
title: "從 XAML 載入"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ca5f830e666ad65ca2162ffd1abb03ce9beca387
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="load-from-xaml"></a><span data-ttu-id="97435-102">從 XAML 載入</span><span class="sxs-lookup"><span data-stu-id="97435-102">Load From XAML</span></span>
<span data-ttu-id="97435-103">這個範例示範如何動態載入 XAML 工作流程，而不必執行 XamlBuildTask 工具。</span><span class="sxs-lookup"><span data-stu-id="97435-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="97435-104">這個範例會改為呼叫 <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="97435-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="97435-105">這個範例是 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] 用戶端應用程式，會使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices> 類別載入 XAML 工作流程並且執行。</span><span class="sxs-lookup"><span data-stu-id="97435-105">The sample is a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="97435-106">使用 <xref:System.Activities.XamlIntegration.ActivityXamlServices> 類別載入工作流程之後，就會傳回可以執行的 <xref:System.Activities.DynamicActivity%601>。</span><span class="sxs-lookup"><span data-stu-id="97435-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="97435-107">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="97435-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="97435-108">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 [LoadFromXAML.sln] 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="97435-108">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LoadFromXAML.sln solution file.</span></span>  
  
2.  <span data-ttu-id="97435-109">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="97435-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="97435-110">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="97435-110">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="97435-111">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="97435-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="97435-112">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="97435-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="97435-113">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="97435-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="97435-114">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="97435-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`  
  
## <a name="see-also"></a><span data-ttu-id="97435-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97435-115">See Also</span></span>
