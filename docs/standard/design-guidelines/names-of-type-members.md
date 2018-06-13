---
title: 類型成員名稱
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25fe93b63c518f54ee72300f26dfcb3f3ad21d76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575345"
---
# <a name="names-of-type-members"></a><span data-ttu-id="42c1f-102">類型成員名稱</span><span class="sxs-lookup"><span data-stu-id="42c1f-102">Names of Type Members</span></span>
<span data-ttu-id="42c1f-103">類型由成員： 方法、 屬性、 事件、 建構函式和欄位。</span><span class="sxs-lookup"><span data-stu-id="42c1f-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="42c1f-104">下列章節說明的指導方針命名型別成員。</span><span class="sxs-lookup"><span data-stu-id="42c1f-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="42c1f-105">方法的名稱</span><span class="sxs-lookup"><span data-stu-id="42c1f-105">Names of Methods</span></span>  
 <span data-ttu-id="42c1f-106">因為方法都是採取之動作的方式，設計指導方針會需要方法名稱是動詞或動詞片語。</span><span class="sxs-lookup"><span data-stu-id="42c1f-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="42c1f-107">遵循這個指導方針也是用來區別屬性和型別名稱，也就是名詞或形容詞片語中的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="42c1f-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="42c1f-108">**✓ 不要**提供動詞或動詞片語的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="42c1f-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="42c1f-109">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="42c1f-109">Names of Properties</span></span>  
 <span data-ttu-id="42c1f-110">不同於其他成員屬性應該指定名詞片語或形容詞的名稱。</span><span class="sxs-lookup"><span data-stu-id="42c1f-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="42c1f-111">這是因為屬性參考到資料，以及屬性的名稱會反映。</span><span class="sxs-lookup"><span data-stu-id="42c1f-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="42c1f-112">PascalCasing 永遠用於屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="42c1f-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="42c1f-113">**✓ 不要**命名屬性使用名詞、 名詞片語或形容詞。</span><span class="sxs-lookup"><span data-stu-id="42c1f-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="42c1f-114">**X 不**沒有符合的名稱 「 取得 」 方法，如下列範例所示的屬性：</span><span class="sxs-lookup"><span data-stu-id="42c1f-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="42c1f-115">此模式通常表示，屬性實際上應該是一種方法。</span><span class="sxs-lookup"><span data-stu-id="42c1f-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="42c1f-116">**✓ 不要**集合屬性名稱複數片語，描述的項目中的集合，而不是使用單數片語，後面接著 「 清單 」 或 「 集合 」。</span><span class="sxs-lookup"><span data-stu-id="42c1f-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="42c1f-117">**✓ 不要**命名肯定片語的布林值屬性 (`CanSeek`而不是`CantSeek`)。</span><span class="sxs-lookup"><span data-stu-id="42c1f-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="42c1f-118">（選擇性） 您也可以前面布林值屬性與 「 是 」，「 可以 」 或 「 沒有，」 但只在它將值。</span><span class="sxs-lookup"><span data-stu-id="42c1f-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="42c1f-119">**✓ 考慮**為屬性提供其型別相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="42c1f-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="42c1f-120">例如，下列屬性正確取得並設定列舉值，名稱為`Color`，所以此屬性名為`Color`:</span><span class="sxs-lookup"><span data-stu-id="42c1f-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="42c1f-121">事件的名稱</span><span class="sxs-lookup"><span data-stu-id="42c1f-121">Names of Events</span></span>  
 <span data-ttu-id="42c1f-122">某些動作，其中一個已發生或發生的其中一個會參考事件。</span><span class="sxs-lookup"><span data-stu-id="42c1f-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="42c1f-123">因此，如同方法，事件會以動詞命令，來命名，而且動詞時態用來指示當引發事件的時間。</span><span class="sxs-lookup"><span data-stu-id="42c1f-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="42c1f-124">**✓ 不要**名稱具有動詞或動詞片語的事件。</span><span class="sxs-lookup"><span data-stu-id="42c1f-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="42c1f-125">範例包括`Clicked`， `Painting`， `DroppedDown`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="42c1f-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="42c1f-126">**✓ 不要**提供事件名稱的概念與之前和之後，使用目前和過去時態。</span><span class="sxs-lookup"><span data-stu-id="42c1f-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="42c1f-127">例如，呼叫視窗關閉之前引發的關閉事件`Closing`，而且會呼叫一個視窗關閉後，就會引發`Closed`。</span><span class="sxs-lookup"><span data-stu-id="42c1f-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="42c1f-128">**X 不**使用 「 之前 」 或 「 之後 」 前置詞或 postfixes 表示前置和後置事件。</span><span class="sxs-lookup"><span data-stu-id="42c1f-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="42c1f-129">使用存在，以及過去時態，如上所述。</span><span class="sxs-lookup"><span data-stu-id="42c1f-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="42c1f-130">**✓ 不要**命名 」 事件處理常式 」 的後置詞，事件處理常式 （委派做為事件的類型），如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="42c1f-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="42c1f-131">**✓ 不要**使用名為兩個參數`sender`和`e`事件處理常式中。</span><span class="sxs-lookup"><span data-stu-id="42c1f-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="42c1f-132">傳送者參數代表引發事件的物件。</span><span class="sxs-lookup"><span data-stu-id="42c1f-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="42c1f-133">傳送者參數的型別通常是`object`，即使可以採用更特定的類型。</span><span class="sxs-lookup"><span data-stu-id="42c1f-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="42c1f-134">**✓ 不要**命名事件引數"EventArgs"後置詞的類別。</span><span class="sxs-lookup"><span data-stu-id="42c1f-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="42c1f-135">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="42c1f-135">Names of Fields</span></span>  
 <span data-ttu-id="42c1f-136">欄位命名指導方針適用於靜態公用和受保護的欄位。</span><span class="sxs-lookup"><span data-stu-id="42c1f-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="42c1f-137">內部及私人欄位未涵蓋的指導方針，而且公用或受保護的執行個體欄位不允許由[成員設計指導方針](../../../docs/standard/design-guidelines/member.md)。</span><span class="sxs-lookup"><span data-stu-id="42c1f-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="42c1f-138">**✓ 不要**PascalCasing 用於欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="42c1f-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="42c1f-139">**✓ 不要**命名欄位使用名詞、 名詞片語或形容詞。</span><span class="sxs-lookup"><span data-stu-id="42c1f-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="42c1f-140">**X 不**使用欄位名稱的前置詞。</span><span class="sxs-lookup"><span data-stu-id="42c1f-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="42c1f-141">例如，請勿"g_"或"s_"，表示的靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="42c1f-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="42c1f-142">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="42c1f-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="42c1f-143">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="42c1f-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c1f-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42c1f-144">See Also</span></span>  
 [<span data-ttu-id="42c1f-145">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="42c1f-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="42c1f-146">命名方針</span><span class="sxs-lookup"><span data-stu-id="42c1f-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
