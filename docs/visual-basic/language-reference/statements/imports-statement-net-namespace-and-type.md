---
title: Imports 語句-.NET 命名空間和類型
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
ms.openlocfilehash: 39fa4e74f973bcb575b5751c387c0b879f4e398d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351073"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="9155a-102">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="9155a-102">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="9155a-103">在不限定命名空間的情況下，允許參考型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9155a-103">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="9155a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9155a-104">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="9155a-105">組件</span><span class="sxs-lookup"><span data-stu-id="9155a-105">Parts</span></span>

|<span data-ttu-id="9155a-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="9155a-106">Term</span></span>|<span data-ttu-id="9155a-107">定義</span><span class="sxs-lookup"><span data-stu-id="9155a-107">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="9155a-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9155a-108">Optional.</span></span> <span data-ttu-id="9155a-109">匯*入別名*或名稱，由程式碼用來參考 `namespace`，而不是完整限定字串。</span><span class="sxs-lookup"><span data-stu-id="9155a-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="9155a-110">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="9155a-110">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="9155a-111">必要。</span><span class="sxs-lookup"><span data-stu-id="9155a-111">Required.</span></span> <span data-ttu-id="9155a-112">要匯入之命名空間的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="9155a-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="9155a-113">可以是嵌套于任何層級的命名空間字串。</span><span class="sxs-lookup"><span data-stu-id="9155a-113">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="9155a-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9155a-114">Optional.</span></span> <span data-ttu-id="9155a-115">命名空間中宣告的程式設計項目名稱。</span><span class="sxs-lookup"><span data-stu-id="9155a-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="9155a-116">可以是任何容器元素。</span><span class="sxs-lookup"><span data-stu-id="9155a-116">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9155a-117">備註</span><span class="sxs-lookup"><span data-stu-id="9155a-117">Remarks</span></span>

<span data-ttu-id="9155a-118">`Imports` 語句可讓您直接參考指定命名空間中包含的類型。</span><span class="sxs-lookup"><span data-stu-id="9155a-118">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="9155a-119">您可以提供單一命名空間名稱或一個嵌套命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="9155a-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="9155a-120">每個嵌套的命名空間會與下一個較高層級的命名空間隔開（`.`），如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="9155a-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="9155a-121">每個來源檔案都可以包含任意數目的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="9155a-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="9155a-122">這些必須遵循任何選項宣告（例如 `Option Strict` 語句），而且必須在任何程式設計專案宣告之前，例如 `Module` 或 `Class` 語句。</span><span class="sxs-lookup"><span data-stu-id="9155a-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="9155a-123">您只能在檔案層級使用 `Imports`。</span><span class="sxs-lookup"><span data-stu-id="9155a-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="9155a-124">這表示匯入的宣告內容必須是原始程式檔，而且不能是命名空間、類別、結構、模組、介面、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="9155a-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="9155a-125">請注意，`Imports` 語句不會將其他專案和元件中的元素提供給您的專案。</span><span class="sxs-lookup"><span data-stu-id="9155a-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="9155a-126">匯入不會取代設定參考。</span><span class="sxs-lookup"><span data-stu-id="9155a-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="9155a-127">這只是不需要限定已可用於您專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="9155a-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="9155a-128">如需詳細資訊，請參閱宣告專案[參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「匯入包含元素」。</span><span class="sxs-lookup"><span data-stu-id="9155a-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9155a-129">您可以使用 [專案設計工具] 的 [[參考] 頁面（[Visual Basic]）](/visualstudio/ide/reference/references-page-project-designer-visual-basic)來定義隱含的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="9155a-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="9155a-130">如需詳細資訊，請參閱[如何：新增或移除匯入的命名空間（Visual Basic）](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="9155a-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="9155a-131">匯入別名</span><span class="sxs-lookup"><span data-stu-id="9155a-131">Import Aliases</span></span>

<span data-ttu-id="9155a-132">匯*入別名*會定義命名空間或類型的別名。</span><span class="sxs-lookup"><span data-stu-id="9155a-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="9155a-133">當您需要使用與一個或多個命名空間中宣告的相同名稱的專案時，匯入別名會很有用。</span><span class="sxs-lookup"><span data-stu-id="9155a-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="9155a-134">如需詳細資訊和範例，請參閱宣告[元素的參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「限定專案名稱」。</span><span class="sxs-lookup"><span data-stu-id="9155a-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="9155a-135">您不應該使用與 `aliasname`相同的名稱來宣告模組層級的成員。</span><span class="sxs-lookup"><span data-stu-id="9155a-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="9155a-136">如果您這樣做，Visual Basic 編譯器只會針對宣告的成員使用 `aliasname`，而不再將它辨識為匯入別名。</span><span class="sxs-lookup"><span data-stu-id="9155a-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="9155a-137">雖然用來宣告匯入別名的語法就像是用來匯入 XML 命名空間前置詞，但結果並不相同。</span><span class="sxs-lookup"><span data-stu-id="9155a-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="9155a-138">匯入別名可以當做程式碼中的運算式使用，而 XML 命名空間前置詞只能用在 XML 常值或 XML 軸屬性中，做為限定專案或屬性名稱的前置詞。</span><span class="sxs-lookup"><span data-stu-id="9155a-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="9155a-139">項目名稱</span><span class="sxs-lookup"><span data-stu-id="9155a-139">Element Names</span></span>

<span data-ttu-id="9155a-140">如果您提供 `element`，它必須代表*容器元素*，也就是可以包含其他元素的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="9155a-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="9155a-141">容器元素包括類別、結構、模組、介面和列舉。</span><span class="sxs-lookup"><span data-stu-id="9155a-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="9155a-142">`Imports` 語句所提供的元素範圍，視您是否指定 `element`而定。</span><span class="sxs-lookup"><span data-stu-id="9155a-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="9155a-143">如果您只指定 `namespace`，就可以使用該命名空間的所有唯一名稱成員，以及該命名空間內的容器元素成員，而無需限定。</span><span class="sxs-lookup"><span data-stu-id="9155a-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="9155a-144">如果您同時指定 `namespace` 和 `element`，則只有該元素的成員可以使用，而不需要限定。</span><span class="sxs-lookup"><span data-stu-id="9155a-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="9155a-145">範例</span><span class="sxs-lookup"><span data-stu-id="9155a-145">Example</span></span>

<span data-ttu-id="9155a-146">下列範例會使用 <xref:System.IO.DirectoryInfo> 類別，傳回*C：\\* 目錄中的所有資料夾：</span><span class="sxs-lookup"><span data-stu-id="9155a-146">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="9155a-147">此程式碼在檔案的頂端沒有 `Imports` 的語句。</span><span class="sxs-lookup"><span data-stu-id="9155a-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="9155a-148">因此，<xref:System.IO.DirectoryInfo>、<xref:System.Text.StringBuilder>和 <xref:Microsoft.VisualBasic.ControlChars.CrLf> 參考都是以命名空間完整限定。</span><span class="sxs-lookup"><span data-stu-id="9155a-148">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="9155a-149">範例</span><span class="sxs-lookup"><span data-stu-id="9155a-149">Example</span></span>

<span data-ttu-id="9155a-150">下列範例包含所參考之命名空間的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="9155a-150">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="9155a-151">因此，類型不一定要使用命名空間來完整限定。</span><span class="sxs-lookup"><span data-stu-id="9155a-151">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="9155a-152">範例</span><span class="sxs-lookup"><span data-stu-id="9155a-152">Example</span></span>

<span data-ttu-id="9155a-153">下列範例包含 `Imports` 語句，以建立參考之命名空間的別名。</span><span class="sxs-lookup"><span data-stu-id="9155a-153">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="9155a-154">類型是以別名限定。</span><span class="sxs-lookup"><span data-stu-id="9155a-154">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="9155a-155">範例</span><span class="sxs-lookup"><span data-stu-id="9155a-155">Example</span></span>

<span data-ttu-id="9155a-156">下列範例包含 `Imports` 語句，以建立參考類型的別名。</span><span class="sxs-lookup"><span data-stu-id="9155a-156">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="9155a-157">別名是用來指定類型。</span><span class="sxs-lookup"><span data-stu-id="9155a-157">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="9155a-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9155a-158">See also</span></span>

- [<span data-ttu-id="9155a-159">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="9155a-159">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="9155a-160">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="9155a-160">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="9155a-161">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="9155a-161">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="9155a-162">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="9155a-162">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="9155a-163">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="9155a-163">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
