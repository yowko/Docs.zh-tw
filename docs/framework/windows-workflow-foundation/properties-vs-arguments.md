---
title: "屬性與。引數"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1b9083ecd147a1247209b272dfd1d7b0e3c74f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="properties-vs-arguments"></a><span data-ttu-id="117b4-102">屬性與。引數</span><span class="sxs-lookup"><span data-stu-id="117b4-102">Properties vs. Arguments</span></span>
<span data-ttu-id="117b4-103">有許多選項可用來將資料傳入活動。</span><span class="sxs-lookup"><span data-stu-id="117b4-103">There are several options available for passing data into an activity.</span></span> <span data-ttu-id="117b4-104">除了使用 <xref:System.Activities.InArgument> 以外，您也可以使用標準 CLR 屬性或公用 <xref:System.Activities.ActivityAction> 屬性來開發接收資料的活動。</span><span class="sxs-lookup"><span data-stu-id="117b4-104">In addition to using <xref:System.Activities.InArgument>, activities can also be developed that receive data using either standard CLR Properties or public <xref:System.Activities.ActivityAction> properties.</span></span> <span data-ttu-id="117b4-105">本主題將討論如何選取適當的方法類型。</span><span class="sxs-lookup"><span data-stu-id="117b4-105">This topic discusses how to select the appropriate method type.</span></span>  
  
## <a name="using-clr-properties"></a><span data-ttu-id="117b4-106">使用 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="117b4-106">Using CLR Properties</span></span>  
 <span data-ttu-id="117b4-107">將資料傳入活動時，CLR 屬性 (亦即，使用 Get 和 Set 常式來公開資料的公用方法) 是具有最多限制的選項。</span><span class="sxs-lookup"><span data-stu-id="117b4-107">When passing data into an activity, CLR properties (that is, public methods that use Get and Set routines to expose data) are the option that has the most restrictions.</span></span> <span data-ttu-id="117b4-108">編譯方案時，必須已知傳入 CLR 屬性的參數值。此值對於工作流程的每個執行個體都相同。</span><span class="sxs-lookup"><span data-stu-id="117b4-108">The value of a parameter passed into a CLR property must be known when the solution is compiled; this value will be the same for every instance of the workflow.</span></span> <span data-ttu-id="117b4-109">如此一來，傳遞到 CLR 屬性的值就會類似程式碼中定義的常數；在活動存留期內，這個值不能更改，也不能因為該活動的不同執行個體而更改。</span><span class="sxs-lookup"><span data-stu-id="117b4-109">In this way, a value passed into a CLR property is similar to a constant defined in code; this value can’t change for the life of the activity, and can’t be changed for different instances of the activity.</span></span> <span data-ttu-id="117b4-110"><xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> 是 CLR 屬性範例，該屬性由活動公開；該活動所呼叫的方法名稱不能隨著執行階段條件而變更，且在該活動的每個執行個體中皆相同。</span><span class="sxs-lookup"><span data-stu-id="117b4-110"><xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> is an example of a CLR property exposed by an activity; the method name that the activity calls can’t be changed based on runtime conditions, and will be the same for every instance of the activity.</span></span>  
  
## <a name="using-arguments"></a><span data-ttu-id="117b4-111">使用引數</span><span class="sxs-lookup"><span data-stu-id="117b4-111">Using Arguments</span></span>  
 <span data-ttu-id="117b4-112">如果在活動存留期內只評估資料一次，則應使用引數；也就是說，在活動存留期內，其值不會更改，但這個值在活動的不同執行個體中是可以改變的。</span><span class="sxs-lookup"><span data-stu-id="117b4-112">Arguments should be used when data is only evaluated once during the lifetime of the activity; that is, its value will not change during the lifetime of the activity, but the value can be different for different instances of the activity.</span></span> <span data-ttu-id="117b4-113"><xref:System.Activities.Statements.If.Condition%2A> 是只評估一次的值的範例；因此，該值會定義為引數。</span><span class="sxs-lookup"><span data-stu-id="117b4-113"><xref:System.Activities.Statements.If.Condition%2A> is an example of a value that gets evaluated once; therefore it is defined as an argument.</span></span> <span data-ttu-id="117b4-114"><xref:System.Activities.Statements.WriteLine.Text%2A> 是另一個應定義為引數之方法的範例，因為在活動執行期間只會評估這個方法一次，但在活動的不同執行個體中可以不同。</span><span class="sxs-lookup"><span data-stu-id="117b4-114"><xref:System.Activities.Statements.WriteLine.Text%2A> is another example of a method that should be defined as an argument, since it is only evaluated once during the activity’s execution, but it can be different for different instances of the activity.</span></span>  
  
## <a name="using-activityaction"></a><span data-ttu-id="117b4-115">使用 ActivityAction</span><span class="sxs-lookup"><span data-stu-id="117b4-115">Using ActivityAction</span></span>  
 <span data-ttu-id="117b4-116">當資料必須在活動執行的存留期內評估多次時，您就應該使用 <xref:System.Activities.ActivityAction>。</span><span class="sxs-lookup"><span data-stu-id="117b4-116">When data needs to be evaluated multiple times during the lifetime of an activity’s execution, an <xref:System.Activities.ActivityAction> should be used.</span></span> <span data-ttu-id="117b4-117">例如，系統會針對 <xref:System.Activities.Statements.While.Condition%2A> 迴圈的每個反覆項目評估 <xref:System.Activities.Statements.While> 屬性。</span><span class="sxs-lookup"><span data-stu-id="117b4-117">For example, the <xref:System.Activities.Statements.While.Condition%2A> property is evaluated for each iteration of the <xref:System.Activities.Statements.While> loop.</span></span> <span data-ttu-id="117b4-118">如果 <xref:System.Activities.InArgument> 已用於此目的，迴圈永遠都不會結束，因為系統不會針對每個反覆項目重新評估引數，而且一定會傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="117b4-118">If an <xref:System.Activities.InArgument> were used for this purpose, the loop would never exit, since the argument would not be reevaluated for each iteration, and would always return the same result.</span></span>
