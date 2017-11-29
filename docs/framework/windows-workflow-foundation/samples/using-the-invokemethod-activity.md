---
title: "使用 InvokeMethod 活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5dd488a01e00af0661ee7ee110c79d2c56a0b777
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-invokemethod-activity"></a><span data-ttu-id="32752-102">使用 InvokeMethod 活動</span><span class="sxs-lookup"><span data-stu-id="32752-102">Using the InvokeMethod Activity</span></span>
<span data-ttu-id="32752-103">這個範例會示範如何使用<!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)活動叫用公用類別中的公用方法。</span><span class="sxs-lookup"><span data-stu-id="32752-103">This sample demonstrates how to use the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity to invoke public methods in public classes.</span></span> <span data-ttu-id="32752-104"><!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)活動允許工作流程針對物件呼叫方法、 傳入參數、 取得傳回值、 指定泛型方法的類型和指定方法是否為同步或非同步的。</span><span class="sxs-lookup"><span data-stu-id="32752-104">The <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity allows a workflow to call methods against objects, pass in parameters, get the return value, specify types for generic methods, and specify whether the method is synchronous or asynchronous.</span></span> 
  
 <span data-ttu-id="32752-105">非泛型版本<xref:System.Activities.Statements.InvokeMethod>活動傳回的值設定為其中<xref:System.Activities.Statements.InvokeMethod.Result%2A>屬性和泛型版本<!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx)活動傳回的傳回值的位置透過<!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx)型別的屬性`TResult`。</span><span class="sxs-lookup"><span data-stu-id="32752-105">There is a non-generic version of the <xref:System.Activities.Statements.InvokeMethod> activity where the return value is set to the <xref:System.Activities.Statements.InvokeMethod.Result%2A> property and a generic version of the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity where the return value is returned through the <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> -->[<code>System.Activities.Statements.InvokeMethod\`1.Result</code>](https://msdn.microsoft.com/library/dd987724.aspx) property of type `TResult`.</span></span>  
  
 <span data-ttu-id="32752-106">這個範例示範如何呼叫各種方法類型。</span><span class="sxs-lookup"><span data-stu-id="32752-106">This sample demonstrates how to call various method types.</span></span> <span data-ttu-id="32752-107">下列清單詳述這個範例中示範的方法類型。</span><span class="sxs-lookup"><span data-stu-id="32752-107">The following list details the method types demonstrated in this sample:</span></span>  
  
-   <span data-ttu-id="32752-108">叫用不含參數的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32752-108">Invoke an instance method without parameters.</span></span>  
  
-   <span data-ttu-id="32752-109">叫用具有兩個參數 (System.String 和 System.Int32) 的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32752-109">Invoke an instance method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="32752-110">叫用具有兩個參數 (System.String 和 System.Int32) 以及 System.String[] 類型之參數陣列的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32752-110">Invoke an instance method with two parameters (System.String and System.Int32) and a parameter array of type System.String[].</span></span>  
  
-   <span data-ttu-id="32752-111">叫用具有兩個參數 (兩個 System.Int32 數字) 以及 System.Int32 類型之結果的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32752-111">Invoke an instance method with two parameters (two System.Int32 numbers) and a result of type System.Int32.</span></span>  
  
     <span data-ttu-id="32752-112">傳回值是繫結至變數，並且使用 <xref:System.Activities.Statements.WriteLine> 活動列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="32752-112">The return value is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="32752-113">叫用具有兩個參數 (System.String 和 System.Int32) 的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="32752-113">Invoke a static method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="32752-114">叫用具有一個泛型參數 (System.String) 的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32752-114">Invoke an instance method with one generic parameter (System.String).</span></span>  
  
-   <span data-ttu-id="32752-115">叫用具有兩個泛型參數 (System.String 和 System.Int32) 的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="32752-115">Invoke a static method with two generic parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="32752-116">叫用執行個體方法，該方法的一個參數是以傳址方式傳遞 (System.String)。</span><span class="sxs-lookup"><span data-stu-id="32752-116">Invoke an instance method that has one parameter passed by reference (System.String).</span></span>  
  
     <span data-ttu-id="32752-117">參考的參數是繫結至變數，並且使用 <xref:System.Activities.Statements.WriteLine> 活動列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="32752-117">The referenced parameter is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="32752-118">叫用非同步執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="32752-118">Invoke an asynchronous instance method.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="32752-119">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="32752-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="32752-120">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 InvokeMethodUsage.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="32752-120">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file.</span></span>  
  
2.  <span data-ttu-id="32752-121">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="32752-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="32752-122">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="32752-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="32752-123">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="32752-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="32752-124">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="32752-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="32752-125">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="32752-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32752-126">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="32752-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`  
  
## <a name="see-also"></a><span data-ttu-id="32752-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32752-127">See Also</span></span>
