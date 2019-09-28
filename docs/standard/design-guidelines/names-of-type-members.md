---
title: 類型成員名稱
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: KrzysztofCwalina
ms.openlocfilehash: b4da14575d29582814d32a3050087b7acc0da802
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353719"
---
# <a name="names-of-type-members"></a><span data-ttu-id="dbf6c-102">類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="dbf6c-102">Names of Type Members</span></span>
<span data-ttu-id="dbf6c-103">類型由成員組成：方法、屬性、事件、建構函式及欄位。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="dbf6c-104">下列各節會描述為類型成員命名的方針。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="dbf6c-105">方法的名稱</span><span class="sxs-lookup"><span data-stu-id="dbf6c-105">Names of Methods</span></span>  
 <span data-ttu-id="dbf6c-106">因為方法是採取動作的手段，所以設計方針會要求方法名稱為動詞或動詞片語。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="dbf6c-107">遵循此方針也能用來區別方法名稱與屬性和類型名稱，後兩者為名詞或形容詞。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="dbf6c-108">**✓ DO**提供是動詞或動詞片語的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="dbf6c-109">屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="dbf6c-109">Names of Properties</span></span>  
 <span data-ttu-id="dbf6c-110">不同於其他成員，屬性應有名詞片語或形容詞名稱。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="dbf6c-111">這是因為屬性會參考資料，而屬性的名稱則會反映這點。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="dbf6c-112">PascalCasing 總是會用作屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="dbf6c-113">**✓ DO**使用名詞、名詞片語或形容詞來命名屬性。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="dbf6c-114">**X DO NOT**使屬性符合 "Get" 方法的名稱，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="dbf6c-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="dbf6c-115">此模式通常表示屬性應該真的是方法。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="dbf6c-116">**✓ DO**以單數片語命名集合屬性，描述集合中的項目而非使用後面接著 "List" 或 "Collection" 的單數片語。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="dbf6c-117">**✓ DO**以肯定片語 (`CanSeek` 而非 `CantSeek`) 命名布林值屬性。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="dbf6c-118">此外，您也可以使用 "Is,"、"Can," 或 "Has," 作為布林值屬性的首碼，但僅限於新增值的情況。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="dbf6c-119">**✓ CONSIDER**為屬性提供與其類型相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="dbf6c-120">例如，下列屬性正確地取得並設定了名為 `Color` 的數值，所以屬性名稱即為 `Color`：</span><span class="sxs-lookup"><span data-stu-id="dbf6c-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="dbf6c-121">事件的名稱</span><span class="sxs-lookup"><span data-stu-id="dbf6c-121">Names of Events</span></span>  
 <span data-ttu-id="dbf6c-122">事件一律會參考某些動作，不論該動作正在發生或已發生。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="dbf6c-123">因此，如同方法一般，事件應以動詞為名，且應使用動詞時態來指出事件發生的時間。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="dbf6c-124">**✓ DO**以動詞或動詞片語命名事件。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="dbf6c-125">範例包括 `Clicked`、`Painting`、`DroppedDown` 等等。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="dbf6c-126">**✓ DO**使用現在和過去式，來為事件賦予具有現在和之後概念的名稱。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="dbf6c-127">例如，在視窗關閉前發生的關閉事件會稱作 `Closing`，而在視窗關閉後發生的事件則稱作 `Closed`。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="dbf6c-128">**X DO NOT**使用 "Before" 或 "After" 首碼與尾碼來表示之前和之後的事件。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="dbf6c-129">使用如同敘述的現在與過去時態。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="dbf6c-130">**✓ DO**以 "EventHandler" 尾碼來命名事件處理常式 (用作事件類型的委派)，如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="dbf6c-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="dbf6c-131">**✓ DO**在事件處理常式中使用名為 `sender` 和 `e` 的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="dbf6c-132">傳送者參數代表引發事件的物件。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="dbf6c-133">傳送者參數的類型通常為 `object`，即使可採用更明確的類型時也一樣。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="dbf6c-134">**✓ DO**以 "EventArgs" 尾碼命名事件引數類別。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="dbf6c-135">欄位的名稱</span><span class="sxs-lookup"><span data-stu-id="dbf6c-135">Names of Fields</span></span>  
 <span data-ttu-id="dbf6c-136">欄位命名方針適用於靜態公開和保護的欄位。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="dbf6c-137">方針並未涵蓋內部與私人的欄位，且[成員設計方針](../../../docs/standard/design-guidelines/member.md)並不允許公開或保護的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="dbf6c-138">**✓ DO**在欄位名稱中使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="dbf6c-139">**✓ DO** 使用名詞、名詞片語或形容詞來命名欄位。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="dbf6c-140">**X DO NOT**為欄位名稱使用首碼。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="dbf6c-141">例如，不要使用 "g_" 或 "s_" 來表示靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="dbf6c-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="dbf6c-142">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="dbf6c-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="dbf6c-143">從 @no__t 1Framework 設計指導方針中，@no__t 0Reprinted by 皮耳森教育，Inc. 的許可權：可重複使用的 .NET 程式庫、第2版 @ no__t-0 by Krzysztof Cwalina 和 Brad Abrams 的慣例、慣用語和模式，已于2008年10月22日發行，其為 Microsoft Windows 開發系列的一部分 Addison-Wesley Professional。 \*</span><span class="sxs-lookup"><span data-stu-id="dbf6c-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf6c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbf6c-144">See also</span></span>

- [<span data-ttu-id="dbf6c-145">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="dbf6c-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="dbf6c-146">命名方針</span><span class="sxs-lookup"><span data-stu-id="dbf6c-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
