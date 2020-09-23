---
title: References 與 Imports 陳述式
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 13f250e1b015e5a821da83e557033bc878a8a3b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097900"
---
# <a name="references-and-the-imports-statement-visual-basic"></a><span data-ttu-id="1c27b-102">參考和 Imports 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c27b-102">References and the Imports Statement (Visual Basic)</span></span>

<span data-ttu-id="1c27b-103">您可以選擇 [**專案**] 功能表上的 [**加入參考**] 命令，讓您的專案使用外部物件。</span><span class="sxs-lookup"><span data-stu-id="1c27b-103">You can make external objects available to your project by choosing the **Add Reference** command on the **Project** menu.</span></span> <span data-ttu-id="1c27b-104">Visual Basic 中的參考可指向元件，這類元件類似于類型程式庫，但會包含詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1c27b-104">References in Visual Basic can point to assemblies, which are like type libraries but contain more information.</span></span>  
  
## <a name="the-imports-statement"></a><span data-ttu-id="1c27b-105">Imports 語句</span><span class="sxs-lookup"><span data-stu-id="1c27b-105">The Imports Statement</span></span>  

 <span data-ttu-id="1c27b-106">元件包括一或多個命名空間。</span><span class="sxs-lookup"><span data-stu-id="1c27b-106">Assemblies include one or more namespaces.</span></span> <span data-ttu-id="1c27b-107">當您加入元件的參考時，您也可以將語句加入 `Imports` 至模組，以控制該元件之命名空間在模組內的可見度。</span><span class="sxs-lookup"><span data-stu-id="1c27b-107">When you add a reference to an assembly, you can also add an `Imports` statement to a module that controls the visibility of that assembly's namespaces within the module.</span></span> <span data-ttu-id="1c27b-108">`Imports`語句提供範圍內容，可讓您只使用提供唯一參考所需的命名空間部分。</span><span class="sxs-lookup"><span data-stu-id="1c27b-108">The `Imports` statement provides a scoping context that lets you use only the portion of the namespace necessary to supply a unique reference.</span></span>  
  
 <span data-ttu-id="1c27b-109">`Imports`語句具有下列語法：</span><span class="sxs-lookup"><span data-stu-id="1c27b-109">The `Imports` statement has the following syntax:</span></span>  
  
 `Imports [Aliasname =] Namespace`  
  
 <span data-ttu-id="1c27b-110">`Aliasname` 參考簡短名稱，您可以在程式碼中用來參考匯入的命名空間。</span><span class="sxs-lookup"><span data-stu-id="1c27b-110">`Aliasname` refers to a short name you can use within code to refer to an imported namespace.</span></span> <span data-ttu-id="1c27b-111">`Namespace` 是可透過專案參考、專案中的定義，或透過上一個語句來取得的命名空間 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="1c27b-111">`Namespace` is a namespace available through either a project reference, through a definition within the project, or through a previous `Imports` statement.</span></span>  
  
 <span data-ttu-id="1c27b-112">模組可包含任意數目的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="1c27b-112">A module may contain any number of `Imports` statements.</span></span> <span data-ttu-id="1c27b-113">它們必須出現在任何 `Option` 語句（如果有的話）之後，但在其他任何程式碼之前。</span><span class="sxs-lookup"><span data-stu-id="1c27b-113">They must appear after any `Option` statements, if present, but before any other code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c27b-114">請勿將專案參考與 `Imports` 語句或 `Declare` 語句混淆。</span><span class="sxs-lookup"><span data-stu-id="1c27b-114">Do not confuse project references with the `Imports` statement or the `Declare` statement.</span></span> <span data-ttu-id="1c27b-115">專案參考會將外部物件（例如元件中的物件）提供給 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="1c27b-115">Project references make external objects, such as objects in assemblies, available to Visual Basic projects.</span></span> <span data-ttu-id="1c27b-116">`Imports`語句是用來簡化對專案參考的存取，但不提供這些物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="1c27b-116">The `Imports` statement is used to simplify access to project references, but does not provide access to these objects.</span></span> <span data-ttu-id="1c27b-117">`Declare`語句是用來在動態連結程式庫 (DLL) 中宣告外部程式的參考。</span><span class="sxs-lookup"><span data-stu-id="1c27b-117">The `Declare` statement is used to declare a reference to an external procedure in a dynamic-link library (DLL).</span></span>  
  
## <a name="using-aliases-with-the-imports-statement"></a><span data-ttu-id="1c27b-118">使用別名搭配 Imports 語句</span><span class="sxs-lookup"><span data-stu-id="1c27b-118">Using Aliases with the Imports Statement</span></span>  

 <span data-ttu-id="1c27b-119">`Imports`語句可讓您輕鬆地存取類別的方法，而不需要明確地輸入參考的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="1c27b-119">The `Imports` statement makes it easier to access methods of classes by eliminating the need to explicitly type the fully qualified names of references.</span></span> <span data-ttu-id="1c27b-120">別名可讓您將易記名稱指派給命名空間的其中一個部分。</span><span class="sxs-lookup"><span data-stu-id="1c27b-120">Aliases let you assign a friendlier name to just one part of a namespace.</span></span> <span data-ttu-id="1c27b-121">例如，在多行上顯示單一文字片段的回車/換行字元，是 <xref:Microsoft.VisualBasic.ControlChars> 命名空間中模組的一部分 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1c27b-121">For example, the carriage return/line feed sequence that causes a single piece of text to be displayed on multiple lines is part of the <xref:Microsoft.VisualBasic.ControlChars> module in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1c27b-122">若要在沒有別名的程式中使用這個常數，您必須輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="1c27b-122">To use this constant in a program without an alias, you would need to type the following code:</span></span>  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 <span data-ttu-id="1c27b-123">`Imports` 語句一律必須是緊接在模組中任何語句之後的第一行 `Option` 。</span><span class="sxs-lookup"><span data-stu-id="1c27b-123">`Imports` statements must always be the first lines immediately following any `Option` statements in a module.</span></span> <span data-ttu-id="1c27b-124">下列程式碼片段顯示如何匯入並指派別名給 <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> 模組：</span><span class="sxs-lookup"><span data-stu-id="1c27b-124">The following code fragment shows how to import and assign an alias to the <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> module:</span></span>  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 <span data-ttu-id="1c27b-125">未來此命名空間的參考可能會變得很短：</span><span class="sxs-lookup"><span data-stu-id="1c27b-125">Future references to this namespace can be considerably shorter:</span></span>  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 <span data-ttu-id="1c27b-126">如果 `Imports` 語句不包含別名名稱，則在匯入的命名空間內定義的元素可在模組中使用，而不需限定。</span><span class="sxs-lookup"><span data-stu-id="1c27b-126">If an `Imports` statement does not include an alias name, elements defined within the imported namespace can be used in the module without qualification.</span></span> <span data-ttu-id="1c27b-127">如果指定了別名名稱，則必須將其當做該命名空間內所含名稱的辨識符號使用。</span><span class="sxs-lookup"><span data-stu-id="1c27b-127">If the alias name is specified, it must be used as a qualifier for names contained within that namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c27b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c27b-128">See also</span></span>

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [<span data-ttu-id="1c27b-129">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="1c27b-129">Namespaces in Visual Basic</span></span>](namespaces.md)
- [<span data-ttu-id="1c27b-130">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="1c27b-130">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="1c27b-131">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="1c27b-131">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
