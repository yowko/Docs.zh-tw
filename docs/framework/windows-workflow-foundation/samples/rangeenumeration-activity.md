---
title: "RangeEnumeration 活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 35bff923b0e8d6fe7c01cb7970c7b6ee46488a43
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="7b069-102">RangeEnumeration 活動</span><span class="sxs-lookup"><span data-stu-id="7b069-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="7b069-103">這個範例會示範如何建立自訂活動，此活動會逐一查看數字集合。下表詳述此範例中所包含的主要檔案。</span><span class="sxs-lookup"><span data-stu-id="7b069-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="7b069-104">檔案名稱</span><span class="sxs-lookup"><span data-stu-id="7b069-104">File name</span></span>|<span data-ttu-id="7b069-105">描述</span><span class="sxs-lookup"><span data-stu-id="7b069-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b069-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="7b069-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="7b069-107">定義名為 `RangeEnumeration` 的自訂活動，此活動會覆寫 <xref:System.Activities.NativeActivity> 類別，並針對一連串的數字執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="7b069-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="7b069-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="7b069-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="7b069-109">使用 `RangeEnumeration` 活動的用戶端應用程式，可逐一查看數字集合。</span><span class="sxs-lookup"><span data-stu-id="7b069-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="7b069-110">下表詳述 `RangeEnumeration` 活動的屬性。</span><span class="sxs-lookup"><span data-stu-id="7b069-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="7b069-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7b069-111">Property</span></span>|<span data-ttu-id="7b069-112">描述</span><span class="sxs-lookup"><span data-stu-id="7b069-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7b069-113">啟動</span><span class="sxs-lookup"><span data-stu-id="7b069-113">Start</span></span>|<span data-ttu-id="7b069-114">開始迴圈的整數。</span><span class="sxs-lookup"><span data-stu-id="7b069-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="7b069-115">停止</span><span class="sxs-lookup"><span data-stu-id="7b069-115">Stop</span></span>|<span data-ttu-id="7b069-116">停止迴圈的整數。</span><span class="sxs-lookup"><span data-stu-id="7b069-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="7b069-117">步驟</span><span class="sxs-lookup"><span data-stu-id="7b069-117">Step</span></span>|<span data-ttu-id="7b069-118">指定每次要反覆查看的數量。</span><span class="sxs-lookup"><span data-stu-id="7b069-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="7b069-119">本文</span><span class="sxs-lookup"><span data-stu-id="7b069-119">Body</span></span>|<span data-ttu-id="7b069-120">指定每一次反覆查看時所要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b069-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="7b069-121">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="7b069-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="7b069-122">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 RangeEnumeration.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="7b069-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7b069-123">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="7b069-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7b069-124">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="7b069-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b069-125">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7b069-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7b069-126">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7b069-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b069-127">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7b069-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b069-128">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7b069-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`