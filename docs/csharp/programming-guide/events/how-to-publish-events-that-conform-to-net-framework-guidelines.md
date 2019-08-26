---
title: 作法：發行符合 .NET Framework 方針的事件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8cf0f57caad41da0a29b935029731260154a2dc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924028"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="4d781-102">作法：發行符合 .NET Framework 方針的事件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="4d781-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="4d781-103">下列程序示範如何將遵循標準 .NET Framework 模式的事件，新增至您的類別和結構。</span><span class="sxs-lookup"><span data-stu-id="4d781-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="4d781-104">.NET Framework 類別庫中的所有事件都是以 <xref:System.EventHandler> 委派為基礎，其定義如下：</span><span class="sxs-lookup"><span data-stu-id="4d781-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="4d781-105">.NET Framework 2.0 引進此委派的泛型版本 <xref:System.EventHandler%601>。</span><span class="sxs-lookup"><span data-stu-id="4d781-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="4d781-106">下列範例示範如何使用這兩種版本。</span><span class="sxs-lookup"><span data-stu-id="4d781-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="4d781-107">雖然您所定義之類別中的事件能以任何有效的委派型別 (甚至是傳回值的委派) 為基礎，但通常建議您使用 <xref:System.EventHandler>，讓事件以 .NET Framework 模式為基礎，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4d781-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="4d781-108">發行以 EventHandler 模式為基礎的事件</span><span class="sxs-lookup"><span data-stu-id="4d781-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="4d781-109">(如果您不需要傳送事件的自訂資料，請跳過此步驟，並前往步驟 3a。)以發行者和訂閱者類別可見的範圍，宣告自訂資料的類別。</span><span class="sxs-lookup"><span data-stu-id="4d781-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="4d781-110">然後新增必要的成員來保存自訂事件資料。</span><span class="sxs-lookup"><span data-stu-id="4d781-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="4d781-111">在此範例中，會傳回一個簡單的字串。</span><span class="sxs-lookup"><span data-stu-id="4d781-111">In this example, a simple string is returned.</span></span>  
  
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
  
2. <span data-ttu-id="4d781-112">(如果您要使用 <xref:System.EventHandler%601> 的泛型版本，請跳過此步驟。)在發行類別中宣告委派。</span><span class="sxs-lookup"><span data-stu-id="4d781-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="4d781-113">指定名稱並以 *EventHandler* 作為結尾。</span><span class="sxs-lookup"><span data-stu-id="4d781-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="4d781-114">第二個參數指定自訂 EventArgs 類型。</span><span class="sxs-lookup"><span data-stu-id="4d781-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="4d781-115">使用下列其中一個步驟，在發行類別中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="4d781-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="4d781-116">如果沒有自訂 EventArgs 類別，Event 類型將會是非泛型的 EventHandler 委派。</span><span class="sxs-lookup"><span data-stu-id="4d781-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="4d781-117">因為當您建立 C# 專案時所包含的 <xref:System> 命名空間中已宣告委派，所以您不需要宣告委派。</span><span class="sxs-lookup"><span data-stu-id="4d781-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="4d781-118">將下列程式碼新增至發行者類別。</span><span class="sxs-lookup"><span data-stu-id="4d781-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="4d781-119">如果您使用的是 <xref:System.EventHandler> 的非泛型版本，而且有衍生自 <xref:System.EventArgs> 的自訂類別，請在發行類別內宣告事件，並使用步驟 2 中的委派作為類型。</span><span class="sxs-lookup"><span data-stu-id="4d781-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="4d781-120">如果您使用的是泛型版本，則不需要自訂委派。</span><span class="sxs-lookup"><span data-stu-id="4d781-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="4d781-121">相反地，您會在發行類別中將事件類型指定為 `EventHandler<CustomEventArgs>`，來替代角括號之間的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="4d781-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="4d781-122">範例</span><span class="sxs-lookup"><span data-stu-id="4d781-122">Example</span></span>  
 <span data-ttu-id="4d781-123">下列範例使用自訂 EventArgs 類別和 <xref:System.EventHandler%601> 作為事件類型，來示範上述步驟。</span><span class="sxs-lookup"><span data-stu-id="4d781-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4d781-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d781-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="4d781-125">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4d781-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4d781-126">事件</span><span class="sxs-lookup"><span data-stu-id="4d781-126">Events</span></span>](./index.md)
- [<span data-ttu-id="4d781-127">委派</span><span class="sxs-lookup"><span data-stu-id="4d781-127">Delegates</span></span>](../delegates/index.md)
