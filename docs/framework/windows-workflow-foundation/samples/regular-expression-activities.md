---
title: 規則運算式活動
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8f24694-49db-4339-92ec-014e3d4ae63b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 74aef126011789cfd48aa962973cc67a4132c224
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="regular-expression-activities"></a><span data-ttu-id="485ca-102">規則運算式活動</span><span class="sxs-lookup"><span data-stu-id="485ca-102">Regular Expression Activities</span></span>
<span data-ttu-id="485ca-103">這個範例示範如何建立可公開 <xref:System.Text.RegularExpressions> 命名空間規則運算式功能的一組活動。</span><span class="sxs-lookup"><span data-stu-id="485ca-103">This sample demonstrates how to create a set of activities that expose the regular expression functionality of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="485ca-104">這些自訂活動可用在工作流程應用程式中。</span><span class="sxs-lookup"><span data-stu-id="485ca-104">These custom activities can be used within a workflow application.</span></span> <span data-ttu-id="485ca-105">如需有關規則運算式的詳細資訊，請參閱[N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434)命名空間。</span><span class="sxs-lookup"><span data-stu-id="485ca-105">For more information about regular expressions, see [N:System.Text.RegularExpressions](http://go.microsoft.com/fwlink/?LinkId=150434) Namespace.</span></span>  
  
 <span data-ttu-id="485ca-106">下表詳述這個範例中的自訂活動。</span><span class="sxs-lookup"><span data-stu-id="485ca-106">The following table details the custom activities in this sample.</span></span>  
  
|<span data-ttu-id="485ca-107">活動</span><span class="sxs-lookup"><span data-stu-id="485ca-107">Activity</span></span>|<span data-ttu-id="485ca-108">描述</span><span class="sxs-lookup"><span data-stu-id="485ca-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="485ca-109">IsMatch</span><span class="sxs-lookup"><span data-stu-id="485ca-109">IsMatch</span></span>|<span data-ttu-id="485ca-110">指定規則運算式是否找到輸入字串的符合項目。</span><span class="sxs-lookup"><span data-stu-id="485ca-110">Specifies whether the regular expression found a match in the input string.</span></span>|  
|<span data-ttu-id="485ca-111">符合項目</span><span class="sxs-lookup"><span data-stu-id="485ca-111">Matches</span></span>|<span data-ttu-id="485ca-112">在輸入字串中搜尋規則運算式的所有符合項目，並傳回所有符合項目。</span><span class="sxs-lookup"><span data-stu-id="485ca-112">Searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span>|  
|<span data-ttu-id="485ca-113">取代</span><span class="sxs-lookup"><span data-stu-id="485ca-113">Replace</span></span>|<span data-ttu-id="485ca-114">在指定的輸入字串中，以指定的取代字串來取代符合規則運算式的字串。</span><span class="sxs-lookup"><span data-stu-id="485ca-114">Within a specified input string, replaces strings that match a regular expression pattern with a specified replacement string.</span></span>|  
  
## <a name="ismatch"></a><span data-ttu-id="485ca-115">IsMatch</span><span class="sxs-lookup"><span data-stu-id="485ca-115">IsMatch</span></span>  
 <span data-ttu-id="485ca-116">如果 `IsMatch` 字串屬性找到 `true` 屬性中所指定規則運算式的符合項目，`Input` 自訂動作會傳回 `Pattern`。</span><span class="sxs-lookup"><span data-stu-id="485ca-116">The `IsMatch` custom activity returns `true` if the `Input` string property finds a match in the regular expression specified in the `Pattern` property.</span></span> <span data-ttu-id="485ca-117">此活動衍生自 <xref:System.Activities.CodeActivity%601>，會在 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法中呼叫 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="485ca-117">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method.</span></span>  
  
 <span data-ttu-id="485ca-118">下表描述 `IsMatch` 自訂活動的屬性和傳回值。</span><span class="sxs-lookup"><span data-stu-id="485ca-118">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="485ca-119">屬性或傳回值</span><span class="sxs-lookup"><span data-stu-id="485ca-119">Property or Return Value</span></span>|<span data-ttu-id="485ca-120">描述</span><span class="sxs-lookup"><span data-stu-id="485ca-120">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="485ca-121">Pattern (必要)</span><span class="sxs-lookup"><span data-stu-id="485ca-121">Pattern (required)</span></span>|<span data-ttu-id="485ca-122">用來搜尋的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="485ca-122">The regular expression to search with.</span></span>|  
|<span data-ttu-id="485ca-123">Input (必要)</span><span class="sxs-lookup"><span data-stu-id="485ca-123">Input (required)</span></span>|<span data-ttu-id="485ca-124">要搜尋的輸入字串。</span><span class="sxs-lookup"><span data-stu-id="485ca-124">The input string to search.</span></span>|  
|<span data-ttu-id="485ca-125">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="485ca-125">RegexOptions</span></span>|<span data-ttu-id="485ca-126">位元 OR 組合的[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446)列舉值。</span><span class="sxs-lookup"><span data-stu-id="485ca-126">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="485ca-127">傳回值</span><span class="sxs-lookup"><span data-stu-id="485ca-127">Return value</span></span>|<span data-ttu-id="485ca-128">如果輸入找到所提供模式的符合項目，則為 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="485ca-128">`true` if the input finds a match in the provided pattern; otherwise `false`.</span></span>|  
  
 <span data-ttu-id="485ca-129">下列程式碼範例示範如何使用 `IsMatch` 自訂活動。</span><span class="sxs-lookup"><span data-stu-id="485ca-129">The following code example demonstrates how to use the `IsMatch` custom activity.</span></span>  
  
```  
new IsMatch  
{  
    Pattern = new InArgument<string>( @"^-?\d+(\.\d{2})?$"),  
    Input = "20.00",  
};  
```  
  
## <a name="matches"></a><span data-ttu-id="485ca-130">符合項目</span><span class="sxs-lookup"><span data-stu-id="485ca-130">Matches</span></span>  
 <span data-ttu-id="485ca-131">`Matches` 自訂活動會在輸入字串中搜尋規則運算式的所有符合項目，並傳回所有符合項目。</span><span class="sxs-lookup"><span data-stu-id="485ca-131">The `Matches` custom activity searches an input string for all occurrences of a regular expression and returns all the successful matches.</span></span> <span data-ttu-id="485ca-132">此活動衍生自 <xref:System.Activities.CodeActivity%601>，會在 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法中呼叫 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="485ca-132">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Matches%2A> method.</span></span>  
  
 <span data-ttu-id="485ca-133">下表描述 `IsMatch` 自訂活動的屬性和傳回值。</span><span class="sxs-lookup"><span data-stu-id="485ca-133">The following table describes the properties and return value for the `IsMatch` custom activity.</span></span>  
  
|<span data-ttu-id="485ca-134">屬性或傳回值</span><span class="sxs-lookup"><span data-stu-id="485ca-134">Property or Return Value</span></span>|<span data-ttu-id="485ca-135">描述</span><span class="sxs-lookup"><span data-stu-id="485ca-135">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="485ca-136">Pattern (必要)</span><span class="sxs-lookup"><span data-stu-id="485ca-136">Pattern (required)</span></span>|<span data-ttu-id="485ca-137">用來搜尋的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="485ca-137">The regular expression to search with.</span></span>|  
|<span data-ttu-id="485ca-138">Input (必要)</span><span class="sxs-lookup"><span data-stu-id="485ca-138">Input (required)</span></span>|<span data-ttu-id="485ca-139">要搜尋的輸入字串。</span><span class="sxs-lookup"><span data-stu-id="485ca-139">The input string to search.</span></span>|  
|<span data-ttu-id="485ca-140">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="485ca-140">RegexOptions</span></span>|<span data-ttu-id="485ca-141">位元 OR 組合的[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446)列舉值。</span><span class="sxs-lookup"><span data-stu-id="485ca-141">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="485ca-142">傳回值</span><span class="sxs-lookup"><span data-stu-id="485ca-142">Return Value</span></span>|<span data-ttu-id="485ca-143"><xref:System.Text.RegularExpressions.MatchCollection>，其中包含所有符合項目的集合。</span><span class="sxs-lookup"><span data-stu-id="485ca-143">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="485ca-144">下列程式碼範例示範如何使用 `Matches` 自訂活動。</span><span class="sxs-lookup"><span data-stu-id="485ca-144">The following code example demonstrates how to use the `Matches` custom activity.</span></span>  
  
```  
new Matches  
{  
    Pattern = @"\b(?<word>\w+)\s+(\k<word>)\b",  
    Input = "The quick brown fox  fox jumped over over the lazy dog dog.",  
};  
```  
  
## <a name="replace"></a><span data-ttu-id="485ca-145">取代</span><span class="sxs-lookup"><span data-stu-id="485ca-145">Replace</span></span>  
 <span data-ttu-id="485ca-146">`Replace` 自訂活動會搜尋輸入字串，並以字串取代符合指定之規則運算式的所有字串。</span><span class="sxs-lookup"><span data-stu-id="485ca-146">The `Replace` custom activity searches an input string and replaces all strings that match a specified regular expression with a string.</span></span> <span data-ttu-id="485ca-147">此活動衍生自 <xref:System.Activities.CodeActivity%601>，會在 <xref:System.Activities.CodeActivity%601.Execute%2A> 方法中呼叫 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="485ca-147">The activity derives from <xref:System.Activities.CodeActivity%601> and within the <xref:System.Activities.CodeActivity%601.Execute%2A> method calls the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method.</span></span>  
  
 <span data-ttu-id="485ca-148">下表描述 `Replace` 自訂活動的屬性和傳回值。</span><span class="sxs-lookup"><span data-stu-id="485ca-148">The following table describes the properties and return value for the `Replace` custom activity.</span></span>  
  
|<span data-ttu-id="485ca-149">屬性或傳回值</span><span class="sxs-lookup"><span data-stu-id="485ca-149">Property or Return Value</span></span>|<span data-ttu-id="485ca-150">描述</span><span class="sxs-lookup"><span data-stu-id="485ca-150">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="485ca-151">Pattern (必要)</span><span class="sxs-lookup"><span data-stu-id="485ca-151">Pattern (required)</span></span>|<span data-ttu-id="485ca-152">用來搜尋的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="485ca-152">The regular expression to search with.</span></span>|  
|<span data-ttu-id="485ca-153">Input (必要)</span><span class="sxs-lookup"><span data-stu-id="485ca-153">Input (required)</span></span>|<span data-ttu-id="485ca-154">要搜尋的輸入字串。</span><span class="sxs-lookup"><span data-stu-id="485ca-154">The input string to search.</span></span>|  
|<span data-ttu-id="485ca-155">Replacement</span><span class="sxs-lookup"><span data-stu-id="485ca-155">Replacement</span></span>|<span data-ttu-id="485ca-156">取代字串。</span><span class="sxs-lookup"><span data-stu-id="485ca-156">The replacement string.</span></span><br /><br /> <span data-ttu-id="485ca-157">如果指定 `Replacement`，則會忽略 `MatchEvaluator` 屬性。</span><span class="sxs-lookup"><span data-stu-id="485ca-157">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="485ca-158">必須設定 `Replacement` 或 `MatchEvaluator` 其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="485ca-158">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="485ca-159">MatchEvaluator</span><span class="sxs-lookup"><span data-stu-id="485ca-159">MatchEvaluator</span></span>|<span data-ttu-id="485ca-160">檢查每個符合項目並傳回原始符合字串或取代字串的自訂方法。</span><span class="sxs-lookup"><span data-stu-id="485ca-160">A custom method that examines each match and returns either the original matched string or a replacement string.</span></span><br /><br /> <span data-ttu-id="485ca-161">如果指定 `Replacement`，則會忽略 `MatchEvaluator` 屬性。</span><span class="sxs-lookup"><span data-stu-id="485ca-161">If a `Replacement` is specified, then the `MatchEvaluator` property is ignored.</span></span> <span data-ttu-id="485ca-162">必須設定 `Replacement` 或 `MatchEvaluator` 其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="485ca-162">Either the `Replacement` or `MatchEvaluator` property must be set.</span></span>|  
|<span data-ttu-id="485ca-163">RegexOptions</span><span class="sxs-lookup"><span data-stu-id="485ca-163">RegexOptions</span></span>|<span data-ttu-id="485ca-164">位元 OR 組合的[RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446)列舉值。</span><span class="sxs-lookup"><span data-stu-id="485ca-164">Bitwise OR combination of [RegexOptions](http://go.microsoft.com/fwlink/?LinkId=150446) enumeration values.</span></span>|  
|<span data-ttu-id="485ca-165">傳回值</span><span class="sxs-lookup"><span data-stu-id="485ca-165">Return Value</span></span>|<span data-ttu-id="485ca-166"><xref:System.Text.RegularExpressions.MatchCollection>，其中包含所有符合項目的集合。</span><span class="sxs-lookup"><span data-stu-id="485ca-166">A <xref:System.Text.RegularExpressions.MatchCollection> that contains the collection of successful matches.</span></span>|  
  
 <span data-ttu-id="485ca-167">下列程式碼範例示範如何使用 `Replace` 自訂活動。</span><span class="sxs-lookup"><span data-stu-id="485ca-167">The following code example demonstrates how to use the `Replace` custom activity.</span></span>  
  
```  
// Using the replacement string.  
new Replace  
{  
    Pattern = @"\bWorld\b",  
    Input = "Hello World! This is a wonderful World",  
    Replacement = "Universe"  
};  
  
// Using a match evaluator.  
new Replace  
{  
    Pattern = new InArgument<string>(pattern),  
    Input = new InArgument<string>(input),  
    MatchEvaluator = new MatchEvaluator(CapText)                  
};  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="485ca-168">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="485ca-168">To use this sample</span></span>  
  
1.  <span data-ttu-id="485ca-169">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 RegexActivities.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="485ca-169">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RegexActivities.sln solution file.</span></span>  
  
2.  <span data-ttu-id="485ca-170">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="485ca-170">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="485ca-171">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="485ca-171">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="485ca-172">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="485ca-172">The samples may already be installed on your machine.</span></span> <span data-ttu-id="485ca-173">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="485ca-173">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="485ca-174">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="485ca-174">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="485ca-175">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="485ca-175">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Regex`