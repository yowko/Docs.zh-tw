---
title: "在 Visual Basic (Visual Basic) 中的泛型型別 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- generic interfaces
- data type arguments, defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword, using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures, generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes, Visual Basic
- parameters, type
- type arguments
- interfaces, generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters, generic
- generic structures
- generic classes
- type parameters
- data type arguments
- structures, generic
- parameters, data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
caps.latest.revision: 45
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 40b175655b2b2341fd15e763058a3dae1291f2c4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="generic-types-in-visual-basic-visual-basic"></a><span data-ttu-id="a0a96-102">Visual Basic 中的泛型類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a96-102">Generic Types in Visual Basic (Visual Basic)</span></span>
<span data-ttu-id="a0a96-103">*「泛型類型」* (generic type) 是單一程式設計項目，適用於為各種資料類型執行相同的功能。</span><span class="sxs-lookup"><span data-stu-id="a0a96-103">A *generic type* is a single programming element that adapts to perform the same functionality for a variety of data types.</span></span> <span data-ttu-id="a0a96-104">當您定義泛型類別或程序時，不需要為想要執行該功能的每種資料類型定義不同的版本。</span><span class="sxs-lookup"><span data-stu-id="a0a96-104">When you define a generic class or procedure, you do not have to define a separate version for each data type for which you might want to perform that functionality.</span></span>  
  
 <span data-ttu-id="a0a96-105">類似的項目是頭部可拆卸的螺絲起子組。</span><span class="sxs-lookup"><span data-stu-id="a0a96-105">An analogy is a screwdriver set with removable heads.</span></span> <span data-ttu-id="a0a96-106">您可以檢查需要轉動的螺絲，並選取該螺絲的正確螺絲起子頭 (一字、十字、星形)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-106">You inspect the screw you need to turn and select the correct head for that screw (slotted, crossed, starred).</span></span> <span data-ttu-id="a0a96-107">將正確的螺絲起子頭插入螺絲起子握把之後，即可執行與螺絲起子完全相同的功能，即轉動螺絲。</span><span class="sxs-lookup"><span data-stu-id="a0a96-107">Once you insert the correct head in the screwdriver handle, you perform the exact same function with the screwdriver, namely turning the screw.</span></span>  
  
 <span data-ttu-id="a0a96-108">![泛用的工具組的螺絲起子的圖表](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")</span><span class="sxs-lookup"><span data-stu-id="a0a96-108">![Diagram of a screwdriver set as a generic tool](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")</span></span>  
<span data-ttu-id="a0a96-109">一組泛用螺絲起子工具組</span><span class="sxs-lookup"><span data-stu-id="a0a96-109">Screwdriver set as a generic tool</span></span>  
  
 <span data-ttu-id="a0a96-110">當您定義泛型類型時，即使用一個或多個資料類型對其進行參數化。</span><span class="sxs-lookup"><span data-stu-id="a0a96-110">When you define a generic type, you parameterize it with one or more data types.</span></span> <span data-ttu-id="a0a96-111">這可讓您使用程式碼來調整資料類型，使其符合需求。</span><span class="sxs-lookup"><span data-stu-id="a0a96-111">This allows the using code to tailor the data types to its requirements.</span></span> <span data-ttu-id="a0a96-112">您的程式碼可以宣告泛型項目的數個不同程式設計項目，而且各代表一組不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-112">Your code can declare several different programming elements from the generic element, each one acting on a different set of data types.</span></span> <span data-ttu-id="a0a96-113">但是，宣告的項目不論使用何種資料類型，都會執行相同的邏輯。</span><span class="sxs-lookup"><span data-stu-id="a0a96-113">But the declared elements all perform the identical logic, no matter what data types they are using.</span></span>  
  
 <span data-ttu-id="a0a96-114">例如，您可能想要建立和使用佇列類別，而這些佇列類別作用於特定資料類型 (如 `String`)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-114">For example, you might want to create and use a queue class that operates on a specific data type such as `String`.</span></span> <span data-ttu-id="a0a96-115">您可以宣告此類別從<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>，如下列範例所示。</xref:System.Collections.Generic.Queue%601?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a0a96-115">You can declare such a class from <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>, as the following example shows.</span></span>  
  
 <span data-ttu-id="a0a96-116">[!code-vb[VbVbalrDataTypes #&1;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0a96-116">[!code-vb[VbVbalrDataTypes#1](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]</span></span>  
  
 <span data-ttu-id="a0a96-117">您現在可以使用 `stringQ` ，以獨佔方式使用 `String` 值。</span><span class="sxs-lookup"><span data-stu-id="a0a96-117">You can now use `stringQ` to work exclusively with `String` values.</span></span> <span data-ttu-id="a0a96-118">因為 `stringQ` 是 `String` 特有的，而不是通用於 `Object` 值，所以您沒有晚期繫結或類型轉換。</span><span class="sxs-lookup"><span data-stu-id="a0a96-118">Because `stringQ` is specific for `String` instead of being generalized for `Object` values, you do not have late binding or type conversion.</span></span> <span data-ttu-id="a0a96-119">這可以節省執行時間，並減少執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="a0a96-119">This saves execution time and reduces run-time errors.</span></span>  
  
 <span data-ttu-id="a0a96-120">如需有關使用泛型類型的詳細資訊，請參閱[How to︰ 使用泛型類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-120">For more information on using a generic type, see [How to: Use a Generic Class](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md).</span></span>  
  
## <a name="example-of-a-generic-class"></a><span data-ttu-id="a0a96-121">泛型類別範例</span><span class="sxs-lookup"><span data-stu-id="a0a96-121">Example of a Generic Class</span></span>  
 <span data-ttu-id="a0a96-122">下列範例顯示泛型類別的基本架構定義。</span><span class="sxs-lookup"><span data-stu-id="a0a96-122">The following example shows a skeleton definition of a generic class.</span></span>  
  
 <span data-ttu-id="a0a96-123">[!code-vb[VbVbalrDataTypes #&2;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0a96-123">[!code-vb[VbVbalrDataTypes#2](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]</span></span>  
  
 <span data-ttu-id="a0a96-124">在上述的基本架構中， `t` 是 *「類型參數」*(type parameter)，即宣告類別時所提供資料類型的預留位置。</span><span class="sxs-lookup"><span data-stu-id="a0a96-124">In the preceding skeleton, `t` is a *type parameter*, that is, a placeholder for a data type that you supply when you declare the class.</span></span> <span data-ttu-id="a0a96-125">您可以在程式碼的其他位置，提供 `classHolder` 的各種資料類型來宣告各種版本的 `t`。</span><span class="sxs-lookup"><span data-stu-id="a0a96-125">Elsewhere in your code, you can declare various versions of `classHolder` by supplying various data types for `t`.</span></span> <span data-ttu-id="a0a96-126">下列範例顯示兩個這類宣告。</span><span class="sxs-lookup"><span data-stu-id="a0a96-126">The following example shows two such declarations.</span></span>  
  
 <span data-ttu-id="a0a96-127">[!code-vb[VbVbalrDataTypes #&3;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0a96-127">[!code-vb[VbVbalrDataTypes#3](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]</span></span>  
  
 <span data-ttu-id="a0a96-128">先前的陳述式宣告 *「已建構類別」*(constructed class)，其中，特定類型會取代類型參數。</span><span class="sxs-lookup"><span data-stu-id="a0a96-128">The preceding statements declare *constructed classes*, in which a specific type replaces the type parameter.</span></span> <span data-ttu-id="a0a96-129">這項取代遍及已建構類別內的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0a96-129">This replacement is propagated throughout the code within the constructed class.</span></span> <span data-ttu-id="a0a96-130">下列範例顯示 `processNewItem` 程序在 `integerClass`中的外觀。</span><span class="sxs-lookup"><span data-stu-id="a0a96-130">The following example shows what the `processNewItem` procedure looks like in `integerClass`.</span></span>  
  
 <span data-ttu-id="a0a96-131">[!code-vb[VbVbalrDataTypes #&4;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0a96-131">[!code-vb[VbVbalrDataTypes#4](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]</span></span>  
  
 <span data-ttu-id="a0a96-132">如需更完整範例，請參閱[How to︰ 在不同的資料型別上定義類別，可以提供相同功能](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-132">For a more complete example, see [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md).</span></span>  
  
## <a name="eligible-programming-elements"></a><span data-ttu-id="a0a96-133">合格的程式設計項目</span><span class="sxs-lookup"><span data-stu-id="a0a96-133">Eligible Programming Elements</span></span>  
 <span data-ttu-id="a0a96-134">您可以定義和使用泛型類別、結構、介面、程序和委派。</span><span class="sxs-lookup"><span data-stu-id="a0a96-134">You can define and use generic classes, structures, interfaces, procedures, and delegates.</span></span> <span data-ttu-id="a0a96-135">請注意，[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]定義數個泛型類別、 結構和介面，代表泛用常用的項目。</span><span class="sxs-lookup"><span data-stu-id="a0a96-135">Note that the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] defines several generic classes, structures, and interfaces that represent commonly used generic elements.</span></span> <span data-ttu-id="a0a96-136"><xref:System.Collections.Generic?displayProperty=fullName>命名空間提供的字典、 清單、 佇列和堆疊。</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a0a96-136">The <xref:System.Collections.Generic?displayProperty=fullName> namespace provides dictionaries, lists, queues, and stacks.</span></span> <span data-ttu-id="a0a96-137">在之前定義您自己的一般項目，請參閱其是否已在<xref:System.Collections.Generic?displayProperty=fullName>.</xref:System.Collections.Generic?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a0a96-137">Before defining your own generic element, see if it is already available in <xref:System.Collections.Generic?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="a0a96-138">程序不是類型，但您可以定義和使用泛型程序。</span><span class="sxs-lookup"><span data-stu-id="a0a96-138">Procedures are not types, but you can define and use generic procedures.</span></span> <span data-ttu-id="a0a96-139">請參閱[在 Visual Basic 中的泛型程序](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-139">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="advantages-of-generic-types"></a><span data-ttu-id="a0a96-140">泛型類型的優點</span><span class="sxs-lookup"><span data-stu-id="a0a96-140">Advantages of Generic Types</span></span>  
 <span data-ttu-id="a0a96-141">泛型類型是宣告數個不同程式設計項目的基礎，而這些項目各作用於特定資料類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-141">A generic type serves as a basis for declaring several different programming elements, each of which operates on a specific data type.</span></span> <span data-ttu-id="a0a96-142">泛型類型的替代項目是：</span><span class="sxs-lookup"><span data-stu-id="a0a96-142">The alternatives to a generic type are:</span></span>  
  
1.  <span data-ttu-id="a0a96-143">作用於 `Object` 資料類型的單一類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-143">A single type operating on the `Object` data type.</span></span>  
  
2.  <span data-ttu-id="a0a96-144">類型的一組 *「類型專用」* (type-specific) 版本，每個版本都會分別進行編碼，並作用於一種特定資料類型 (例如 `String`)、 `Integer`或使用者定義的類型 (例如 `customer`)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-144">A set of *type-specific* versions of the type, each version individually coded and operating on one specific data type such as `String`, `Integer`, or a user-defined type such as `customer`.</span></span>  
  
 <span data-ttu-id="a0a96-145">泛型類型優於這些替代項目的優點如下：</span><span class="sxs-lookup"><span data-stu-id="a0a96-145">A generic type has the following advantages over these alternatives:</span></span>  
  
-   <span data-ttu-id="a0a96-146">**型別安全。**</span><span class="sxs-lookup"><span data-stu-id="a0a96-146">**Type Safety.**</span></span> <span data-ttu-id="a0a96-147">泛型類型會強制執行編譯階段類型檢查。</span><span class="sxs-lookup"><span data-stu-id="a0a96-147">Generic types enforce compile-time type checking.</span></span> <span data-ttu-id="a0a96-148">以 `Object` 為基礎的類型會接受任何資料類型，而且您必須撰寫程式碼來檢查是否可以接受輸入資料類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-148">Types based on `Object` accept any data type, and you must write code to check whether an input data type is acceptable.</span></span> <span data-ttu-id="a0a96-149">使用泛型類型，編譯器可以在執行階段之前捕捉類型不符。</span><span class="sxs-lookup"><span data-stu-id="a0a96-149">With generic types, the compiler can catch type mismatches before run time.</span></span>  
  
-   <span data-ttu-id="a0a96-150">**效能。**</span><span class="sxs-lookup"><span data-stu-id="a0a96-150">**Performance.**</span></span> <span data-ttu-id="a0a96-151">泛型類型不需要 *Box* 和 *unBox* 資料，因為每種泛型類型都是一種資料類型特有的。</span><span class="sxs-lookup"><span data-stu-id="a0a96-151">Generic types do not have to *box* and *unbox* data, because each one is specialized for one data type.</span></span> <span data-ttu-id="a0a96-152">以 `Object` 為基礎的作業必須對輸入資料類型進行 Box 處理以將它們轉換成 `Object` ，並對要進行輸出的資料進行 Unbox 處理。</span><span class="sxs-lookup"><span data-stu-id="a0a96-152">Operations based on `Object` must box input data types to convert them to `Object` and unbox data destined for output.</span></span> <span data-ttu-id="a0a96-153">Box 和 Unbox 處理會降低效能。</span><span class="sxs-lookup"><span data-stu-id="a0a96-153">Boxing and unboxing reduce performance.</span></span>  
  
     <span data-ttu-id="a0a96-154">以 `Object` 為基礎的類型也會進行晚期繫結，這表示在執行階段時存取其成員需要額外撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="a0a96-154">Types based on `Object` are also late-bound, which means that accessing their members requires extra code at run time.</span></span> <span data-ttu-id="a0a96-155">這也會降低效能。</span><span class="sxs-lookup"><span data-stu-id="a0a96-155">This also reduces performance.</span></span>  
  
-   <span data-ttu-id="a0a96-156">**程式碼合併。**</span><span class="sxs-lookup"><span data-stu-id="a0a96-156">**Code Consolidation.**</span></span> <span data-ttu-id="a0a96-157">泛型類型中的程式碼僅需要定義一次。</span><span class="sxs-lookup"><span data-stu-id="a0a96-157">The code in a generic type has to be defined only once.</span></span> <span data-ttu-id="a0a96-158">類型的一組類型專用版本必須在每個版本中複寫相同的程式碼，唯一的差異在於為該版本的特定資料類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-158">A set of type-specific versions of a type must replicate the same code in each version, with the only difference being the specific data type for that version.</span></span> <span data-ttu-id="a0a96-159">使用泛型類型，類型專用版本都是產生自原始泛型類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-159">With generic types, the type-specific versions are all generated from the original generic type.</span></span>  
  
-   <span data-ttu-id="a0a96-160">**重複使用程式碼。**</span><span class="sxs-lookup"><span data-stu-id="a0a96-160">**Code Reuse.**</span></span> <span data-ttu-id="a0a96-161">如果未依賴特定資料類型的程式碼是泛型，則可以與各種資料類型一起重複使用。</span><span class="sxs-lookup"><span data-stu-id="a0a96-161">Code that does not depend on a particular data type can be reused with various data types if it is generic.</span></span> <span data-ttu-id="a0a96-162">您甚至可以經常將它與您原先未預期的資料類型一起重複使用。</span><span class="sxs-lookup"><span data-stu-id="a0a96-162">You can often reuse it even with a data type that you did not originally predict.</span></span>  
  
-   <span data-ttu-id="a0a96-163">**IDE 支援。**</span><span class="sxs-lookup"><span data-stu-id="a0a96-163">**IDE Support.**</span></span> <span data-ttu-id="a0a96-164">當您使用從泛型類型宣告的已建構類型時，整合式開發環境 (IDE) 可在您開發程式碼時提供更多的支援。</span><span class="sxs-lookup"><span data-stu-id="a0a96-164">When you use a constructed type declared from a generic type, the integrated development environment (IDE) can give you more support while you are developing your code.</span></span> <span data-ttu-id="a0a96-165">例如，IntelliSense 可以顯示建構函式或方法引數的類型專用選項。</span><span class="sxs-lookup"><span data-stu-id="a0a96-165">For example, IntelliSense can show you the type-specific options for an argument to a constructor or method.</span></span>  
  
-   <span data-ttu-id="a0a96-166">**泛型演算法。**</span><span class="sxs-lookup"><span data-stu-id="a0a96-166">**Generic Algorithms.**</span></span> <span data-ttu-id="a0a96-167">與類型無關的抽象演算法適用於泛型類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-167">Abstract algorithms that are type-independent are good candidates for generic types.</span></span> <span data-ttu-id="a0a96-168">例如，泛型程序所使用的<xref:System.IComparable>介面可以用來實作<xref:System.IComparable>.</xref:System.IComparable>任何資料類型</xref:System.IComparable>的項目排序</span><span class="sxs-lookup"><span data-stu-id="a0a96-168">For example, a generic procedure that sorts items using the <xref:System.IComparable> interface can be used with any data type that implements <xref:System.IComparable>.</span></span>  
  
## <a name="constraints"></a><span data-ttu-id="a0a96-169">條件約束</span><span class="sxs-lookup"><span data-stu-id="a0a96-169">Constraints</span></span>  
 <span data-ttu-id="a0a96-170">雖然泛型類型定義中的程式碼應該盡可能與類型無關，但是您可能需要要求提供給泛型類型之任何資料類型的特定功能。</span><span class="sxs-lookup"><span data-stu-id="a0a96-170">Although the code in a generic type definition should be as type-independent as possible, you might need to require a certain capability of any data type supplied to your generic type.</span></span> <span data-ttu-id="a0a96-171">例如，如果您想要比較兩個項目進行排序，或定序，其資料型別必須實作<xref:System.IComparable>介面。</xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="a0a96-171">For example, if you want to compare two items for the purpose of sorting or collating, their data type must implement the <xref:System.IComparable> interface.</span></span> <span data-ttu-id="a0a96-172">您可以將 *「條件約束」* (constraint) 加入類型參數中，來強制執行這項需求。</span><span class="sxs-lookup"><span data-stu-id="a0a96-172">You can enforce this requirement by adding a *constraint* to the type parameter.</span></span>  
  
### <a name="example-of-a-constraint"></a><span data-ttu-id="a0a96-173">條件約束範例</span><span class="sxs-lookup"><span data-stu-id="a0a96-173">Example of a Constraint</span></span>  
 <span data-ttu-id="a0a96-174">下列範例示範具有需要實作<xref:System.IComparable>.</xref:System.IComparable>的型別引數的條件約束的類別的基本架構定義</span><span class="sxs-lookup"><span data-stu-id="a0a96-174">The following example shows a skeleton definition of a class with a constraint that requires the type argument to implement <xref:System.IComparable>.</span></span>  
  
 <span data-ttu-id="a0a96-175">[!code-vb[VbVbalrDataTypes #&5;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0a96-175">[!code-vb[VbVbalrDataTypes#5](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]</span></span>  
  
 <span data-ttu-id="a0a96-176">如果後續的程式碼嘗試建構自`itemManager`提供不會實作型別<xref:System.IComparable>，編譯器會發出信號發生錯誤。</xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="a0a96-176">If subsequent code attempts to construct a class from `itemManager` supplying a type that does not implement <xref:System.IComparable>, the compiler signals an error.</span></span>  
  
### <a name="types-of-constraints"></a><span data-ttu-id="a0a96-177">條件約束類型</span><span class="sxs-lookup"><span data-stu-id="a0a96-177">Types of Constraints</span></span>  
 <span data-ttu-id="a0a96-178">您的條件約束可以利用任意組合指定下列需求：</span><span class="sxs-lookup"><span data-stu-id="a0a96-178">Your constraint can specify the following requirements in any combination:</span></span>  
  
-   <span data-ttu-id="a0a96-179">類型引數必須實作一或多個介面</span><span class="sxs-lookup"><span data-stu-id="a0a96-179">The type argument must implement one or more interfaces</span></span>  
  
-   <span data-ttu-id="a0a96-180">類型引數最多只能是一個類別的類型，或繼承自一個類別</span><span class="sxs-lookup"><span data-stu-id="a0a96-180">The type argument must be of the type of, or inherit from, at most one class</span></span>  
  
-   <span data-ttu-id="a0a96-181">類型引數必須公開從中建立物件之程式碼可存取的無參數建構函式</span><span class="sxs-lookup"><span data-stu-id="a0a96-181">The type argument must expose a parameterless constructor accessible to the code that creates objects from it</span></span>  
  
-   <span data-ttu-id="a0a96-182">類型引數必須是 *「參考類型」*(reference type)，或必須是 *「實值類型」*(value type)</span><span class="sxs-lookup"><span data-stu-id="a0a96-182">The type argument must be a *reference type*, or it must be a *value type*</span></span>  
  
 <span data-ttu-id="a0a96-183">如果您需要多個需求，請在大括弧 ( *) 內使用逗號分隔的* 「條件約束清單」`{ }`(constraint list)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-183">If you need to impose more than one requirement, you use a comma-separated *constraint list* inside braces (`{ }`).</span></span> <span data-ttu-id="a0a96-184">若要要求存取的建構函式，包括[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)清單中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a0a96-184">To require an accessible constructor, you include the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the list.</span></span> <span data-ttu-id="a0a96-185">若需要參考類型，請包括 `Class` 關鍵字；若需要實值類型，請包括 `Structure` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a0a96-185">To require a reference type, you include the `Class` keyword; to require a value type, you include the `Structure` keyword.</span></span>  
  
 <span data-ttu-id="a0a96-186">如需有關條件約束的詳細資訊，請參閱[類型清單](../../../../visual-basic/language-reference/statements/type-list.md)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-186">For more information on constraints, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
### <a name="example-of-multiple-constraints"></a><span data-ttu-id="a0a96-187">多個條件約束範例</span><span class="sxs-lookup"><span data-stu-id="a0a96-187">Example of Multiple Constraints</span></span>  
 <span data-ttu-id="a0a96-188">下列範例顯示類型參數上具有條件約束清單之泛型類別的基本架構定義。</span><span class="sxs-lookup"><span data-stu-id="a0a96-188">The following example shows a skeleton definition of a generic class with a constraint list on the type parameter.</span></span> <span data-ttu-id="a0a96-189">建立這個類別的執行個體的程式碼，在型別引數必須同時實作<xref:System.IComparable>和<xref:System.IDisposable>介面，為參考型別，並公開存取的無參數建構函式。</xref:System.IDisposable> </xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="a0a96-189">In the code that creates an instance of this class, the type argument must implement both the <xref:System.IComparable> and <xref:System.IDisposable> interfaces, be a reference type, and expose an accessible parameterless constructor.</span></span>  
  
 <span data-ttu-id="a0a96-190">[!code-vb[VbVbalrDataTypes #&6;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0a96-190">[!code-vb[VbVbalrDataTypes#6](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]</span></span>  
  
## <a name="important-terms"></a><span data-ttu-id="a0a96-191">重要詞彙</span><span class="sxs-lookup"><span data-stu-id="a0a96-191">Important Terms</span></span>  
 <span data-ttu-id="a0a96-192">泛型類型引進並使用下列詞彙：</span><span class="sxs-lookup"><span data-stu-id="a0a96-192">Generic types introduce and use the following terms:</span></span>  
  
-   <span data-ttu-id="a0a96-193">*「泛型類型」*(Generic Type)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-193">*Generic Type*.</span></span> <span data-ttu-id="a0a96-194">在您宣告時至少提供一種資料類型之類別、結構、介面、程序或委派的定義。</span><span class="sxs-lookup"><span data-stu-id="a0a96-194">A definition of a class, structure, interface, procedure, or delegate for which you supply at least one data type when you declare it.</span></span>  
  
-   <span data-ttu-id="a0a96-195">*「類型參數」*(Type Parameter)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-195">*Type Parameter*.</span></span> <span data-ttu-id="a0a96-196">在泛型類型定義中，這是您在宣告類型時所提供之資料類型的預留位置。</span><span class="sxs-lookup"><span data-stu-id="a0a96-196">In a generic type definition, a placeholder for a data type you supply when you declare the type.</span></span>  
  
-   <span data-ttu-id="a0a96-197">*「類型引數」*(Type Argument)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-197">*Type Argument*.</span></span> <span data-ttu-id="a0a96-198">一種特定資料類型，會在您從泛型類型宣告已建構類型時取代類型參數。</span><span class="sxs-lookup"><span data-stu-id="a0a96-198">A specific data type that replaces a type parameter when you declare a constructed type from a generic type.</span></span>  
  
-   <span data-ttu-id="a0a96-199">*「條件約束」*(Constraint)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-199">*Constraint*.</span></span> <span data-ttu-id="a0a96-200">類型參數上限制您可以為其提供類型引數的條件。</span><span class="sxs-lookup"><span data-stu-id="a0a96-200">A condition on a type parameter that restricts the type argument you can supply for it.</span></span> <span data-ttu-id="a0a96-201">條件約束可以要求的類型引數必須實作特定介面、為特定類別或繼承自特定類別、具有可存取的無參數建構函式，或者為參考類型或實值類型。</span><span class="sxs-lookup"><span data-stu-id="a0a96-201">A constraint can require that the type argument must implement a particular interface, be or inherit from a particular class, have an accessible parameterless constructor, or be a reference type or a value type.</span></span> <span data-ttu-id="a0a96-202">您可以合併這些條件約束，但最多只能指定一個類別。</span><span class="sxs-lookup"><span data-stu-id="a0a96-202">You can combine these constraints, but you can specify at most one class.</span></span>  
  
-   <span data-ttu-id="a0a96-203">*「已建構類型」*(Constructed Type)。</span><span class="sxs-lookup"><span data-stu-id="a0a96-203">*Constructed Type*.</span></span> <span data-ttu-id="a0a96-204">透過提供其類型參數的類型引數，以從泛型類型宣告的類別、結構、介面、程序或委派。</span><span class="sxs-lookup"><span data-stu-id="a0a96-204">A class, structure, interface, procedure, or delegate declared from a generic type by supplying type arguments for its type parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a96-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0a96-205">See Also</span></span>  
 <span data-ttu-id="a0a96-206">[資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-206">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="a0a96-207"> [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-207"> [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="a0a96-208"> [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-208"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="a0a96-209"> [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-209"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="a0a96-210"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-210"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="a0a96-211"> [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-211"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="a0a96-212"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-212"> [Of](../../../../visual-basic/language-reference/statements/of-clause.md) </span></span>  
<span data-ttu-id="a0a96-213"> [做為](../../../../visual-basic/language-reference/statements/as-clause.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-213"> [As](../../../../visual-basic/language-reference/statements/as-clause.md) </span></span>  
<span data-ttu-id="a0a96-214"> [Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="a0a96-214"> [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) </span></span>  
<span data-ttu-id="a0a96-215"> [共變數和反變數](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span><span class="sxs-lookup"><span data-stu-id="a0a96-215"> [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) </span></span>  
<span data-ttu-id="a0a96-216"> [迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span><span class="sxs-lookup"><span data-stu-id="a0a96-216"> [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)</span></span>
