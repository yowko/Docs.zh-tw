---
title: Imports 陳述式-.NET 命名空間和類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 0211438e8b4c02fead910dd7a32e0df9ed73ddc5
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925594"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="7152d-102">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="7152d-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="7152d-103">可讓類型參考而不需要命名空間限定性條件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7152d-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7152d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7152d-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="7152d-105">組件</span><span class="sxs-lookup"><span data-stu-id="7152d-105">Parts</span></span>  
  
|<span data-ttu-id="7152d-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="7152d-106">Term</span></span>|<span data-ttu-id="7152d-107">定義</span><span class="sxs-lookup"><span data-stu-id="7152d-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="7152d-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7152d-108">Optional.</span></span> <span data-ttu-id="7152d-109">*匯入別名*或 程式碼可以參考到名稱`namespace`而不是完整限定性條件字串。</span><span class="sxs-lookup"><span data-stu-id="7152d-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="7152d-110">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="7152d-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="7152d-111">必要。</span><span class="sxs-lookup"><span data-stu-id="7152d-111">Required.</span></span> <span data-ttu-id="7152d-112">正在匯入的命名空間完整限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="7152d-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="7152d-113">可以是命名空間的巢狀字串為任何層級。</span><span class="sxs-lookup"><span data-stu-id="7152d-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="7152d-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7152d-114">Optional.</span></span> <span data-ttu-id="7152d-115">命名空間中宣告的程式設計項目名稱。</span><span class="sxs-lookup"><span data-stu-id="7152d-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="7152d-116">可以是任何容器項目。</span><span class="sxs-lookup"><span data-stu-id="7152d-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7152d-117">備註</span><span class="sxs-lookup"><span data-stu-id="7152d-117">Remarks</span></span>  
 <span data-ttu-id="7152d-118">`Imports`陳述式可啟用包含在指定的命名空間，來直接參考的類型。</span><span class="sxs-lookup"><span data-stu-id="7152d-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="7152d-119">您可以提供單一的命名空間名稱或巢狀命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="7152d-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="7152d-120">每個巢狀命名空間以句號分隔下一個較高的層級命名空間 (`.`)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7152d-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="7152d-121">每個來源檔案可以包含任意數目的`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7152d-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="7152d-122">這些必須遵循的任何選項宣告，例如`Option Strict`陳述式，而且它們必須在前面的任何程式設計項目宣告，例如`Module`或`Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7152d-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="7152d-123">您可以使用`Imports`只能在檔案層級。</span><span class="sxs-lookup"><span data-stu-id="7152d-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="7152d-124">這表示匯入作業的宣告內容必須是原始程式檔，且不能命名空間、 類別、 結構、 模組、 介面、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="7152d-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="7152d-125">請注意，`Imports`陳述式不會從其他專案和組件的項目提供至您的專案。</span><span class="sxs-lookup"><span data-stu-id="7152d-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="7152d-126">匯入不會設定參考。</span><span class="sxs-lookup"><span data-stu-id="7152d-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="7152d-127">此外，它只會移除已可供專案的名稱進行限定的需求。</span><span class="sxs-lookup"><span data-stu-id="7152d-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="7152d-128">如需詳細資訊，請參閱 < 匯入包含項目 」 中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="7152d-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7152d-129">您可以定義隱含`Imports`陳述式，利用[參考 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="7152d-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="7152d-130">如需詳細資訊，請參閱 <<c0> [ 如何： 加入或移除已匯入命名空間 (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="7152d-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="7152d-131">匯入別名</span><span class="sxs-lookup"><span data-stu-id="7152d-131">Import Aliases</span></span>  
 <span data-ttu-id="7152d-132">*匯入別名*定義命名空間或類型的別名。</span><span class="sxs-lookup"><span data-stu-id="7152d-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="7152d-133">當您需要使用一或多個命名空間中宣告的同名的項目，則匯入別名會非常有用。</span><span class="sxs-lookup"><span data-stu-id="7152d-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="7152d-134">如需詳細資訊和範例，請參閱 「 合格的項目名稱 」 中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。</span><span class="sxs-lookup"><span data-stu-id="7152d-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="7152d-135">您不應該宣告同名的模組層級的成員`aliasname`。</span><span class="sxs-lookup"><span data-stu-id="7152d-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="7152d-136">如果您這樣做，就會使用 Visual Basic 編譯器`aliasname`只針對宣告的成員，但不能將其辨識為匯入別名。</span><span class="sxs-lookup"><span data-stu-id="7152d-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="7152d-137">雖然用來宣告匯入別名的語法類似用於匯入 XML 命名空間前置詞，結果就不同。</span><span class="sxs-lookup"><span data-stu-id="7152d-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="7152d-138">匯入別名可以用做您的程式碼中的運算式，而 XML 命名空間前置詞可以用於只能在 XML 常值或 XML 軸屬性做為前置詞限定的項目或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="7152d-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="7152d-139">項目名稱</span><span class="sxs-lookup"><span data-stu-id="7152d-139">Element Names</span></span>  
 <span data-ttu-id="7152d-140">如果您提供`element`，它必須表示*的容器項目*，也就是程式設計項目可以包含其他元素。</span><span class="sxs-lookup"><span data-stu-id="7152d-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="7152d-141">容器項目包括類別、 結構、 模組、 介面和列舉型別。</span><span class="sxs-lookup"><span data-stu-id="7152d-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="7152d-142">所提供的項目範圍`Imports`陳述式，取決於您是否指定`element`。</span><span class="sxs-lookup"><span data-stu-id="7152d-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="7152d-143">如果您只有指定`namespace`、 所有唯一命名為該命名空間，以及該命名空間內的容器項目的成員，都可供使用。</span><span class="sxs-lookup"><span data-stu-id="7152d-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="7152d-144">如果您同時指定`namespace`和`element`，只有該元素的成員都可供使用。</span><span class="sxs-lookup"><span data-stu-id="7152d-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7152d-145">範例</span><span class="sxs-lookup"><span data-stu-id="7152d-145">Example</span></span>  
 <span data-ttu-id="7152d-146">下列範例傳回 C:\ 目錄中的所有資料夾，使用<xref:System.IO.DirectoryInfo>類別。</span><span class="sxs-lookup"><span data-stu-id="7152d-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="7152d-147">程式碼沒有`Imports`陳述式在檔案頂端。</span><span class="sxs-lookup"><span data-stu-id="7152d-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="7152d-148">因此， `DirectoryInfo`， <xref:System.Text.StringBuilder>，和<xref:Microsoft.VisualBasic.ControlChars.CrLf>是命名空間與所有完整的參考。</span><span class="sxs-lookup"><span data-stu-id="7152d-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="7152d-149">範例</span><span class="sxs-lookup"><span data-stu-id="7152d-149">Example</span></span>  
 <span data-ttu-id="7152d-150">下列範例會加入`Imports`參考的命名空間的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7152d-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="7152d-151">因此，型別不必完整限定的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7152d-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="7152d-152">範例</span><span class="sxs-lookup"><span data-stu-id="7152d-152">Example</span></span>  
 <span data-ttu-id="7152d-153">下列範例會加入`Imports`為參考的命名空間建立別名的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7152d-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="7152d-154">類型是以別名限定。</span><span class="sxs-lookup"><span data-stu-id="7152d-154">The types are qualified with the aliases.</span></span>  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="7152d-155">範例</span><span class="sxs-lookup"><span data-stu-id="7152d-155">Example</span></span>  
 <span data-ttu-id="7152d-156">下列範例會加入`Imports`陳述式建立參考類型的別名。</span><span class="sxs-lookup"><span data-stu-id="7152d-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="7152d-157">別名用來指定的類型。</span><span class="sxs-lookup"><span data-stu-id="7152d-157">Aliases are used to specify the types.</span></span>  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7152d-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7152d-158">See Also</span></span>  
 [<span data-ttu-id="7152d-159">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="7152d-159">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="7152d-160">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="7152d-160">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="7152d-161">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="7152d-161">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="7152d-162">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="7152d-162">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="7152d-163">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="7152d-163">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
