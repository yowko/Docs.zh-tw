---
title: '如何宣告和使用讀寫屬性-c # 程式設計指南'
description: '瞭解如何在 c # 中使用讀取/寫入屬性。 此範例包含兩個屬性，其中每個屬性都有 get 和 set 存取子，因此屬性是讀取/寫入。'
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 75f3b4d6fa8595734cf1310c08281c26c829fd84
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899018"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="f55b4-104">如何宣告和使用讀寫屬性 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="f55b4-104">How to declare and use read write properties (C# Programming Guide)</span></span>

<span data-ttu-id="f55b4-105">屬性會提供公用資料成員的便利性，卻沒有不受保護、控制和驗證存取物件資料所附帶的風險。</span><span class="sxs-lookup"><span data-stu-id="f55b4-105">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="f55b4-106">這是透過「存取子」完成的：從基礎資料成員指派和擷取值的特殊方法。</span><span class="sxs-lookup"><span data-stu-id="f55b4-106">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="f55b4-107">[set](../../language-reference/keywords/set.md) 存取子可讓資料成員被指派，而 [get](../../language-reference/keywords/get.md) 存取子可擷取資料成員值。</span><span class="sxs-lookup"><span data-stu-id="f55b4-107">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="f55b4-108">這個範例會示範有兩個屬性的 `Person` 類別：`Name` (字串) 和 `Age` (整數)。</span><span class="sxs-lookup"><span data-stu-id="f55b4-108">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="f55b4-109">這兩個屬性都提供 `get` 和 `set` 存取子，所以它們被視為讀取/寫入屬性。</span><span class="sxs-lookup"><span data-stu-id="f55b4-109">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f55b4-110">範例</span><span class="sxs-lookup"><span data-stu-id="f55b4-110">Example</span></span>  

 [!code-csharp[properties#1](snippets/how-to-declare-and-use-read-write-properties/Program.cs#1)]
  
## <a name="robust-programming"></a><span data-ttu-id="f55b4-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="f55b4-111">Robust Programming</span></span>  

 <span data-ttu-id="f55b4-112">在上例中，`Name` 和 `Age` 屬性是[公用的](../../language-reference/keywords/public.md)，且同時包含 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="f55b4-112">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="f55b4-113">這可讓任何物件讀取和寫入這些屬性。</span><span class="sxs-lookup"><span data-stu-id="f55b4-113">This allows any object to read and write these properties.</span></span> <span data-ttu-id="f55b4-114">但有時候會很想排除其中一個存取子。</span><span class="sxs-lookup"><span data-stu-id="f55b4-114">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="f55b4-115">例如，省略 `set` 存取子會讓屬性變成唯讀的：</span><span class="sxs-lookup"><span data-stu-id="f55b4-115">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[properties#2](snippets/how-to-declare-and-use-read-write-properties/Program.cs#2)]
  
 <span data-ttu-id="f55b4-116">或者，您也可以向公眾公開某個存取子，但讓其他存取子為私用或受保護的。</span><span class="sxs-lookup"><span data-stu-id="f55b4-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="f55b4-117">如需詳細資訊，請參閱[非對稱存取子的存取範圍](./restricting-accessor-accessibility.md)。</span><span class="sxs-lookup"><span data-stu-id="f55b4-117">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="f55b4-118">屬性一旦宣告，即可當成類別的欄位使用。</span><span class="sxs-lookup"><span data-stu-id="f55b4-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="f55b4-119">這在取得和設定屬性值時，可使用非常自然的語法，如下列陳述式所示：</span><span class="sxs-lookup"><span data-stu-id="f55b4-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[properties#3](snippets/how-to-declare-and-use-read-write-properties/Program.cs#3)]
  
 <span data-ttu-id="f55b4-120">請注意，在屬性 `set` 方法中提供特殊的 `value` 變數。</span><span class="sxs-lookup"><span data-stu-id="f55b4-120">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="f55b4-121">此變數包含使用者指定的值，例如：</span><span class="sxs-lookup"><span data-stu-id="f55b4-121">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[properties#4](snippets/how-to-declare-and-use-read-write-properties/Program.cs#4)]
  
 <span data-ttu-id="f55b4-122">請注意在 `Person` 物件上遞增 `Age` 屬性的全新語法：</span><span class="sxs-lookup"><span data-stu-id="f55b4-122">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[properties#5](snippets/how-to-declare-and-use-read-write-properties/Program.cs#5)]
  
 <span data-ttu-id="f55b4-123">如果分別使用 `set` 和 `get` 方法建立了屬性模型，對等的程式碼可能看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="f55b4-123">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="f55b4-124">本例中覆寫 `ToString` 方法：</span><span class="sxs-lookup"><span data-stu-id="f55b4-124">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[properties#6](snippets/how-to-declare-and-use-read-write-properties/Program.cs#6)]
  
 <span data-ttu-id="f55b4-125">請注意，程式中未明確使用 `ToString`。</span><span class="sxs-lookup"><span data-stu-id="f55b4-125">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="f55b4-126">預設會由 `WriteLine` 呼叫叫用。</span><span class="sxs-lookup"><span data-stu-id="f55b4-126">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f55b4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f55b4-127">See also</span></span>

- [<span data-ttu-id="f55b4-128">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f55b4-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f55b4-129">屬性</span><span class="sxs-lookup"><span data-stu-id="f55b4-129">Properties</span></span>](./properties.md)
- [<span data-ttu-id="f55b4-130">類別和結構</span><span class="sxs-lookup"><span data-stu-id="f55b4-130">Classes and Structs</span></span>](./index.md)
