---
title: 參考和 Imports 陳述式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 89d360e5caa3cdb0dd1ecb985ea7ba727e5a6d9d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208506"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="354e8-102">參考和 Imports 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="354e8-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="354e8-103">您可以對外部物件可以使用您的專案選擇**加入參考**命令**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="354e8-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="354e8-104">在 Visual Basic 中的參考可以指向組件，就像型別程式庫，但包含更多資訊。</span><span class="sxs-lookup"><span data-stu-id="354e8-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="354e8-105">Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="354e8-105">The Imports Statement</span></span>  
 <span data-ttu-id="354e8-106">組件包含一或多個命名空間。</span><span class="sxs-lookup"><span data-stu-id="354e8-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="354e8-107">當您新增組件的參考時，您也可以新增`Imports`陳述式來控制模組內的組件的命名空間的可見性的模組。</span><span class="sxs-lookup"><span data-stu-id="354e8-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="354e8-108">`Imports`陳述式提供的範圍的內容，可讓您使用只需要提供唯一的參考命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="354e8-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="354e8-109">`Imports`陳述式的語法如下：</span><span class="sxs-lookup"><span data-stu-id="354e8-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="354e8-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="354e8-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="354e8-111">`Aliasname` 是指您可以使用程式碼中參考匯入的命名空間的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="354e8-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="354e8-112">`Namespace` 透過定義在專案中，或透過先前的專案參考是可透過其中一個命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="354e8-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="354e8-113">模組可能包含任意數目的`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="354e8-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="354e8-114">它們必須出現在任何之後`Option`陳述式，如果有的話，但任何其他程式碼之前。</span><span class="sxs-lookup"><span data-stu-id="354e8-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="354e8-115">請勿混淆的專案參考`Imports`陳述式或`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="354e8-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="354e8-116">專案參考的組件中的物件等外部物件可讓 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="354e8-116">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="354e8-117">`Imports`陳述式可用來簡化存取專案的參考，但並不會提供這些物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="354e8-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="354e8-118">`Declare`陳述式用來宣告外部程序動態連結程式庫 (DLL) 中的參考。</span><span class="sxs-lookup"><span data-stu-id="354e8-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="354e8-119">使用 Imports 陳述式的別名</span><span class="sxs-lookup"><span data-stu-id="354e8-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="354e8-120">`Imports`陳述式就可以更輕鬆地存取方法的類別不需要明確地輸入完整的名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="354e8-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="354e8-121">別名可讓您將容易使用的名稱指派給命名空間的一個部分而已。</span><span class="sxs-lookup"><span data-stu-id="354e8-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="354e8-122">比方說，歸位/換行會導致一段文字，以在多行上顯示的順序會是一部分<xref:Microsoft.VisualBasic.ControlChars>中的模組<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="354e8-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="354e8-123">若要在程式中不含別名中使用這個常數，您需要輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="354e8-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="354e8-124">`Imports` 陳述式都必須緊接著任何的前幾行`Option`模組中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="354e8-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="354e8-125">下列程式碼片段示範如何匯入並指派至別名<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>模組：</span><span class="sxs-lookup"><span data-stu-id="354e8-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="354e8-126">未來參考此命名空間可以是非常簡短的：</span><span class="sxs-lookup"><span data-stu-id="354e8-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="354e8-127">如果`Imports`陳述式不包含別名名稱，匯入的命名空間內定義的項目可用在不需完整的模組。</span><span class="sxs-lookup"><span data-stu-id="354e8-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="354e8-128">如果指定的別名名稱，則它必須用作辨識符號包含在該命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="354e8-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354e8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="354e8-129">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="354e8-130">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="354e8-130">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
- [<span data-ttu-id="354e8-131">組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="354e8-131">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [<span data-ttu-id="354e8-132">如何：使用命令列建立和使用組件</span><span class="sxs-lookup"><span data-stu-id="354e8-132">How to: Create and Use Assemblies Using the Command Line</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)  
- [<span data-ttu-id="354e8-133">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="354e8-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
