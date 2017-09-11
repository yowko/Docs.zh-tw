---
title: "sealed (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a8d0fe959eac03aad4f1ae1fada61c0ad2fd65cd
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="sealed-c-reference"></a><span data-ttu-id="87811-102">sealed (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="87811-102">sealed (C# Reference)</span></span>
<span data-ttu-id="87811-103">套用至類別時，`sealed` 修飾詞可防止其他類別繼承自它。</span><span class="sxs-lookup"><span data-stu-id="87811-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="87811-104">在下列範例中，`B` 類別繼承自 `A`類別，但類別無法繼承自 `B` 類別。</span><span class="sxs-lookup"><span data-stu-id="87811-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 <span data-ttu-id="87811-105">您也可以在方法或屬性上使用可覆寫基底類別中虛擬方法或屬性的 `sealed` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="87811-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="87811-106">這可讓您允許類別衍生自您的類別，並防止它們覆寫特定虛擬方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="87811-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87811-107">範例</span><span class="sxs-lookup"><span data-stu-id="87811-107">Example</span></span>  
 <span data-ttu-id="87811-108">在下列範例中，`Z` 繼承自 `Y`，但 `Z` 無法覆寫宣告於 `X` 並密封於 `Y` 的虛擬函式 `F`。</span><span class="sxs-lookup"><span data-stu-id="87811-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>  
  
 <span data-ttu-id="87811-109">[!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="87811-109">[!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]</span></span>  
  
 <span data-ttu-id="87811-110">當您在類別中定義新方法或屬性時，可以不將這些方法或屬性宣告為 [virtual](../../../csharp/language-reference/keywords/virtual.md)，以防止衍生類別覆寫它們。</span><span class="sxs-lookup"><span data-stu-id="87811-110">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
 <span data-ttu-id="87811-111">搭配使用 [abstract](../../../csharp/language-reference/keywords/abstract.md) 修飾詞與 sealed 類別會產生錯誤，因為提供 abstract 方法或屬性實作的類別必須繼承 abstract 類別。</span><span class="sxs-lookup"><span data-stu-id="87811-111">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>  
  
 <span data-ttu-id="87811-112">套用至方法或屬性時，`sealed` 修飾詞必須一律與 [override](../../../csharp/language-reference/keywords/override.md) 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="87811-112">When applied to a method or property, the `sealed` modifier must always be used with [override](../../../csharp/language-reference/keywords/override.md).</span></span>  
  
 <span data-ttu-id="87811-113">結構會隱含地進行密封，因此無法進行繼承。</span><span class="sxs-lookup"><span data-stu-id="87811-113">Because structs are implicitly sealed, they cannot be inherited.</span></span>  
  
 <span data-ttu-id="87811-114">如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="87811-114">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span>  
  
 <span data-ttu-id="87811-115">如需更多範例，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="87811-115">For more examples, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87811-116">範例</span><span class="sxs-lookup"><span data-stu-id="87811-116">Example</span></span>  
 <span data-ttu-id="87811-117">[!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="87811-117">[!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]</span></span>  
  
 <span data-ttu-id="87811-118">在上述範例中，您可以嘗試使用下列陳述式從 sealed 類別繼承︰</span><span class="sxs-lookup"><span data-stu-id="87811-118">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 <span data-ttu-id="87811-119">結果是錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="87811-119">The result is an error message:</span></span>  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="87811-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="87811-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="87811-121">備註</span><span class="sxs-lookup"><span data-stu-id="87811-121">Remarks</span></span>  
 <span data-ttu-id="87811-122">若要判斷是否密封類別、方法或屬性，您通常應該考慮下列兩點︰</span><span class="sxs-lookup"><span data-stu-id="87811-122">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>  
  
-   <span data-ttu-id="87811-123">衍生類別的潛在優點可能是透過類別自訂功能所取得。</span><span class="sxs-lookup"><span data-stu-id="87811-123">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>  
  
-   <span data-ttu-id="87811-124">衍生類別可能會修改您的類別，因此它們無法再正確運作或如預期運作。</span><span class="sxs-lookup"><span data-stu-id="87811-124">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87811-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87811-125">See Also</span></span>  
 <span data-ttu-id="87811-126">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="87811-126">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="87811-127">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="87811-127">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="87811-128">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="87811-128">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="87811-129">[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="87811-129">[Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) </span></span>  
 <span data-ttu-id="87811-130">[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span><span class="sxs-lookup"><span data-stu-id="87811-130">[Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md) </span></span>  
 <span data-ttu-id="87811-131">[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="87811-131">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 <span data-ttu-id="87811-132">[修飾詞](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="87811-132">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="87811-133">[override](../../../csharp/language-reference/keywords/override.md) </span><span class="sxs-lookup"><span data-stu-id="87811-133">[override](../../../csharp/language-reference/keywords/override.md) </span></span>  
 [<span data-ttu-id="87811-134">virtual</span><span class="sxs-lookup"><span data-stu-id="87811-134">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)

