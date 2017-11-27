---
title: "Namespace 陳述式"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9863286a8eda2559ab678c77a81cc7d6063c3e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-statement"></a><span data-ttu-id="ef0a6-102">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="ef0a6-102">Namespace Statement</span></span>
<span data-ttu-id="ef0a6-103">宣告命名空間的名稱，並遵循編譯該命名空間中宣告的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef0a6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef0a6-104">Syntax</span></span>  
  
```  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="ef0a6-105">組件</span><span class="sxs-lookup"><span data-stu-id="ef0a6-105">Parts</span></span>  
 <span data-ttu-id="ef0a6-106">Global</span><span class="sxs-lookup"><span data-stu-id="ef0a6-106">Global</span></span>  
 <span data-ttu-id="ef0a6-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-107">Optional.</span></span> <span data-ttu-id="ef0a6-108">可讓您定義超出您的專案的根命名空間的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="ef0a6-109">請參閱[Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-109">See [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="ef0a6-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-110">Required.</span></span> <span data-ttu-id="ef0a6-111">唯一名稱識別命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="ef0a6-112">必須是有效的 Visual Basic 識別項。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="ef0a6-113">如需詳細資訊，請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-113">For more information, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="ef0a6-114">選擇項。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-114">Optional.</span></span> <span data-ttu-id="ef0a6-115">命名空間所組成的項目。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-115">Elements that make up the namespace.</span></span> <span data-ttu-id="ef0a6-116">這些包括但不限於列舉、 結構、 介面、 類別、 模組、 委派，以及其他命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="ef0a6-117">終止`Namespace`區塊。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef0a6-118">備註</span><span class="sxs-lookup"><span data-stu-id="ef0a6-118">Remarks</span></span>  
 <span data-ttu-id="ef0a6-119">命名空間會作為組織的系統。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="ef0a6-120">提供的方式來分類和呈現公開給其他程式和應用程式的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="ef0a6-121">請注意，命名空間不是*類型*類別或結構會在概念上，您無法宣告具有命名空間的資料類型的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="ef0a6-122">所有的程式設計項目宣告之後`Namespace`陳述式屬於該命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="ef0a6-123">若要編譯至最後一個宣告的命名空間的項目，直到它遇到任何的 Visual Basic 會繼續`End Namespace`陳述式或另一個`Namespace`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="ef0a6-124">如果已定義命名空間，即使超出您的專案，您可以新增程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="ef0a6-125">若要這樣做，您使用`Namespace`陳述式來直接 Visual Basic 編譯該命名空間中的項目。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="ef0a6-126">您可以使用`Namespace`陳述式只能在檔案或命名空間層級。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="ef0a6-127">這表示*宣告內容*命名空間必須是原始程式檔或另一個命名空間，而且不可為類別、 結構、 模組、 介面或程序。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="ef0a6-128">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-128">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="ef0a6-129">您可以宣告在另一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-129">You can declare one namespace within another.</span></span> <span data-ttu-id="ef0a6-130">您可以宣告，但是請記住，當其他程式碼存取的最內層的命名空間中宣告的項目時，它必須使用限定性條件字串，包含巢狀階層中的所有命名空間名稱的巢狀層級沒有嚴格限制。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="ef0a6-131">存取層級</span><span class="sxs-lookup"><span data-stu-id="ef0a6-131">Access Level</span></span>  
 <span data-ttu-id="ef0a6-132">命名空間會視為它們有`Public`存取層級。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="ef0a6-133">從程式碼在同一個專案中的任何位置、 其他參考該專案的專案和專案所建立的任何組件，就可以存取命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="ef0a6-134">命名空間層級，這表示命名空間中，但不是能在任何其他項目，在宣告的程式設計項目可以有`Public`或`Friend`存取。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="ef0a6-135">如果未指定，這類的存取層級項目使用`Friend`預設。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="ef0a6-136">您可以在命名空間層級宣告的項目包括類別、 結構、 模組、 介面、 列舉和委派。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="ef0a6-137">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-137">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="ef0a6-138">根命名空間</span><span class="sxs-lookup"><span data-stu-id="ef0a6-138">Root Namespace</span></span>  
 <span data-ttu-id="ef0a6-139">您的專案中的所有命名空間名稱根據*根命名空間*。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="ef0a6-140">Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="ef0a6-141">例如，如果專案已命名為 `Payroll`，其程式設計項目會屬於命名空間 `Payroll`。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="ef0a6-142">如果您宣告`Namespace funding`，該命名空間的完整名稱是`Payroll.funding`。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="ef0a6-143">如果您想要指定現有的命名空間中`Namespace`陳述式，例如在泛型清單類別範例中，您可以設定您的根命名空間為 null 值。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="ef0a6-144">若要這樣做，請按一下**專案屬性**從**專案**功能表，然後取消核取**根命名空間**項目以便方塊是空的。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="ef0a6-145">如果您沒有這麼做在泛型清單類別範例中，Visual Basic 編譯器會採用`System.Collections.Generic`做為新專案中的命名空間`Payroll`，使用的完整名稱`Payroll.System.Collections.Generic`。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="ef0a6-146">或者，您可以使用`Global`關鍵字來參考您的專案之外定義的命名空間的項目。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="ef0a6-147">這樣可讓您保留您的專案名稱做為根命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="ef0a6-148">這可減少意外合併程式設計項目與現有的命名空間的機會。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="ef0a6-149">如需詳細資訊，請參閱中的 「 全域關鍵字中完整限定名稱 」 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="ef0a6-150">`Global`關鍵字也可以用於命名空間陳述式。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="ef0a6-151">這可讓您從專案的根命名空間定義一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="ef0a6-152">如需詳細資訊，請參閱中的 「 全域關鍵字在命名空間陳述式 」 一節[在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="ef0a6-153">**疑難排解。**</span><span class="sxs-lookup"><span data-stu-id="ef0a6-153">**Troubleshooting.**</span></span> <span data-ttu-id="ef0a6-154">根命名空間可能會導致非預期的命名空間名稱的串連。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="ef0a6-155">若要在專案外部定義的命名空間的參考，Visual Basic 編譯器會將它們是做為根命名空間中的巢狀命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="ef0a6-156">在這種情況下，編譯器無法辨識已經定義外部命名空間中的任何型別。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="ef0a6-157">若要避免這個問題，請將您的根命名空間設定為 「 根命名空間 」 中所述的 null 值，或使用`Global`關鍵字來存取的外部命名空間的項目。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="ef0a6-158">屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="ef0a6-158">Attributes and Modifiers</span></span>  
 <span data-ttu-id="ef0a6-159">您無法將屬性套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="ef0a6-160">屬性會提供資訊給組件的中繼資料，不是有意義的來源分類器，例如命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="ef0a6-161">您無法將任何存取或程序修飾詞或任何其他修飾詞，套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="ef0a6-162">因為它不是型別，這些修飾詞並沒有意義。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef0a6-163">範例</span><span class="sxs-lookup"><span data-stu-id="ef0a6-163">Example</span></span>  
 <span data-ttu-id="ef0a6-164">下列範例會宣告兩個命名空間，其中巢狀方式置於另一個。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ef0a6-165">範例</span><span class="sxs-lookup"><span data-stu-id="ef0a6-165">Example</span></span>  
 <span data-ttu-id="ef0a6-166">下列範例會宣告多個巢狀命名空間在單一行中，它相當於先前的範例。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-166">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="ef0a6-167">範例</span><span class="sxs-lookup"><span data-stu-id="ef0a6-167">Example</span></span>  
 <span data-ttu-id="ef0a6-168">下列範例會存取先前範例中定義的類別。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-168">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="ef0a6-169">範例</span><span class="sxs-lookup"><span data-stu-id="ef0a6-169">Example</span></span>  
 <span data-ttu-id="ef0a6-170">下列範例會定義新的泛型清單類別的基本架構，並將它加入<xref:System.Collections.Generic?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="ef0a6-170">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef0a6-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef0a6-171">See Also</span></span>  
 [<span data-ttu-id="ef0a6-172">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="ef0a6-172">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="ef0a6-173">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="ef0a6-173">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="ef0a6-174">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="ef0a6-174">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
