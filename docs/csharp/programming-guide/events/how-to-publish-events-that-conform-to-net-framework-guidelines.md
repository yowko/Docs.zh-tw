---
title: '如何發行符合 .NET Framework 方針的事件-c # 程式設計手冊'
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 137e52b80703491a4528a3eddc7fa12f9dce6f52
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144795"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="48c5a-102">如何發行符合 .NET Framework 方針的事件（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="48c5a-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="48c5a-103">下列程序示範如何將遵循標準 .NET Framework 模式的事件，新增至您的類別和結構。</span><span class="sxs-lookup"><span data-stu-id="48c5a-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="48c5a-104">.NET Framework 類別庫中的所有事件都是以 <xref:System.EventHandler> 委派為基礎，其定義如下：</span><span class="sxs-lookup"><span data-stu-id="48c5a-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="48c5a-105">.NET Framework 2.0 引進此委派的泛型版本 <xref:System.EventHandler%601>。</span><span class="sxs-lookup"><span data-stu-id="48c5a-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="48c5a-106">下列範例示範如何使用這兩種版本。</span><span class="sxs-lookup"><span data-stu-id="48c5a-106">The following examples show how to use both versions.</span></span>

<span data-ttu-id="48c5a-107">雖然您所定義之類別中的事件能以任何有效的委派型別 (甚至是傳回值的委派) 為基礎，但通常建議您使用 <xref:System.EventHandler>，讓事件以 .NET Framework 模式為基礎，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="48c5a-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="48c5a-108">名稱 `EventHandler` 可能會造成一些混淆，因為它實際上不會處理事件。</span><span class="sxs-lookup"><span data-stu-id="48c5a-108">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="48c5a-109"><xref:System.EventHandler>、和泛型 <xref:System.EventHandler%601> 是委派類型。</span><span class="sxs-lookup"><span data-stu-id="48c5a-109">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="48c5a-110">其簽章符合委派定義的方法或 lambda 運算式是*事件處理常式*，而且會在引發事件時叫用。</span><span class="sxs-lookup"><span data-stu-id="48c5a-110">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="48c5a-111">發行以 EventHandler 模式為基礎的事件</span><span class="sxs-lookup"><span data-stu-id="48c5a-111">To publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="48c5a-112">（如果您不需要隨事件傳送自訂資料，請略過此步驟並移至步驟3a）。針對您的「發行者」和「訂閱者」類別顯示的範圍，宣告自訂資料的類別。</span><span class="sxs-lookup"><span data-stu-id="48c5a-112">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="48c5a-113">然後新增必要的成員來保存自訂事件資料。</span><span class="sxs-lookup"><span data-stu-id="48c5a-113">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="48c5a-114">在此範例中，會傳回一個簡單的字串。</span><span class="sxs-lookup"><span data-stu-id="48c5a-114">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="48c5a-115">（如果您使用的是泛型版本，請略過此步驟 <xref:System.EventHandler%601> ）。在發行類別中宣告委派。</span><span class="sxs-lookup"><span data-stu-id="48c5a-115">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="48c5a-116">提供結尾為的名稱 `EventHandler` 。</span><span class="sxs-lookup"><span data-stu-id="48c5a-116">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="48c5a-117">第二個參數指定您的自訂 `EventArgs` 類型。</span><span class="sxs-lookup"><span data-stu-id="48c5a-117">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="48c5a-118">使用下列其中一個步驟，在發行類別中宣告事件。</span><span class="sxs-lookup"><span data-stu-id="48c5a-118">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="48c5a-119">如果沒有自訂 EventArgs 類別，Event 類型將會是非泛型的 EventHandler 委派。</span><span class="sxs-lookup"><span data-stu-id="48c5a-119">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="48c5a-120">因為當您建立 C# 專案時所包含的 <xref:System> 命名空間中已宣告委派，所以您不需要宣告委派。</span><span class="sxs-lookup"><span data-stu-id="48c5a-120">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="48c5a-121">將下列程式碼新增至發行者類別。</span><span class="sxs-lookup"><span data-stu-id="48c5a-121">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="48c5a-122">如果您使用的是 <xref:System.EventHandler> 的非泛型版本，而且有衍生自 <xref:System.EventArgs> 的自訂類別，請在發行類別內宣告事件，並使用步驟 2 中的委派作為類型。</span><span class="sxs-lookup"><span data-stu-id="48c5a-122">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="48c5a-123">如果您使用的是泛型版本，則不需要自訂委派。</span><span class="sxs-lookup"><span data-stu-id="48c5a-123">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="48c5a-124">相反地，您會在發行類別中將事件類型指定為 `EventHandler<CustomEventArgs>`，來替代角括號之間的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="48c5a-124">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="48c5a-125">範例</span><span class="sxs-lookup"><span data-stu-id="48c5a-125">Example</span></span>

<span data-ttu-id="48c5a-126">下列範例使用自訂 EventArgs 類別和 <xref:System.EventHandler%601> 作為事件類型，來示範上述步驟。</span><span class="sxs-lookup"><span data-stu-id="48c5a-126">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="48c5a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48c5a-127">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="48c5a-128">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="48c5a-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="48c5a-129">事件</span><span class="sxs-lookup"><span data-stu-id="48c5a-129">Events</span></span>](index.md)
- [<span data-ttu-id="48c5a-130">委派</span><span class="sxs-lookup"><span data-stu-id="48c5a-130">Delegates</span></span>](../delegates/index.md)
