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
ms.openlocfilehash: 87cf793229cfc7d8d0547af935369a3febee41a3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290184"
---
# <a name="names-of-type-members"></a><span data-ttu-id="ef4bd-102">類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="ef4bd-102">Names of Type Members</span></span>
<span data-ttu-id="ef4bd-103">類型由成員組成：方法、屬性、事件、建構函式及欄位。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="ef4bd-104">下列各節會描述為類型成員命名的方針。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-104">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="ef4bd-105">方法的名稱</span><span class="sxs-lookup"><span data-stu-id="ef4bd-105">Names of Methods</span></span>
 <span data-ttu-id="ef4bd-106">因為方法是採取動作的手段，所以設計方針會要求方法名稱為動詞或動詞片語。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="ef4bd-107">遵循此方針也能用來區別方法名稱與屬性和類型名稱，後兩者為名詞或形容詞。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="ef4bd-108">✔️提供的方法名稱是動詞或動詞片語。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-108">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="ef4bd-109">屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="ef4bd-109">Names of Properties</span></span>
 <span data-ttu-id="ef4bd-110">不同於其他成員，屬性應有名詞片語或形容詞名稱。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="ef4bd-111">這是因為屬性會參考資料，而屬性的名稱則會反映這點。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="ef4bd-112">PascalCasing 總是會用作屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-112">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="ef4bd-113">✔️使用名詞、名詞片語或形容詞來命名屬性。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-113">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="ef4bd-114">❌沒有符合 "Get" 方法名稱的屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ef4bd-114">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="ef4bd-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="ef4bd-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="ef4bd-116">此模式通常表示屬性應該真的是方法。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-116">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="ef4bd-117">✔️使用複數片語來命名集合屬性，以描述集合中的專案，而不是使用後面接著 "List" 或 "Collection" 的單數片語。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-117">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="ef4bd-118">✔️使用肯定片語（ `CanSeek` 而不是）來命名布林屬性 `CantSeek` 。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-118">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="ef4bd-119">（選擇性）您也可以使用 "Is"、"Can" 或 "has" 作為布林值屬性的前置詞，但只有其加入值的位置。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-119">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="ef4bd-120">✔️考慮為屬性提供與其類型相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-120">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="ef4bd-121">例如，下列屬性正確地取得並設定了名為 `Color` 的數值，所以屬性名稱即為 `Color`：</span><span class="sxs-lookup"><span data-stu-id="ef4bd-121">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="ef4bd-122">事件的名稱</span><span class="sxs-lookup"><span data-stu-id="ef4bd-122">Names of Events</span></span>
 <span data-ttu-id="ef4bd-123">事件一律會參考某些動作，不論該動作正在發生或已發生。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-123">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="ef4bd-124">因此，如同方法一般，事件應以動詞為名，且應使用動詞時態來指出事件發生的時間。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-124">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="ef4bd-125">✔️使用動詞或動詞片語來命名事件。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-125">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="ef4bd-126">範例包括 `Clicked`、`Painting`、`DroppedDown` 等等。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-126">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="ef4bd-127">✔️確實使用目前和過去的時態，為事件名稱提供前後的概念。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-127">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="ef4bd-128">例如，在視窗關閉前發生的關閉事件會稱作 `Closing`，而在視窗關閉後發生的事件則稱作 `Closed`。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-128">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="ef4bd-129">❌請勿使用 "Before" 或 "After" 前置詞或 postfixes 來表示前置和後置事件。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-129">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="ef4bd-130">使用如同敘述的現在與過去時態。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-130">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="ef4bd-131">✔️使用 "EventHandler" 尾碼來命名事件處理常式（做為事件種類的委派），如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ef4bd-131">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="ef4bd-132">✔️確實會 `sender` `e` 在事件處理常式中使用名為和的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-132">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="ef4bd-133">傳送者參數代表引發事件的物件。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-133">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="ef4bd-134">傳送者參數的類型通常為 `object`，即使可採用更明確的類型時也一樣。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-134">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="ef4bd-135">✔️ DO 以 "EventArgs" 尾碼命名事件引數類別。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-135">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="ef4bd-136">欄位的名稱</span><span class="sxs-lookup"><span data-stu-id="ef4bd-136">Names of Fields</span></span>
 <span data-ttu-id="ef4bd-137">欄位命名方針適用於靜態公開和保護的欄位。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-137">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="ef4bd-138">方針並未涵蓋內部與私人的欄位，且[成員設計方針](member.md)並不允許公開或保護的執行個體欄位。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-138">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](member.md).</span></span>

 <span data-ttu-id="ef4bd-139">✔️請在功能變數名稱中使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-139">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="ef4bd-140">✔️使用名詞、名詞片語或形容詞來命名欄位。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-140">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="ef4bd-141">❌請不要使用功能變數名稱的前置詞。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-141">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="ef4bd-142">例如，不要使用 "g_" 或 "s_" 來表示靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="ef4bd-142">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="ef4bd-143">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="ef4bd-143">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ef4bd-144">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="ef4bd-144">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ef4bd-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef4bd-145">See also</span></span>

- [<span data-ttu-id="ef4bd-146">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="ef4bd-146">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ef4bd-147">命名方針</span><span class="sxs-lookup"><span data-stu-id="ef4bd-147">Naming Guidelines</span></span>](naming-guidelines.md)
