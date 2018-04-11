---
title: C# 屬性 - C# 語言教學課程
description: 了解在 C# 中使用屬性的宣告式程式設計
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 6878a408ef892ee47a03bfa04f736b9bf9671696
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="attributes"></a><span data-ttu-id="5536a-104">屬性</span><span class="sxs-lookup"><span data-stu-id="5536a-104">Attributes</span></span>

<span data-ttu-id="5536a-105">C# 程式中的型別、成員和其他實體支援控制其某方面行為的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="5536a-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="5536a-106">例如，方法的協助工具是使用 `public`、`protected`、`internal` 和 `private` 修飾詞控制。</span><span class="sxs-lookup"><span data-stu-id="5536a-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="5536a-107">C# 將此能力一般化，宣告式資訊的使用者定義型別才能附加至程式實體，並在執行階段擷取。</span><span class="sxs-lookup"><span data-stu-id="5536a-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="5536a-108">程式是透過定義和使用***屬性***指定這項額外的宣告式資訊。</span><span class="sxs-lookup"><span data-stu-id="5536a-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="5536a-109">下列範例宣告的 `HelpAttribute` 屬性可置於程式實體，以提供其相關文件的連結。</span><span class="sxs-lookup"><span data-stu-id="5536a-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="5536a-110">所有屬性類別均衍生自標準程式庫提供的 <xref:System.Attribute> 基底類別。</span><span class="sxs-lookup"><span data-stu-id="5536a-110">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="5536a-111">在相關聯的宣告之前，於方括弧中提供屬性的名稱 (及任何引數) 即可套用屬性。</span><span class="sxs-lookup"><span data-stu-id="5536a-111">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="5536a-112">如果屬性名稱的結尾是 `Attribute`，則參考該屬性時可以省略該部分名稱。</span><span class="sxs-lookup"><span data-stu-id="5536a-112">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="5536a-113">例如，`HelpAttribute` 屬性可以下列方式使用。</span><span class="sxs-lookup"><span data-stu-id="5536a-113">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="5536a-114">這個範例會將 `HelpAttribute` 附加至 `Widget` 類別。</span><span class="sxs-lookup"><span data-stu-id="5536a-114">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="5536a-115">它會在類別的 `Display` 方法中加入另一個 `HelpAttribute`。</span><span class="sxs-lookup"><span data-stu-id="5536a-115">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="5536a-116">屬性類別的公用建構函式控制將屬性附加至程式實體時必須提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="5536a-116">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="5536a-117">透過參考屬性類別的公用讀寫屬性可提供其他資訊 (例如先前對 `Topic` 的參考 )。</span><span class="sxs-lookup"><span data-stu-id="5536a-117">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="5536a-118">透過反射要求特定的屬性時，會以程式來源中提供的資訊叫用屬性類別的建構函式，並傳回產生的屬性執行個體。</span><span class="sxs-lookup"><span data-stu-id="5536a-118">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="5536a-119">如果是透過屬性提供其他資訊，傳回屬性執行個體之前，這些屬性會設為指定的值。</span><span class="sxs-lookup"><span data-stu-id="5536a-119">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="5536a-120">上一步</span><span class="sxs-lookup"><span data-stu-id="5536a-120">Previous</span></span>](delegates.md)
