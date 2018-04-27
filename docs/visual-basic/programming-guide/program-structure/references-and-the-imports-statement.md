---
title: 參考和 Imports 陳述式 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 051351c2fa0648de54bbfd36b1630ec1cd49d6f0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="ab34e-102">參考和 Imports 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab34e-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="ab34e-103">您可以使用外部物件至您的專案選擇**加入參考**命令**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="ab34e-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="ab34e-104">在 Visual Basic 中的參考可以指向組件，就像型別程式庫，但包含更多資訊。</span><span class="sxs-lookup"><span data-stu-id="ab34e-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="ab34e-105">Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="ab34e-105">The Imports Statement</span></span>  
 <span data-ttu-id="ab34e-106">組件包含一或多個命名空間。</span><span class="sxs-lookup"><span data-stu-id="ab34e-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="ab34e-107">當您將組件的參考時，您也可以加入`Imports`陳述式來控制在模組中的組件的命名空間的可見性的模組。</span><span class="sxs-lookup"><span data-stu-id="ab34e-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="ab34e-108">`Imports`陳述式提供的範圍的內容，可讓您使用只需要提供唯一的參考命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="ab34e-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="ab34e-109">`Imports`陳述式具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="ab34e-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="ab34e-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="ab34e-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="ab34e-111">`Aliasname` 是指您可以使用程式碼中參考匯入的命名空間的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="ab34e-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="ab34e-112">`Namespace` 透過定義在專案中，或透過先前的專案參考是透過使用命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab34e-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="ab34e-113">模組可能包含任意數目的`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab34e-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="ab34e-114">它們必須出現在任何之後`Option`陳述式，如果有的話，但任何其他程式碼之前。</span><span class="sxs-lookup"><span data-stu-id="ab34e-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab34e-115">請勿混淆的專案參考`Imports`陳述式或`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab34e-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="ab34e-116">專案參考的組件中的物件等外部物件可讓 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="ab34e-116">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="ab34e-117">`Imports`陳述式用來簡化存取專案的參考，但不提供這些物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="ab34e-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="ab34e-118">`Declare`陳述式用來宣告外部程序動態連結程式庫 (DLL) 中的參考。</span><span class="sxs-lookup"><span data-stu-id="ab34e-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="ab34e-119">Imports 陳述式搭配使用別名</span><span class="sxs-lookup"><span data-stu-id="ab34e-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="ab34e-120">`Imports`陳述式可以讓您更輕鬆地存取方法的類別不必明確地輸入參照的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="ab34e-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="ab34e-121">別名可讓您指派比較易記的名稱命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="ab34e-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="ab34e-122">比方說，歸位/換會導致一段文字，以在多行上顯示的順序是一部分<xref:Microsoft.VisualBasic.ControlChars>中的模組<xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="ab34e-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ab34e-123">若要在程式中不含別名中使用這個常數，您必須輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ab34e-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 <span data-ttu-id="ab34e-124">`Imports` 陳述式都必須緊接著任何前行`Option`模組中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="ab34e-124">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="ab34e-125">下列程式碼片段示範如何匯入並指派別名<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>模組：</span><span class="sxs-lookup"><span data-stu-id="ab34e-125">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 <span data-ttu-id="ab34e-126">未來參考此命名空間可以是非常簡短的：</span><span class="sxs-lookup"><span data-stu-id="ab34e-126">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 <span data-ttu-id="ab34e-127">如果`Imports`陳述式不包含的別名名稱，在匯入的命名空間中定義的項目可以用於無限制的模組。</span><span class="sxs-lookup"><span data-stu-id="ab34e-127">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="ab34e-128">如果指定的別名名稱，就必須採用與限定詞的名稱包含在該命名空間內。</span><span class="sxs-lookup"><span data-stu-id="ab34e-128">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab34e-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab34e-129">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
   
 [<span data-ttu-id="ab34e-130">在 Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="ab34e-130">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="ab34e-131">組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="ab34e-131">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="ab34e-132">如何：使用命令列建立和使用組件</span><span class="sxs-lookup"><span data-stu-id="ab34e-132">How to: Create and Use Assemblies Using the Command Line</span></span>](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [<span data-ttu-id="ab34e-133">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="ab34e-133">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
