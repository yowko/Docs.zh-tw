---
title: 命名空間陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 28016763b2cef2e8b8954f486bbbdb6930b5364c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417408"
---
# <a name="namespace-statement"></a><span data-ttu-id="c2f78-102">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="c2f78-102">Namespace Statement</span></span>
<span data-ttu-id="c2f78-103">宣告命名空間的名稱，並造成接在宣告該命名空間內進行編譯的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2f78-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f78-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2f78-104">Syntax</span></span>  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="c2f78-105">組件</span><span class="sxs-lookup"><span data-stu-id="c2f78-105">Parts</span></span>  
 <span data-ttu-id="c2f78-106">Global</span><span class="sxs-lookup"><span data-stu-id="c2f78-106">Global</span></span>  
 <span data-ttu-id="c2f78-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c2f78-107">Optional.</span></span> <span data-ttu-id="c2f78-108">可讓您定義的命名空間從您的專案的根命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="c2f78-109">請參閱[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f78-109">See [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="c2f78-110">必要。</span><span class="sxs-lookup"><span data-stu-id="c2f78-110">Required.</span></span> <span data-ttu-id="c2f78-111">唯一的名稱識別命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="c2f78-112">必須是有效的 Visual Basic 識別項。</span><span class="sxs-lookup"><span data-stu-id="c2f78-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="c2f78-113">如需詳細資訊，請參閱 <<c0> [ 宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f78-113">For more information, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="c2f78-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c2f78-114">Optional.</span></span> <span data-ttu-id="c2f78-115">命名空間所組成的項目。</span><span class="sxs-lookup"><span data-stu-id="c2f78-115">Elements that make up the namespace.</span></span> <span data-ttu-id="c2f78-116">這些包括但不限於列舉、 結構、 介面、 類別、 模組、 委派及其他命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="c2f78-117">終止`Namespace`區塊。</span><span class="sxs-lookup"><span data-stu-id="c2f78-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2f78-118">備註</span><span class="sxs-lookup"><span data-stu-id="c2f78-118">Remarks</span></span>  
 <span data-ttu-id="c2f78-119">命名空間會作為組織的系統。</span><span class="sxs-lookup"><span data-stu-id="c2f78-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="c2f78-120">它們提供分類，並提供程式設計的項目公開給其他程式和應用程式的方式。</span><span class="sxs-lookup"><span data-stu-id="c2f78-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="c2f78-121">請注意，命名空間不是*型別*意思是類別或結構，您不能宣告為具有資料類型的命名空間的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="c2f78-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="c2f78-122">所有的程式設計項目宣告之後`Namespace`陳述式屬於該命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="c2f78-123">Visual Basic 會繼續編譯成最後一個宣告的命名空間的項目，直到它遇到其中`End Namespace`陳述式或另一個`Namespace`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2f78-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="c2f78-124">如果已經定義命名空間，甚至是外部專案中，您可以新增給它的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="c2f78-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="c2f78-125">若要這樣做，您使用`Namespace`直接編譯項目至該命名空間的 Visual Basic 的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2f78-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="c2f78-126">您可以使用`Namespace`只能在檔案或命名空間層級的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2f78-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="c2f78-127">這表示*宣告內容*命名空間必須是原始程式檔或另一個命名空間，並不是類別、 結構、 模組、 介面或程序。</span><span class="sxs-lookup"><span data-stu-id="c2f78-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="c2f78-128">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f78-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="c2f78-129">您可以宣告在另一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-129">You can declare one namespace within another.</span></span> <span data-ttu-id="c2f78-130">您可以宣告，但請記住，當其他程式碼存取最內層的命名空間中宣告的項目時，它必須使用限定性條件字串，包含巢狀階層中的所有命名空間名稱的巢狀層級沒有嚴格限制。</span><span class="sxs-lookup"><span data-stu-id="c2f78-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="c2f78-131">存取層級</span><span class="sxs-lookup"><span data-stu-id="c2f78-131">Access Level</span></span>  
 <span data-ttu-id="c2f78-132">命名空間會視為它們有`Public`存取層級。</span><span class="sxs-lookup"><span data-stu-id="c2f78-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="c2f78-133">從相同的專案中的任何位置的程式碼、 其他參考該專案的專案和專案所建立的任何組件，就可以存取命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="c2f78-134">在命名空間層級，這表示命名空間中，但不是能在任何其他項目，宣告的程式設計項目可以有`Public`或`Friend`存取。</span><span class="sxs-lookup"><span data-stu-id="c2f78-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="c2f78-135">如果未指定，這類的存取層級項目使用`Friend`預設。</span><span class="sxs-lookup"><span data-stu-id="c2f78-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="c2f78-136">您可以在命名空間層級宣告的項目包括類別、 結構、 模組、 介面、 列舉和委派。</span><span class="sxs-lookup"><span data-stu-id="c2f78-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="c2f78-137">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f78-137">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="c2f78-138">根命名空間</span><span class="sxs-lookup"><span data-stu-id="c2f78-138">Root Namespace</span></span>  
 <span data-ttu-id="c2f78-139">在您的專案中的所有命名空間名稱為基礎*根命名空間*。</span><span class="sxs-lookup"><span data-stu-id="c2f78-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="c2f78-140">Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="c2f78-141">例如，如果專案已命名為 `Payroll`，其程式設計項目會屬於命名空間 `Payroll`。</span><span class="sxs-lookup"><span data-stu-id="c2f78-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="c2f78-142">如果您宣告`Namespace funding`，該命名空間的完整名稱是`Payroll.funding`。</span><span class="sxs-lookup"><span data-stu-id="c2f78-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="c2f78-143">如果您想要指定現有的命名空間中`Namespace`陳述式，例如在泛型清單類別範例中，您可以設定您的根命名空間為 null 值。</span><span class="sxs-lookup"><span data-stu-id="c2f78-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="c2f78-144">若要這樣做，請按一下**專案屬性**從**專案**功能表，然後清除**根命名空間**項目以便方塊是空的。</span><span class="sxs-lookup"><span data-stu-id="c2f78-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="c2f78-145">如果您未這麼做在泛型清單類別的範例中，採取 Visual Basic 編譯器`System.Collections.Generic`專案中的新命名空間`Payroll`，以完整名稱`Payroll.System.Collections.Generic`。</span><span class="sxs-lookup"><span data-stu-id="c2f78-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="c2f78-146">或者，您可以使用`Global`關鍵字來參考您的專案以外定義的命名空間的項目。</span><span class="sxs-lookup"><span data-stu-id="c2f78-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="c2f78-147">如此一來，可讓您保留您的專案名稱，當做根命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="c2f78-148">這可減少意外合併您的程式設計項目，以及現有的命名空間的機會。</span><span class="sxs-lookup"><span data-stu-id="c2f78-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="c2f78-149">如需詳細資訊，請參閱中的 「 全域關鍵字中完整限定名稱 」 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f78-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="c2f78-150">`Global`關鍵字也可以用於命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="c2f78-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="c2f78-151">這可讓您從專案的根命名空間定義一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="c2f78-152">如需詳細資訊，請參閱中的 < 全域關鍵字在命名空間陳述式 > 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f78-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="c2f78-153">**疑難排解。**</span><span class="sxs-lookup"><span data-stu-id="c2f78-153">**Troubleshooting.**</span></span> <span data-ttu-id="c2f78-154">根命名空間可能會導致非預期的命名空間名稱的串連。</span><span class="sxs-lookup"><span data-stu-id="c2f78-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="c2f78-155">若要在專案以外定義的命名空間的參考，Visual Basic 編譯器可以將它們當做是根命名空間中的巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="c2f78-156">在此情況下，編譯器無法辨識已經定義外部命名空間中的任何型別。</span><span class="sxs-lookup"><span data-stu-id="c2f78-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="c2f78-157">若要避免這個問題，請將您的根命名空間設定為 「 根命名空間 」 中所述的 null 值，或使用`Global`關鍵字來存取的外部命名空間的項目。</span><span class="sxs-lookup"><span data-stu-id="c2f78-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="c2f78-158">屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="c2f78-158">Attributes and Modifiers</span></span>  
 <span data-ttu-id="c2f78-159">您無法將屬性套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="c2f78-160">屬性會提供資訊給組件的中繼資料，這不是有意義的來源分類器，例如命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="c2f78-161">您無法將任何存取或程序修飾詞或任何其他修飾詞，套用至命名空間中。</span><span class="sxs-lookup"><span data-stu-id="c2f78-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="c2f78-162">由於不是類型，這些修飾詞不是有意義的。</span><span class="sxs-lookup"><span data-stu-id="c2f78-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2f78-163">範例</span><span class="sxs-lookup"><span data-stu-id="c2f78-163">Example</span></span>  
 <span data-ttu-id="c2f78-164">下列範例會宣告兩個命名空間，巢狀方式置於另一個。</span><span class="sxs-lookup"><span data-stu-id="c2f78-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2f78-165">範例</span><span class="sxs-lookup"><span data-stu-id="c2f78-165">Example</span></span>  
 <span data-ttu-id="c2f78-166">下列範例會宣告多個巢狀命名空間以單行，並相當於先前的範例。</span><span class="sxs-lookup"><span data-stu-id="c2f78-166">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2f78-167">範例</span><span class="sxs-lookup"><span data-stu-id="c2f78-167">Example</span></span>  
 <span data-ttu-id="c2f78-168">下列範例會存取先前的範例中定義的類別。</span><span class="sxs-lookup"><span data-stu-id="c2f78-168">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="c2f78-169">範例</span><span class="sxs-lookup"><span data-stu-id="c2f78-169">Example</span></span>  
 <span data-ttu-id="c2f78-170">下列範例會定義新的泛型清單類別的基本架構，並將它加入<xref:System.Collections.Generic?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="c2f78-170">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2f78-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2f78-171">See Also</span></span>  
 [<span data-ttu-id="c2f78-172">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="c2f78-172">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="c2f78-173">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="c2f78-173">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="c2f78-174">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="c2f78-174">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
