---
title: C# 介面 - C# 語言教學課程
description: 介面會定義 C# 中由類型實作的合約
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 240ddfb321c5a89c8aada4353845915d0e242ae0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634547"
---
# <a name="interfaces"></a><span data-ttu-id="64b7d-103">介面</span><span class="sxs-lookup"><span data-stu-id="64b7d-103">Interfaces</span></span>

<span data-ttu-id="64b7d-104">「介面」定義可由類別和結構實作的合約。</span><span class="sxs-lookup"><span data-stu-id="64b7d-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="64b7d-105">介面可以包含方法、屬性、事件和索引子。</span><span class="sxs-lookup"><span data-stu-id="64b7d-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="64b7d-106">介面不提供它所定義之成員的實作 (它只會指定必須由類別提供的成員或實作介面的結構)。</span><span class="sxs-lookup"><span data-stu-id="64b7d-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="64b7d-107">介面可以採用「多重繼承」。</span><span class="sxs-lookup"><span data-stu-id="64b7d-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="64b7d-108">在下列範例中，介面 `IComboBox` 同時繼承自 `ITextBox` 和 `IListBox`。</span><span class="sxs-lookup"><span data-stu-id="64b7d-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="64b7d-109">類別和結構可以實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="64b7d-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="64b7d-110">在下列範例中，類別 `EditBox` 可以實作 `IControl` 與 `IDataBound` 兩者。</span><span class="sxs-lookup"><span data-stu-id="64b7d-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="64b7d-111">當類別或結構實作特定介面時，可以將該類別或結構的執行個體隱含地轉換為該介面型別。</span><span class="sxs-lookup"><span data-stu-id="64b7d-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="64b7d-112">例如</span><span class="sxs-lookup"><span data-stu-id="64b7d-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="64b7d-113">在實作特定介面的執行個體無法確知的情況下，可以使用動態型別轉換。</span><span class="sxs-lookup"><span data-stu-id="64b7d-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="64b7d-114">例如，下列陳述式使用動態型別轉換以取得物件的 `IControl` 和 `IDataBound` 介面實作。</span><span class="sxs-lookup"><span data-stu-id="64b7d-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="64b7d-115">因為物件的執行階段實際型別是 `EditBox`，所以會轉型成功。</span><span class="sxs-lookup"><span data-stu-id="64b7d-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="64b7d-116">在上一個 `EditBox` 類別中，來自 `IControl` 介面的 `Paint` 方法和來自 `IDataBound` 介面的 `Bind` 方法，都使用公用成員來實作。</span><span class="sxs-lookup"><span data-stu-id="64b7d-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="64b7d-117">C# 也支援明確「介面成員實作」，啟用類別或結構以避免將成員設為公用。</span><span class="sxs-lookup"><span data-stu-id="64b7d-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="64b7d-118">明確介面成員實作是使用介面成員完整名稱來撰寫。</span><span class="sxs-lookup"><span data-stu-id="64b7d-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="64b7d-119">例如，`EditBox` 類別可以使用明確介面成員實作來實作 `IControl.Paint` 和 `IDataBound.Bind` 方法，如下所示。</span><span class="sxs-lookup"><span data-stu-id="64b7d-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="64b7d-120">明確介面成員只能透過介面型別來存取。</span><span class="sxs-lookup"><span data-stu-id="64b7d-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="64b7d-121">例如，要先將 `EditBox` 參考轉換為 `IControl` 介面型別，才可以叫用上述 EditBox 類別所提供的 `IControl.Paint` 實作。</span><span class="sxs-lookup"><span data-stu-id="64b7d-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="64b7d-122">[上一頁](arrays.md)
>[下一頁](enums.md)</span><span class="sxs-lookup"><span data-stu-id="64b7d-122">[Previous](arrays.md)
[Next](enums.md)</span></span>
