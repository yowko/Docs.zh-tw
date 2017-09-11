---
title: "C# 介面 - C# 語言教學課程"
description: "介面會定義 C# 中由類型實作的合約"
keywords: ".NET, csharp, 介面, 多重繼承, 多型"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="interfaces"></a><span data-ttu-id="18691-104">介面</span><span class="sxs-lookup"><span data-stu-id="18691-104">Interfaces</span></span>

<span data-ttu-id="18691-105">「介面」定義可由類別和結構實作的合約。</span><span class="sxs-lookup"><span data-stu-id="18691-105">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="18691-106">介面可以包含方法、屬性、事件和索引子。</span><span class="sxs-lookup"><span data-stu-id="18691-106">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="18691-107">介面不提供它所定義之成員的實作 (它只會指定必須由類別提供的成員或實作介面的結構)。</span><span class="sxs-lookup"><span data-stu-id="18691-107">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="18691-108">介面可以採用「多重繼承」。</span><span class="sxs-lookup"><span data-stu-id="18691-108">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="18691-109">在下列範例中，介面 `IComboBox` 同時繼承自 `ITextBox` 和 `IListBox`。</span><span class="sxs-lookup"><span data-stu-id="18691-109">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

<span data-ttu-id="18691-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span><span class="sxs-lookup"><span data-stu-id="18691-110">[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]</span></span>

<span data-ttu-id="18691-111">類別和結構可以實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="18691-111">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="18691-112">在下列範例中，類別 `EditBox` 可以實作 `IControl` 與 `IDataBound` 兩者。</span><span class="sxs-lookup"><span data-stu-id="18691-112">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

<span data-ttu-id="18691-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span><span class="sxs-lookup"><span data-stu-id="18691-113">[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]</span></span>

<span data-ttu-id="18691-114">當類別或結構實作特定介面時，可以將該類別或結構的執行個體隱含地轉換為該介面型別。</span><span class="sxs-lookup"><span data-stu-id="18691-114">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="18691-115">例如</span><span class="sxs-lookup"><span data-stu-id="18691-115">For example</span></span>

<span data-ttu-id="18691-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span><span class="sxs-lookup"><span data-stu-id="18691-116">[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]</span></span>

<span data-ttu-id="18691-117">在實作特定介面的執行個體無法確知的情況下，可以使用動態型別轉換。</span><span class="sxs-lookup"><span data-stu-id="18691-117">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="18691-118">例如，下列陳述式使用動態型別轉換以取得物件的 `IControl` 和 `IDataBound` 介面實作。</span><span class="sxs-lookup"><span data-stu-id="18691-118">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="18691-119">因為物件的執行階段實際型別是 `EditBox`，所以會轉型成功。</span><span class="sxs-lookup"><span data-stu-id="18691-119">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

<span data-ttu-id="18691-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span><span class="sxs-lookup"><span data-stu-id="18691-120">[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]</span></span>

<span data-ttu-id="18691-121">在上一個 `EditBox` 類別中，來自 `IControl` 介面的 `Paint` 方法和來自 `IDataBound` 介面的 `Bind` 方法，都使用公用成員來實作。</span><span class="sxs-lookup"><span data-stu-id="18691-121">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="18691-122">C# 也支援明確「介面成員實作」，啟用類別或結構以避免將成員設為公用。</span><span class="sxs-lookup"><span data-stu-id="18691-122">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="18691-123">明確介面成員實作是使用介面成員完整名稱來撰寫。</span><span class="sxs-lookup"><span data-stu-id="18691-123">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="18691-124">例如，`EditBox` 類別可以使用明確介面成員實作來實作 `IControl.Paint` 和 `IDataBound.Bind` 方法，如下所示。</span><span class="sxs-lookup"><span data-stu-id="18691-124">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

<span data-ttu-id="18691-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span><span class="sxs-lookup"><span data-stu-id="18691-125">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]</span></span>

<span data-ttu-id="18691-126">明確介面成員只能透過介面型別來存取。</span><span class="sxs-lookup"><span data-stu-id="18691-126">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="18691-127">例如，要先將 `EditBox` 參考轉換為 `IControl` 介面型別，才可以叫用上述 EditBox 類別所提供的 `IControl.Paint` 實作。</span><span class="sxs-lookup"><span data-stu-id="18691-127">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

<span data-ttu-id="18691-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span><span class="sxs-lookup"><span data-stu-id="18691-128">[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="18691-129">[上一頁](arrays.md)
[下一頁](enums.md)</span><span class="sxs-lookup"><span data-stu-id="18691-129">[Previous](arrays.md)
[Next](enums.md)</span></span>

