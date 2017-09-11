---
title: "如何：發行符合 .NET Framework 方針的事件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 6d529e60643966fbabd5290543146977b4dc83c5
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="5085f-102">如何：發行符合 .NET Framework 方針的事件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5085f-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="5085f-103">下列程序示範如何將遵循標準 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 模式的事件，新增至您的類別和結構。</span><span class="sxs-lookup"><span data-stu-id="5085f-103">The following procedure demonstrates how to add events that follow the standard [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] pattern to your classes and structs.</span></span> <span data-ttu-id="5085f-104">[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] Class Library 中的所有事件都是以定義如下的 <xref:System.EventHandler> 委派為基礎：</span><span class="sxs-lookup"><span data-stu-id="5085f-104">All events in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="5085f-105">[!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] 引進此委派的泛型版本 <xref:System.EventHandler%601>。</span><span class="sxs-lookup"><span data-stu-id="5085f-105">The [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="5085f-106">下列範例示範如何使用這兩種版本。</span><span class="sxs-lookup"><span data-stu-id="5085f-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="5085f-107">雖然您所定義之類別中的所有事件都能以任何有效的委派類型 (甚至是傳回值的委派) 為基礎，但通常建議您使用 <xref:System.EventHandler>，讓事件以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 模式為基礎，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5085f-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="5085f-108">發行以 EventHandler 模式為基礎的事件</span><span class="sxs-lookup"><span data-stu-id="5085f-108">To publish events based on the EventHandler pattern</span></span>  
  
1.  <span data-ttu-id="5085f-109">(如果您不需要傳送事件的自訂資料，請跳過此步驟，並前往步驟 3a。)以發行者和訂閱者類別可見的範圍，宣告自訂資料的類別。</span><span class="sxs-lookup"><span data-stu-id="5085f-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="5085f-110">然後新增必要的成員來保存自訂事件資料。</span><span class="sxs-lookup"><span data-stu-id="5085f-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="5085f-111">在此範例中，會傳回一個簡單的字串。</span><span class="sxs-lookup"><span data-stu-id="5085f-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  <span data-ttu-id="5085f-112">(如果您要使用 <xref:System.EventHandler%601> 的泛型版本，請跳過此步驟。)在發行類別中宣告委派。</span><span class="sxs-lookup"><span data-stu-id="5085f-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="5085f-113">指定名稱並以 *EventHandler* 作為結尾。</span><span class="sxs-lookup"><span data-stu-id="5085f-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="5085f-114">第二個參數指定自訂 EventArgs 類型。</span><span class="sxs-lookup"><span data-stu-id="5085f-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  <span data-ttu-id="5085f-115">使用下列其中一個步驟，在發行類別中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="5085f-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1.  <span data-ttu-id="5085f-116">如果沒有自訂 EventArgs 類別，Event 類型將會是非泛型的 EventHandler 委派。</span><span class="sxs-lookup"><span data-stu-id="5085f-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="5085f-117">因為當您建立 C# 專案時所包含的 <xref:System> 命名空間中已宣告委派，所以您不需要宣告委派。</span><span class="sxs-lookup"><span data-stu-id="5085f-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="5085f-118">將下列程式碼新增至發行者類別。</span><span class="sxs-lookup"><span data-stu-id="5085f-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  <span data-ttu-id="5085f-119">如果您使用的是 <xref:System.EventHandler> 的非泛型版本，而且有衍生自 <xref:System.EventArgs> 的自訂類別，請在發行類別內宣告事件，並使用步驟 2 中的委派作為類型。</span><span class="sxs-lookup"><span data-stu-id="5085f-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  <span data-ttu-id="5085f-120">如果您使用的是泛型版本，則不需要自訂委派。</span><span class="sxs-lookup"><span data-stu-id="5085f-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="5085f-121">相反地，您會在發行類別中將事件類型指定為 `EventHandler<CustomEventArgs>`，來替代角括號之間的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="5085f-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="5085f-122">範例</span><span class="sxs-lookup"><span data-stu-id="5085f-122">Example</span></span>  
 <span data-ttu-id="5085f-123">下列範例使用自訂 EventArgs 類別和 <xref:System.EventHandler%601> 作為事件類型，來示範上述步驟。</span><span class="sxs-lookup"><span data-stu-id="5085f-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 <span data-ttu-id="5085f-124">[!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5085f-124">[!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5085f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5085f-125">See Also</span></span>  
 <span data-ttu-id="5085f-126"><xref:System.Delegate></span><span class="sxs-lookup"><span data-stu-id="5085f-126"><xref:System.Delegate></span></span>   
<span data-ttu-id="5085f-127"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5085f-127"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="5085f-128"> [事件](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="5085f-128"> [Events](../../../csharp/programming-guide/events/index.md) </span></span>  
<span data-ttu-id="5085f-129"> [委派](../../../csharp/programming-guide/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="5085f-129"> [Delegates](../../../csharp/programming-guide/delegates/index.md)</span></span>
