---
title: "使用原則處理訂"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86c7890af651ba9f0ee0ec2a1763f9c579bac89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="order-processing-with-policy"></a><span data-ttu-id="5283c-102">使用原則處理訂</span><span class="sxs-lookup"><span data-stu-id="5283c-102">Order Processing with Policy</span></span>
<span data-ttu-id="5283c-103">訂單處理原則範例將示範在 Windows Workflow Foundation (WF) 的 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 中引入的一些主要功能。</span><span class="sxs-lookup"><span data-stu-id="5283c-103">The Order Processing Policy sample demonstrates some of the key features introduced in the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] of the Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="5283c-104">下列是 WF 規則引擎的新功能：</span><span class="sxs-lookup"><span data-stu-id="5283c-104">The following functionality is new for the WF rules engine:</span></span>  
  
-   <span data-ttu-id="5283c-105">運算子多載支援。</span><span class="sxs-lookup"><span data-stu-id="5283c-105">Support for operator overloading.</span></span>  
  
-   <span data-ttu-id="5283c-106">`new` 運算子的支援，以便允許使用者從 WF 規則建立新的物件和陣列。</span><span class="sxs-lookup"><span data-stu-id="5283c-106">Support for the `new` operator, allowing users to create new objects and arrays from WF rules.</span></span>  
  
-   <span data-ttu-id="5283c-107">擴充方法的支援，可讓從 WF 規則呼叫擴充方法的使用者經驗與 C# 程式碼撰寫方式相容。</span><span class="sxs-lookup"><span data-stu-id="5283c-107">Support for extension methods to make the user experience in calling extension methods from WF rules compatible with C# coding styles.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5283c-108">此範例需安裝 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 才能建置及執行。</span><span class="sxs-lookup"><span data-stu-id="5283c-108">This sample requires that [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] is installed to build and run.</span></span> <span data-ttu-id="5283c-109">需要 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 才能開啟專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="5283c-109">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] is required to open the project and solution files.</span></span>  
  
 <span data-ttu-id="5283c-110">此範例將示範 `OrderProcessingPolicy` 專案，其中會輸入包含可用項目的編號清單以及郵遞區號的客戶訂單。</span><span class="sxs-lookup"><span data-stu-id="5283c-110">The sample demonstrates an `OrderProcessingPolicy` project in which a customer order, which consists of a numbered list of available items and a zip code, is entered.</span></span> <span data-ttu-id="5283c-111">如果兩個項目都正確，訂單便會成功處理，否則，原則會建立錯誤物件，並利用多載 `+` 運算子和預先定義的擴充方法來通知使用者發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5283c-111">The order is processed successfully if both entries are correct; otherwise, the policy creates error objects, utilizing an overloaded `+` operator and a predefined extension method to inform the user of the errors.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5283c-112">擴充方法，請參閱[C# 3.0 版規則](http://go.microsoft.com/fwlink/?LinkId=95402)。</span><span class="sxs-lookup"><span data-stu-id="5283c-112"> extension methods, see [C# Version 3.0 Specification](http://go.microsoft.com/fwlink/?LinkId=95402).</span></span>  
  
 <span data-ttu-id="5283c-113">此範例是由下列專案所組成：</span><span class="sxs-lookup"><span data-stu-id="5283c-113">The sample is comprised of the following projects:</span></span>  
  
-   `OrderErrorLibrary`  
  
     <span data-ttu-id="5283c-114">`OrderErrorLibrary` 是定義 `OrderError` 和 `OrderErrorCollection` 類別的類別程式庫。</span><span class="sxs-lookup"><span data-stu-id="5283c-114">The `OrderErrorLibrary` is a class library that defines `OrderError` and `OrderErrorCollection` classes.</span></span> <span data-ttu-id="5283c-115">`OrderError` 執行個體是在輸入無效輸入時所建立。</span><span class="sxs-lookup"><span data-stu-id="5283c-115">An `OrderError` instance is created when an invalid input is entered.</span></span> <span data-ttu-id="5283c-116">此類別程式庫也會提供 `OrderErrorCollection` 類別上的擴充方法，此方法會輸出 `ErrorText` 中所有 `OrderError` 物件上的 `OrderErrorCollection` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5283c-116">The library also provides an extension method on the `OrderErrorCollection` class that outputs the `ErrorText` property on all `OrderError` objects in the `OrderErrorCollection`.</span></span>  
  
-   `OrderProcessingPolicy`  
  
     <span data-ttu-id="5283c-117">`OrderProcessingPolicy` 專案是 WF 主控台應用程式，其中會定義單一 `PolicyFromFile` 活動。</span><span class="sxs-lookup"><span data-stu-id="5283c-117">The `OrderProcessingPolicy` project is a WF console application that defines a single `PolicyFromFile` activity.</span></span> <span data-ttu-id="5283c-118">此活動有下列規則：</span><span class="sxs-lookup"><span data-stu-id="5283c-118">The activity has the following rules:</span></span>  
  
    -   `invalidItemNum`  
  
         <span data-ttu-id="5283c-119">這個規則會驗證 1 到 6 之間 (包括 1 和 6) 的項目編號。</span><span class="sxs-lookup"><span data-stu-id="5283c-119">This rule validates that the item number is between 1 and 6, inclusive.</span></span> <span data-ttu-id="5283c-120">如果項目編號在有效範圍之內，此規則就不會執行任何動作 (除了列印至主控台)。</span><span class="sxs-lookup"><span data-stu-id="5283c-120">If the item number is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="5283c-121">如果項目編號不是在 1 到 6 之間，`invalidItemNum` 規則便會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5283c-121">If the item number is not between 1 and 6, the `invalidItemNum` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="5283c-122">建立新的 `OrderError` 物件，並將輸入的項目編號傳遞給它，然後在該物件上設定 `ErrorText` 和 `CustomerName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5283c-122">Creates a new `OrderError` object, passing it the item number entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="5283c-123">建立 `invalidItemNumErrorCollection` 物件。</span><span class="sxs-lookup"><span data-stu-id="5283c-123">Creates an `invalidItemNumErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="5283c-124">將新建立的 `OrderError` 執行個體新增至 `invalidItemNumErrorCollection`。</span><span class="sxs-lookup"><span data-stu-id="5283c-124">Adds the newly-created `OrderError` instance to the `invalidItemNumErrorCollection`.</span></span>  
  
         <span data-ttu-id="5283c-125">這樣便會示範 `new` 運算子的支援，而您可以透過該項支援來產生符合規則的物件。</span><span class="sxs-lookup"><span data-stu-id="5283c-125">This demonstrates support for the `new` operator, with which you can instantiate objects inside rules.</span></span>  
  
    -   `invalidZip`  
  
         <span data-ttu-id="5283c-126">這個規則會驗證郵遞區號有 5 個數字，而且範圍在 600 到 99998。</span><span class="sxs-lookup"><span data-stu-id="5283c-126">This rule validates that the zip code has 5 digits, and is within the range 600 to 99998.</span></span> <span data-ttu-id="5283c-127">如果郵遞區號在有效範圍之內，此規則就不會執行任何動作 (除了列印至主控台)。</span><span class="sxs-lookup"><span data-stu-id="5283c-127">If the zip code is within the valid range, the rule does nothing (other than printing to the console).</span></span> <span data-ttu-id="5283c-128">如果郵遞區號少於 5 碼，或者不是在 00600 到 99998 之間，`invalidZip` 規則便會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5283c-128">If the length of the zip code is less than 5, or the zip code is not between 00600 and 99998, the `invalidZip` rule does the following:</span></span>  
  
        1.  <span data-ttu-id="5283c-129">建立 `OrderError` 物件，並將輸入的郵遞區號傳遞給它，然後在該物件上設定 `ErrorText` 和 `CustomerName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5283c-129">Creates an `OrderError` object, passing it the zip code entered, and sets the `ErrorText` and `CustomerName` properties on the object.</span></span>  
  
        2.  <span data-ttu-id="5283c-130">建立 `invalidZipCodeErrorCollection` 物件。</span><span class="sxs-lookup"><span data-stu-id="5283c-130">Creates an `invalidZipCodeErrorCollection` object.</span></span>  
  
        3.  <span data-ttu-id="5283c-131">將新建立的 `OrderError` 執行個體新增至新建立的 `invalidZipCodeErrorCollection`。</span><span class="sxs-lookup"><span data-stu-id="5283c-131">Adds the newly-created `OrderError` instance to the newly-created `invalidZipCodeErrorCollection`.</span></span>  
  
         <span data-ttu-id="5283c-132">這個規則會再次示範 `new` 運算子的支援，而您可以透過它來產生符合規則的物件。</span><span class="sxs-lookup"><span data-stu-id="5283c-132">This rule again demonstrates support for the `new` operator, which allows you to instantiate objects inside rules.</span></span>  
  
    -   `displayErrors`  
  
         <span data-ttu-id="5283c-133">這個規則會檢查在兩個 `OrderErrorCollection` 物件 (`invalidItemNumErrorCollection` 和 `invalidIZipCodeErrorCollection`) 中的先前兩個規則是否有新增任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="5283c-133">This rule checks to see if there were any errors added by the previous two rules in the two `OrderErrorCollection` objects `invalidItemNumErrorCollection` and `invalidIZipCodeErrorCollection`.</span></span> <span data-ttu-id="5283c-134">如果有發生錯誤 (`invalidItemNumErrorCollection` 或 `invalidZipCodeErrorCollection` 不是 `null`)，規則便會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5283c-134">If there were errors (either `invalidItemNumErrorCollection` or `invalidZipCodeErrorCollection` is not `null`), the rule does the following:</span></span>  
  
        1.  <span data-ttu-id="5283c-135">呼叫多載`+`要複製的內容運算子`invalidItemNumErrorCollection`和`invalidZipCodeErrorCollection`至`invalidOrdersCollection``OrderErrorCollection`執行個體。</span><span class="sxs-lookup"><span data-stu-id="5283c-135">Calls the overloaded `+` operator to copy the contents of `invalidItemNumErrorCollection` and `invalidZipCodeErrorCollection` to an `invalidOrdersCollection``OrderErrorCollection` instance.</span></span>  
  
        2.  <span data-ttu-id="5283c-136">在 `PrintOrderErrors` 上呼叫 `invalidOrdersCollection` 擴充方法，並輸出 `ErrorText` 中所有 `orderError` 物件上的 `invalidOrdersCollection` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5283c-136">Calls the `PrintOrderErrors` extension method on `invalidOrdersCollection` and outputs the `ErrorText` property on all `orderError` objects in `invalidOrdersCollection`.</span></span>  
  
 <span data-ttu-id="5283c-137">在 `+` 專案中，`OrderErrorCollection` 上的多載運算子 `OrderErrorCollection` 是定義在 `OrderErrorLibrary` 類別中。</span><span class="sxs-lookup"><span data-stu-id="5283c-137">The overloaded operator `+` on the `OrderErrorCollection` is defined in the `OrderErrorCollection` class, in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="5283c-138">它會接受兩個 `OrderErrorCollection` 物件，並將它們結合成為一個 `OrderErrorCollection` 物件。</span><span class="sxs-lookup"><span data-stu-id="5283c-138">It takes two `OrderErrorCollection` objects and combines them into one `OrderErrorCollection` object.</span></span>  
  
 <span data-ttu-id="5283c-139">`PrintOrderErrors` 擴充方法也有定義在 `OrderErrorLibrary` 專案中。</span><span class="sxs-lookup"><span data-stu-id="5283c-139">The `PrintOrderErrors` extension method is also defined in the `OrderErrorLibrary` project.</span></span> <span data-ttu-id="5283c-140">擴充方法是新的 C# 功能，其可讓開發人員將新方法新增至現有 CLR 型別的公用合約，而不需為其衍生類別或重新編譯原始型別。</span><span class="sxs-lookup"><span data-stu-id="5283c-140">Extension methods are a new C# feature that enables developers to add new methods to the public contract of an existing CLR type, without having to derive a class from it or recompile the original type.</span></span>  
  
 <span data-ttu-id="5283c-141">執行範例時會出現提示，要求您輸入名稱、要購買之項目的項目編號以及郵遞區號。</span><span class="sxs-lookup"><span data-stu-id="5283c-141">When you run the sample you are prompted to enter a name, the item number of the item to be purchased, and a zip code.</span></span> <span data-ttu-id="5283c-142">這份資訊接著會由定義於原則活動中的規則加以驗證。</span><span class="sxs-lookup"><span data-stu-id="5283c-142">This information is then verified by the rules defined in the policy activity.</span></span> <span data-ttu-id="5283c-143">下列是來自此程式的輸出範例。</span><span class="sxs-lookup"><span data-stu-id="5283c-143">The following is sample output from the program.</span></span>  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5283c-144">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="5283c-144">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5283c-145">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 OrderProcessingPolicy.sln 專案檔。</span><span class="sxs-lookup"><span data-stu-id="5283c-145">Open the OrderProcessingPolicy.sln project file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="5283c-146">在此方案中有兩個不同的專案：`OrderErrorLibrary` 和 `OrderProcessingPolicy`。</span><span class="sxs-lookup"><span data-stu-id="5283c-146">There are two different projects in the solution: `OrderErrorLibrary` and `OrderProcessingPolicy`.</span></span> <span data-ttu-id="5283c-147">`OrderProcessingPolicy` 專案會使用定義於 `OrderErrorLibrary` 中的類別和方法。</span><span class="sxs-lookup"><span data-stu-id="5283c-147">The `OrderProcessingPolicy` project uses classes and methods defined in the `OrderErrorLibrary`.</span></span>  
  
3.  <span data-ttu-id="5283c-148">建置所有專案。</span><span class="sxs-lookup"><span data-stu-id="5283c-148">Build all projects.</span></span>  
  
4.  <span data-ttu-id="5283c-149">按一下 [執行] 。</span><span class="sxs-lookup"><span data-stu-id="5283c-149">Click **Run**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5283c-150">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5283c-150">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5283c-151">請先檢查下列 (預設) 目錄，然後再繼續：</span><span class="sxs-lookup"><span data-stu-id="5283c-151">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5283c-152">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="5283c-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5283c-153">此範例位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="5283c-153">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`