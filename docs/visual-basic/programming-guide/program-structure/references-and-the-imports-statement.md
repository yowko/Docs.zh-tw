---
title: "參考和 Imports 陳述式 (Visual Basic) |Microsoft 文件"
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
- assemblies [Visual Basic], namespaces
- references, assembly
- namespaces, assemblies
- referencing assemblies
- Imports statement, referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4c6ce65005f84317c96a1124d609c46734d3cc66
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="e64be-102">參考和 Imports 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e64be-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="e64be-103">您可以使用外部物件至您的專案選擇**加入參考**命令**專案**功能表。</span><span class="sxs-lookup"><span data-stu-id="e64be-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="e64be-104">在參考[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可以指向組件，就像但包含型別程式庫的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e64be-104">References in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="e64be-105">Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="e64be-105">The Imports Statement</span></span>  
 <span data-ttu-id="e64be-106">組件包含一或多個命名空間。</span><span class="sxs-lookup"><span data-stu-id="e64be-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="e64be-107">當您將加入組件的參考時，您也可以加入`Imports`陳述式，以控制可見性的模組內的組件的命名空間的模組。</span><span class="sxs-lookup"><span data-stu-id="e64be-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="e64be-108">`Imports`陳述式提供的內容範圍設定，可讓您使用只需要提供唯一的參考命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="e64be-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="e64be-109">`Imports`陳述式的語法如下︰</span><span class="sxs-lookup"><span data-stu-id="e64be-109">The `Imports` statement has the following syntax:</span></span>  
  
 <span data-ttu-id="e64be-110">`Imports` [`|``Aliasname` =] `Namespace`</span><span class="sxs-lookup"><span data-stu-id="e64be-110">`Imports` [`|``Aliasname` =] `Namespace`</span></span>  
  
 <span data-ttu-id="e64be-111">`Aliasname`指的是簡短名稱，您可以使用程式碼中參考匯入的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e64be-111">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="e64be-112">`Namespace`透過在專案中，定義或先前的專案參考是命名空間，可透過`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e64be-112">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="e64be-113">模組可能包含任意數目的`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e64be-113">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="e64be-114">它們必須出現在任何之後`Option`陳述式，如果存在，但在任何其他程式碼之前。</span><span class="sxs-lookup"><span data-stu-id="e64be-114">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e64be-115">請勿混淆的專案參考`Imports`陳述式或`Declare`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e64be-115">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="e64be-116">專案參考的組件中的物件等外部物件可讓以[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="e64be-116">Project references make external objects, such as objects in assemblies, available to [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projects.</span></span> <span data-ttu-id="e64be-117">`Imports`陳述式用來簡化專案參考的存取，但並不提供這些物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="e64be-117">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="e64be-118">`Declare`陳述式用來宣告外部程序中的動態連結程式庫 (DLL) 的參考。</span><span class="sxs-lookup"><span data-stu-id="e64be-118">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="e64be-119">使用 Imports 陳述式的別名</span><span class="sxs-lookup"><span data-stu-id="e64be-119">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="e64be-120">`Imports`陳述式就可以更輕鬆地存取方法的類別而不必明確地輸入完整的參考名稱。</span><span class="sxs-lookup"><span data-stu-id="e64be-120">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="e64be-121">別名可讓您更易記的名稱為命名空間的一部分。</span><span class="sxs-lookup"><span data-stu-id="e64be-121">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="e64be-122">比方說，歸位/換會導致一段文字，以顯示多行的順序是一部分<xref:Microsoft.VisualBasic.ControlChars>中的模組<xref:Microsoft.VisualBasic?displayProperty=fullName>命名空間。</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="e64be-122">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="e64be-123">若要在程式中不含別名中使用這個常數，您必須輸入下列程式碼︰</span><span class="sxs-lookup"><span data-stu-id="e64be-123">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 <span data-ttu-id="e64be-124">[!code-vb[VbVbalrApplication #&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e64be-124">[!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="e64be-125">`Imports`陳述式必須是第一個程式碼行，並緊接著任何`Option`模組中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="e64be-125">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="e64be-126">下列程式碼片段示範如何匯入並指派別名<xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>模組︰</xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e64be-126">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName> module:</span></span>  
  
 <span data-ttu-id="e64be-127">[!code-vb[VbVbalrApplication #&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e64be-127">[!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="e64be-128">未來參考此命名空間可以是非常簡短︰</span><span class="sxs-lookup"><span data-stu-id="e64be-128">Future references to this namespace can be considerably shorter:</span></span>  
  
 <span data-ttu-id="e64be-129">[!code-vb[VbVbalrApplication #&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e64be-129">[!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="e64be-130">如果`Imports`陳述式不包含別名名稱，匯入的命名空間內定義的項目可以用於無限制的模組。</span><span class="sxs-lookup"><span data-stu-id="e64be-130">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="e64be-131">如果指定的別名名稱，則它必須當做限定詞，包含該命名空間內的名稱。</span><span class="sxs-lookup"><span data-stu-id="e64be-131">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e64be-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e64be-132">See Also</span></span>  
 <span data-ttu-id="e64be-133"><xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars></span><span class="sxs-lookup"><span data-stu-id="e64be-133"><xref:Microsoft.VisualBasic.ControlChars></span></span>   
 <span data-ttu-id="e64be-134"><xref:Microsoft.VisualBasic></xref:Microsoft.VisualBasic></span><span class="sxs-lookup"><span data-stu-id="e64be-134"><xref:Microsoft.VisualBasic></span></span>   
<span data-ttu-id="e64be-135"> [NIB 如何：使用加入參考對話方塊加入或移除參考](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="e64be-135"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="e64be-136"> [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="e64be-136"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="e64be-137"> [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="e64be-137"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="e64be-138"> [如何︰ 建立和使用組件︰ 使用命令列](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span><span class="sxs-lookup"><span data-stu-id="e64be-138"> [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4) </span></span>  
<span data-ttu-id="e64be-139"> [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span><span class="sxs-lookup"><span data-stu-id="e64be-139"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)</span></span>
