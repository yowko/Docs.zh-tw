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
ms.openlocfilehash: 5b810af86f8659ffbe27d23d36aece408516a9bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972050"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="f3fe6-102">參考和 Imports 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3fe6-102">References and the Imports Statement (Visual Basic)</span></span>
<span data-ttu-id="f3fe6-103">您可以選擇 [**專案**] 功能表上的 [**加入參考**] 命令，讓外部物件可供專案使用。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="f3fe6-104">Visual Basic 中的參考可以指向類似類型程式庫的元件，但會包含詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="f3fe6-105">Imports 語句</span><span class="sxs-lookup"><span data-stu-id="f3fe6-105">The Imports Statement</span></span>  
 <span data-ttu-id="f3fe6-106">元件包含一或多個命名空間。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="f3fe6-107">當您加入元件的參考時，您也可以將`Imports`語句加入模組中，以控制該元件在模組內的可見度。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="f3fe6-108">`Imports`語句提供範圍內容，讓您只使用提供唯一參考所需的命名空間部分。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="f3fe6-109">`Imports`語句具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="f3fe6-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="f3fe6-110">`Aliasname`是指您可以在程式碼內用來參考已匯入之命名空間的簡短名稱。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="f3fe6-111">`Namespace`是透過專案參考、專案內的定義，或透過上`Imports`一個語句提供的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="f3fe6-112">模組可以包含任意數目的`Imports`語句。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="f3fe6-113">它們必須出現在任何`Option`語句之後（如果有的話），但在任何其他程式碼之前。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3fe6-114">請勿混淆專案參考與`Imports`語句`Declare`或語句。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="f3fe6-115">專案參考會使外部物件（例如元件中的物件）可用於 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="f3fe6-116">`Imports`語句可用來簡化對專案參考的存取，但不會提供這些物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="f3fe6-117">`Declare`語句是用來在動態連結程式庫（DLL）中宣告外部程式的參考。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="f3fe6-118">搭配 Imports 語句使用別名</span><span class="sxs-lookup"><span data-stu-id="f3fe6-118">Using Aliases with the Imports Statement</span></span>  
 <span data-ttu-id="f3fe6-119">`Imports`語句可讓您藉由排除明確輸入參考完整名稱的需求，更輕鬆地存取類別的方法。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="f3fe6-120">別名可讓您將易記名稱指派給命名空間的一個部分。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="f3fe6-121">例如，導致在多行上顯示單一文字片段的線路傳回/換行字元順序，就是<xref:Microsoft.VisualBasic.ControlChars> <xref:Microsoft.VisualBasic?displayProperty=nameWithType>命名空間中模組的一部分。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f3fe6-122">若要在沒有別名的程式中使用此常數，您必須輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="f3fe6-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="f3fe6-123">`Imports`語句必須一律是緊接在模組中任何`Option`語句之後的第一行。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="f3fe6-124">下列程式碼片段顯示如何匯入並指派別名給<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>模組：</span><span class="sxs-lookup"><span data-stu-id="f3fe6-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="f3fe6-125">未來對此命名空間的參考可能會變得很短：</span><span class="sxs-lookup"><span data-stu-id="f3fe6-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="f3fe6-126">`Imports`如果語句不包含別名名稱，在匯入的命名空間內定義的專案就可以在模組中使用，而不需要限定。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="f3fe6-127">如果指定別名名稱，則必須將它當做包含在該命名空間內之名稱的限定詞使用。</span><span class="sxs-lookup"><span data-stu-id="f3fe6-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fe6-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3fe6-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="f3fe6-129">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="f3fe6-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="f3fe6-130">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="f3fe6-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="f3fe6-131">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="f3fe6-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
