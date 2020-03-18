---
title: 介面屬性 - C# 程式設計手冊
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626616"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="f97be-102">介面屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f97be-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="f97be-103">屬性可以宣告於 [interface](../../language-reference/keywords/interface.md) 上。</span><span class="sxs-lookup"><span data-stu-id="f97be-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="f97be-104">以下示例聲明介面屬性訪問器：</span><span class="sxs-lookup"><span data-stu-id="f97be-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="f97be-105">介面屬性通常沒有正文。</span><span class="sxs-lookup"><span data-stu-id="f97be-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="f97be-106">訪問器指示屬性是讀寫、唯讀還是僅寫。</span><span class="sxs-lookup"><span data-stu-id="f97be-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="f97be-107">與類和結構不同，在沒有正文的情況下聲明訪問者不會聲明[自動實現的屬性](auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="f97be-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="f97be-108">從 C# 8.0 開始，介面可以定義成員的預設實現，包括屬性。</span><span class="sxs-lookup"><span data-stu-id="f97be-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="f97be-109">在介面中定義屬性的預設實現很少見，因為介面可能無法定義實例資料欄位。</span><span class="sxs-lookup"><span data-stu-id="f97be-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="f97be-110">範例</span><span class="sxs-lookup"><span data-stu-id="f97be-110">Example</span></span>

<span data-ttu-id="f97be-111">在此範例中，`IEmployee` 介面具有讀寫屬性 `Name` 和唯讀屬性 `Counter`。</span><span class="sxs-lookup"><span data-stu-id="f97be-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="f97be-112">`Employee` 類別會實作 `IEmployee` 介面，並使用這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="f97be-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="f97be-113">程式會讀取新員工的姓名和目前員工人數，並顯示員工姓名和計算的員工人數。</span><span class="sxs-lookup"><span data-stu-id="f97be-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="f97be-114">您可以使用屬性的完整名稱，而屬性參考在其中宣告成員的介面。</span><span class="sxs-lookup"><span data-stu-id="f97be-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="f97be-115">例如：</span><span class="sxs-lookup"><span data-stu-id="f97be-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="f97be-116">前面的示例演示[了明確介面實作](../interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="f97be-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="f97be-117">例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有 `Name` 屬性，則需要明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="f97be-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="f97be-118">也就是說，下列屬性宣告：</span><span class="sxs-lookup"><span data-stu-id="f97be-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="f97be-119">在 `IEmployee` 介面上實作 `Name` 屬性，而下列宣告：</span><span class="sxs-lookup"><span data-stu-id="f97be-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="f97be-120">在 `ICitizen` 介面上實作 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="f97be-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="f97be-121">範例輸出</span><span class="sxs-lookup"><span data-stu-id="f97be-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="f97be-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f97be-122">See also</span></span>

- [<span data-ttu-id="f97be-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f97be-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f97be-124">屬性</span><span class="sxs-lookup"><span data-stu-id="f97be-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="f97be-125">使用屬性</span><span class="sxs-lookup"><span data-stu-id="f97be-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="f97be-126">屬性與索引子之間的比較</span><span class="sxs-lookup"><span data-stu-id="f97be-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="f97be-127">索引子</span><span class="sxs-lookup"><span data-stu-id="f97be-127">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="f97be-128">介面</span><span class="sxs-lookup"><span data-stu-id="f97be-128">Interfaces</span></span>](../interfaces/index.md)
