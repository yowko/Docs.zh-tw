---
title: C# 屬性 - C# 語言教學課程
description: 了解在 C# 中使用屬性的宣告式程式設計
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 671023f268ae78d63db8868ef6046b8f13880659
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "34312231"
---
# <a name="attributes"></a><span data-ttu-id="6d73f-103">屬性</span><span class="sxs-lookup"><span data-stu-id="6d73f-103">Attributes</span></span>

<span data-ttu-id="6d73f-104">C# 程式中的型別、成員和其他實體支援控制其某方面行為的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="6d73f-104">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="6d73f-105">例如，方法的協助工具是使用 `public`、`protected`、`internal` 和 `private` 修飾詞控制。</span><span class="sxs-lookup"><span data-stu-id="6d73f-105">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="6d73f-106">C# 將此能力一般化，宣告式資訊的使用者定義型別才能附加至程式實體，並在執行階段擷取。</span><span class="sxs-lookup"><span data-stu-id="6d73f-106">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="6d73f-107">程式是透過定義和使用***屬性***指定這項額外的宣告式資訊。</span><span class="sxs-lookup"><span data-stu-id="6d73f-107">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="6d73f-108">下列範例宣告的 `HelpAttribute` 屬性可置於程式實體，以提供其相關文件的連結。</span><span class="sxs-lookup"><span data-stu-id="6d73f-108">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="6d73f-109">所有屬性類別均衍生自標準程式庫提供的 <xref:System.Attribute> 基底類別。</span><span class="sxs-lookup"><span data-stu-id="6d73f-109">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="6d73f-110">在相關聯的宣告之前，於方括弧中提供屬性的名稱 (及任何引數) 即可套用屬性。</span><span class="sxs-lookup"><span data-stu-id="6d73f-110">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="6d73f-111">如果屬性名稱的結尾是 `Attribute`，則參考該屬性時可以省略該部分名稱。</span><span class="sxs-lookup"><span data-stu-id="6d73f-111">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="6d73f-112">例如，`HelpAttribute` 可以下列方式使用。</span><span class="sxs-lookup"><span data-stu-id="6d73f-112">For example, the `HelpAttribute` can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="6d73f-113">這個範例會將 `HelpAttribute` 附加至 `Widget` 類別。</span><span class="sxs-lookup"><span data-stu-id="6d73f-113">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="6d73f-114">它會在類別的 `Display` 方法中加入另一個 `HelpAttribute`。</span><span class="sxs-lookup"><span data-stu-id="6d73f-114">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="6d73f-115">屬性類別的公用建構函式控制將屬性附加至程式實體時必須提供的資訊。</span><span class="sxs-lookup"><span data-stu-id="6d73f-115">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="6d73f-116">透過參考屬性類別的公用讀寫屬性可提供其他資訊 (例如先前對 `Topic` 的參考 )。</span><span class="sxs-lookup"><span data-stu-id="6d73f-116">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="6d73f-117">由屬性定義的中繼資料可在執行階段使用反射來讀取及操控。</span><span class="sxs-lookup"><span data-stu-id="6d73f-117">The metadata defined by attributes can be read and manipulated at runtime using reflection.</span></span> <span data-ttu-id="6d73f-118">使用此技巧要求特定的屬性時，會以程式來源中提供的資訊叫用屬性類別的建構函式，並傳回產生的屬性執行個體。</span><span class="sxs-lookup"><span data-stu-id="6d73f-118">When a particular attribute is requested using this technique, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="6d73f-119">如果是透過屬性提供其他資訊，傳回屬性執行個體之前，這些屬性會設為指定的值。</span><span class="sxs-lookup"><span data-stu-id="6d73f-119">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

<span data-ttu-id="6d73f-120">下列程式碼範例示範如何取得與 `Widget` 類別關聯的 `HelpAttribute` 執行個體與其 `Display` 方法。</span><span class="sxs-lookup"><span data-stu-id="6d73f-120">The following code sample demonstrates how to get the `HelpAttribute` instances associated to the `Widget` class and its `Display` method.</span></span>

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
[<span data-ttu-id="6d73f-121">上一步</span><span class="sxs-lookup"><span data-stu-id="6d73f-121">Previous</span></span>](delegates.md)
