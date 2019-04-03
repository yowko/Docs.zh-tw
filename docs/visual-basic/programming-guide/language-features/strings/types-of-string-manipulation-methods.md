---
title: Visual Basic 中字串管理方法的類型
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 44eb101ebdfeb316958a659107190ef1fc84df44
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821149"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="ffbc6-102">Visual Basic 中字串管理方法的類型</span><span class="sxs-lookup"><span data-stu-id="ffbc6-102">Types of String Manipulation Methods in Visual Basic</span></span>
<span data-ttu-id="ffbc6-103">有數個不同的方式，來分析及管理您的字串。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="ffbc6-104">某些方法屬於 Visual Basic 語言的有些則是內在`String`類別。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="ffbc6-105">Visual Basic 語言和.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ffbc6-105">Visual Basic Language and the .NET Framework</span></span>  
 <span data-ttu-id="ffbc6-106">做為語言的固有的函式會使用 Visual Basic 方法。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="ffbc6-107">它們必須配合您的程式碼中的限定性條件。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="ffbc6-108">下列範例會示範 Visual Basic 字串操作命令的一般用法：</span><span class="sxs-lookup"><span data-stu-id="ffbc6-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="ffbc6-109">在此範例中，`Mid`函式上執行直接運算`aString`並將值指派給`bString`。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="ffbc6-110">如需 Visual Basic 字串操作方法的清單，請參閱 <<c0> [ 字串操作摘要](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="ffbc6-111">共用的方法和執行個體方法</span><span class="sxs-lookup"><span data-stu-id="ffbc6-111">Shared Methods and Instance Methods</span></span>  
 <span data-ttu-id="ffbc6-112">您也可以使用的方法來操作字串`String`類別。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="ffbc6-113">有兩種類型的方法中`String`:*共用*方法並*執行個體*方法。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="ffbc6-114">共用的方法</span><span class="sxs-lookup"><span data-stu-id="ffbc6-114">Shared Methods</span></span>  
 <span data-ttu-id="ffbc6-115">共用的方法是方法，就是源自`String`類別本身，而且不需要運作該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="ffbc6-116">這些方法可以限定的類別名稱 (`String`)，而不是與執行個體`String`類別。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="ffbc6-117">例如: </span><span class="sxs-lookup"><span data-stu-id="ffbc6-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="ffbc6-118">在上述範例中，<xref:System.String.Copy%2A?displayProperty=nameWithType>方法是靜態方法，它就在運算式上的它提供，並將產生的值指派`bString`。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="ffbc6-119">執行個體方法</span><span class="sxs-lookup"><span data-stu-id="ffbc6-119">Instance Methods</span></span>  
 <span data-ttu-id="ffbc6-120">執行個體方法，相較之下，源自於特定執行個體`String`和必須以執行個體名稱加以限定。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="ffbc6-121">例如: </span><span class="sxs-lookup"><span data-stu-id="ffbc6-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="ffbc6-122">在此範例中，<xref:System.String.Substring%2A?displayProperty=nameWithType>方法是一種方法的執行個體`String`(也就是`aString`)。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="ffbc6-123">在執行作業`aString`，並將該值指派`bString`。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="ffbc6-124">如需詳細資訊，請參閱文件<xref:System.String>類別。</span><span class="sxs-lookup"><span data-stu-id="ffbc6-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffbc6-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ffbc6-125">See also</span></span>

- [<span data-ttu-id="ffbc6-126">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="ffbc6-126">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
