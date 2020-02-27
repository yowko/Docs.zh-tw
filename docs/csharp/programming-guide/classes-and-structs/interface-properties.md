---
title: 介面屬性 - C# 程式設計手冊
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626616"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="ae7a3-102">介面屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="ae7a3-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="ae7a3-103">屬性可以宣告於 [interface](../../language-reference/keywords/interface.md) 上。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="ae7a3-104">下列範例會宣告介面屬性存取子：</span><span class="sxs-lookup"><span data-stu-id="ae7a3-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="ae7a3-105">介面屬性通常不會有主體。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="ae7a3-106">存取子會指出屬性為讀寫、唯讀或僅寫入。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="ae7a3-107">不同于類別和結構，宣告不含主體的存取子並不會宣告[自動實作為屬性](auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="ae7a3-108">從C# 8.0 開始，介面可能會定義成員的預設實值，包括屬性。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="ae7a3-109">在介面中定義屬性的預設實為罕見，因為介面可能不會定義實例資料欄位。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="ae7a3-110">範例</span><span class="sxs-lookup"><span data-stu-id="ae7a3-110">Example</span></span>

<span data-ttu-id="ae7a3-111">在此範例中，`IEmployee` 介面具有讀寫屬性 `Name` 和唯讀屬性 `Counter`。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="ae7a3-112">`Employee` 類別會實作 `IEmployee` 介面，並使用這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="ae7a3-113">程式會讀取新員工的姓名和目前員工人數，並顯示員工姓名和計算的員工人數。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="ae7a3-114">您可以使用屬性的完整名稱，而屬性參考在其中宣告成員的介面。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="ae7a3-115">例如：</span><span class="sxs-lookup"><span data-stu-id="ae7a3-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="ae7a3-116">上述範例示範[明確的介面執行](../interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="ae7a3-117">例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有 `Name` 屬性，則需要明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="ae7a3-118">也就是說，下列屬性宣告：</span><span class="sxs-lookup"><span data-stu-id="ae7a3-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="ae7a3-119">在 `Name` 介面上實作 `IEmployee` 屬性，而下列宣告：</span><span class="sxs-lookup"><span data-stu-id="ae7a3-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="ae7a3-120">在 `Name` 介面上實作 `ICitizen` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ae7a3-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="ae7a3-121">範例輸出</span><span class="sxs-lookup"><span data-stu-id="ae7a3-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="ae7a3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae7a3-122">See also</span></span>

- [<span data-ttu-id="ae7a3-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ae7a3-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ae7a3-124">屬性</span><span class="sxs-lookup"><span data-stu-id="ae7a3-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="ae7a3-125">使用屬性</span><span class="sxs-lookup"><span data-stu-id="ae7a3-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="ae7a3-126">屬性與索引子之間的比較</span><span class="sxs-lookup"><span data-stu-id="ae7a3-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="ae7a3-127">索引子</span><span class="sxs-lookup"><span data-stu-id="ae7a3-127">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="ae7a3-128">介面</span><span class="sxs-lookup"><span data-stu-id="ae7a3-128">Interfaces</span></span>](../interfaces/index.md)
