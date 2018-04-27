---
title: Visual Basic 中字串管理方法的類型
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3677c8a23e956716af4357fe79041fc96f4014f2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="5b3cb-102">Visual Basic 中字串管理方法的類型</span><span class="sxs-lookup"><span data-stu-id="5b3cb-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="5b3cb-103">有幾種不同方式來分析和操作字串。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="5b3cb-104">某些方法屬於的 Visual Basic 語言，而其他可能是固有`String`類別。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="5b3cb-105">Visual Basic 語言和.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5b3cb-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="5b3cb-106">做為語言的固有函式會使用 Visual Basic 方法。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="5b3cb-107">它們可能使用不需在程式碼中的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="5b3cb-108">下列範例會示範 Visual Basic 字串操作命令的一般用法：</span><span class="sxs-lookup"><span data-stu-id="5b3cb-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 <span data-ttu-id="5b3cb-109">在此範例中，`Mid`函式會直接操作執行上`aString`和指派值`bString`。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="5b3cb-110">如需 Visual Basic 字串操作方法的清單，請參閱[字串操作摘要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="5b3cb-111">共用的方法和執行個體方法</span><span class="sxs-lookup"><span data-stu-id="5b3cb-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="5b3cb-112">您也可以使用字串操作的方法與`String`類別。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="5b3cb-113">有兩種類型的方法中`String`:*共用*方法和*執行個體*方法。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="5b3cb-114">共用的方法</span><span class="sxs-lookup"><span data-stu-id="5b3cb-114">Shared Methods</span></span>  
 <span data-ttu-id="5b3cb-115">共用的方法是源自於方法`String`類別本身，而且不需要用於該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="5b3cb-116">這些方法可以限定的類別名稱 (`String`)，而非執行個體與`String`類別。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="5b3cb-117">例如: </span><span class="sxs-lookup"><span data-stu-id="5b3cb-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 <span data-ttu-id="5b3cb-118">在上述範例中，<xref:System.String.Copy%2A?displayProperty=nameWithType>方法是靜態方法，在運算式上的哪些做它指定，並將結果指派至`bString`。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="5b3cb-119">執行個體方法</span><span class="sxs-lookup"><span data-stu-id="5b3cb-119">Instance Methods</span></span>  
 <span data-ttu-id="5b3cb-120">執行個體方法，相反地，源自於特定的執行個體`String`而且必須具有執行個體名稱限定。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="5b3cb-121">例如: </span><span class="sxs-lookup"><span data-stu-id="5b3cb-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 <span data-ttu-id="5b3cb-122">在此範例中，<xref:System.String.Substring%2A?displayProperty=nameWithType>方法是一種方法的執行個體`String`(也就是`aString`)。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="5b3cb-123">在執行作業`aString`，並將該值指派`bString`。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="5b3cb-124">如需詳細資訊，請參閱文件<xref:System.String>類別。</span><span class="sxs-lookup"><span data-stu-id="5b3cb-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3cb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b3cb-125">See Also</span></span>  
 [<span data-ttu-id="5b3cb-126">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="5b3cb-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
