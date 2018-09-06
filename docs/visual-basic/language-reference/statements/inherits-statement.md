---
title: Inherits 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: 4a98ada39a04730b46f40fe139e72d1855d9b067
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739499"
---
# <a name="inherits-statement"></a><span data-ttu-id="3a98a-102">Inherits 陳述式</span><span class="sxs-lookup"><span data-stu-id="3a98a-102">Inherits Statement</span></span>
<span data-ttu-id="3a98a-103">會導致目前的類別或介面從另一個類別或介面集合繼承屬性、 變數、 屬性、 程序和事件。</span><span class="sxs-lookup"><span data-stu-id="3a98a-103">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a98a-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a98a-104">Syntax</span></span>  
  
```  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="3a98a-105">組件</span><span class="sxs-lookup"><span data-stu-id="3a98a-105">Parts</span></span>  
  
|<span data-ttu-id="3a98a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="3a98a-106">Term</span></span>|<span data-ttu-id="3a98a-107">定義</span><span class="sxs-lookup"><span data-stu-id="3a98a-107">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="3a98a-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="3a98a-108">Required.</span></span> <span data-ttu-id="3a98a-109">從這個類別衍生的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="3a98a-109">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="3a98a-110">-或-</span><span class="sxs-lookup"><span data-stu-id="3a98a-110">-or-</span></span><br /><br /> <span data-ttu-id="3a98a-111">從這個介面衍生的介面名稱。</span><span class="sxs-lookup"><span data-stu-id="3a98a-111">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="3a98a-112">使用逗號來分隔多個名稱。</span><span class="sxs-lookup"><span data-stu-id="3a98a-112">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a98a-113">備註</span><span class="sxs-lookup"><span data-stu-id="3a98a-113">Remarks</span></span>  
 <span data-ttu-id="3a98a-114">如果使用，`Inherits`陳述式必須是類別或介面定義中的第一個非空白的非註解一行。</span><span class="sxs-lookup"><span data-stu-id="3a98a-114">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="3a98a-115">它應該緊接`Class`或`Interface`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3a98a-115">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="3a98a-116">您可以使用`Inherits`只能在類別或介面中。</span><span class="sxs-lookup"><span data-stu-id="3a98a-116">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="3a98a-117">這表示原始程式檔、 命名空間、 結構、 模組、 程序或區塊，不能繼承的宣告內容。</span><span class="sxs-lookup"><span data-stu-id="3a98a-117">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3a98a-118">規則</span><span class="sxs-lookup"><span data-stu-id="3a98a-118">Rules</span></span>  
  
-   <span data-ttu-id="3a98a-119">**類別繼承。**</span><span class="sxs-lookup"><span data-stu-id="3a98a-119">**Class Inheritance.**</span></span> <span data-ttu-id="3a98a-120">如果類別會使用`Inherits`陳述式中，您可以指定只有一個基底類別。</span><span class="sxs-lookup"><span data-stu-id="3a98a-120">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="3a98a-121">類別無法繼承自巢狀類別。</span><span class="sxs-lookup"><span data-stu-id="3a98a-121">A class cannot inherit from a class nested within it.</span></span>  
  
-   <span data-ttu-id="3a98a-122">**介面繼承。**</span><span class="sxs-lookup"><span data-stu-id="3a98a-122">**Interface Inheritance.**</span></span> <span data-ttu-id="3a98a-123">如果介面使用`Inherits`陳述式中，您可以指定一或多個基底介面。</span><span class="sxs-lookup"><span data-stu-id="3a98a-123">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="3a98a-124">您可以繼承自兩個介面，即使它們都各自定義具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="3a98a-124">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="3a98a-125">如果您這樣做時，實作程式碼必須使用名稱限定性條件來指定它所實作的成員。</span><span class="sxs-lookup"><span data-stu-id="3a98a-125">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="3a98a-126">介面無法繼承自另一個介面具有更嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="3a98a-126">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="3a98a-127">例如，`Public`介面無法繼承自`Friend`介面。</span><span class="sxs-lookup"><span data-stu-id="3a98a-127">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="3a98a-128">介面無法繼承自的巢狀介面。</span><span class="sxs-lookup"><span data-stu-id="3a98a-128">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="3a98a-129">舉例來說，.NET Framework 中的類別繼承<xref:System.ArgumentException>類別，繼承自<xref:System.SystemException>類別。</span><span class="sxs-lookup"><span data-stu-id="3a98a-129">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="3a98a-130">這提供<xref:System.ArgumentException>所有預先定義的屬性和程序所需的系統例外狀況，例如<xref:System.Exception.Message%2A>屬性和<xref:System.Exception.ToString%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3a98a-130">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="3a98a-131">舉例來說，.NET Framework 中的介面繼承<xref:System.Collections.ICollection>介面，繼承自<xref:System.Collections.IEnumerable>介面。</span><span class="sxs-lookup"><span data-stu-id="3a98a-131">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="3a98a-132">這會導致<xref:System.Collections.ICollection>繼承需要周遊集合的列舉值的定義。</span><span class="sxs-lookup"><span data-stu-id="3a98a-132">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a98a-133">範例</span><span class="sxs-lookup"><span data-stu-id="3a98a-133">Example</span></span>  
 <span data-ttu-id="3a98a-134">下列範例會使用`Inherits`陳述式來顯示類別的命名方式`thisClass`可以繼承的基底類別，名為的所有成員`anotherClass`。</span><span class="sxs-lookup"><span data-stu-id="3a98a-134">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="3a98a-135">範例</span><span class="sxs-lookup"><span data-stu-id="3a98a-135">Example</span></span>  
 <span data-ttu-id="3a98a-136">下列範例顯示多個介面的繼承。</span><span class="sxs-lookup"><span data-stu-id="3a98a-136">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/inherits-statement_2.vb)]  
  
 <span data-ttu-id="3a98a-137">名為介面`thisInterface`現在包含中的所有定義<xref:System.IComparable>， <xref:System.IDisposable>，和<xref:System.IFormattable>介面繼承的成員分別提供針對特定類型的比較的兩個物件，釋放配置的資源表示為物件的值和`String`。</span><span class="sxs-lookup"><span data-stu-id="3a98a-137">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="3a98a-138">類別若實作`thisInterface`必須實作每個基底介面的每個成員。</span><span class="sxs-lookup"><span data-stu-id="3a98a-138">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a98a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a98a-139">See Also</span></span>  
 [<span data-ttu-id="3a98a-140">MustInherit</span><span class="sxs-lookup"><span data-stu-id="3a98a-140">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="3a98a-141">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="3a98a-141">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="3a98a-142">物件和類別</span><span class="sxs-lookup"><span data-stu-id="3a98a-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="3a98a-143">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="3a98a-143">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="3a98a-144">介面</span><span class="sxs-lookup"><span data-stu-id="3a98a-144">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
