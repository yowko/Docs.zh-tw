---
title: 字串操作方法的類型
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: c44f02880858b8a9fc1f0e70c3226623d05baa3a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072466"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a><span data-ttu-id="337d7-102">Visual Basic 中字串管理方法的類型</span><span class="sxs-lookup"><span data-stu-id="337d7-102">Types of String Manipulation Methods in Visual Basic</span></span>

<span data-ttu-id="337d7-103">有幾種不同的方式可以分析和操作您的字串。</span><span class="sxs-lookup"><span data-stu-id="337d7-103">There are several different ways to analyze and manipulate your strings.</span></span> <span data-ttu-id="337d7-104">某些方法是 Visual Basic 語言的一部分，而其他方法則是類別中的固有部分 `String` 。</span><span class="sxs-lookup"><span data-stu-id="337d7-104">Some of the methods are a part of the Visual Basic language, and others are inherent in the `String` class.</span></span>  
  
## <a name="visual-basic-language-and-the-net-framework"></a><span data-ttu-id="337d7-105">Visual Basic 語言和 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="337d7-105">Visual Basic Language and the .NET Framework</span></span>  

 <span data-ttu-id="337d7-106">Visual Basic 方法會當做語言的固有函式使用。</span><span class="sxs-lookup"><span data-stu-id="337d7-106">Visual Basic methods are used as inherent functions of the language.</span></span> <span data-ttu-id="337d7-107">您可以使用它們，而不需要在程式碼中限定。</span><span class="sxs-lookup"><span data-stu-id="337d7-107">They may be used without qualification in your code.</span></span> <span data-ttu-id="337d7-108">下列範例顯示 Visual Basic 字串操作命令的一般用法：</span><span class="sxs-lookup"><span data-stu-id="337d7-108">The following example shows typical use of a Visual Basic string-manipulation command:</span></span>  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 <span data-ttu-id="337d7-109">在此範例中，此函式會 `Mid` 在上執行直接操作 `aString` ，並將值指派給 `bString` 。</span><span class="sxs-lookup"><span data-stu-id="337d7-109">In this example, the `Mid` function performs a direct operation on `aString` and assigns the value to `bString`.</span></span>  
  
 <span data-ttu-id="337d7-110">如需 Visual Basic 字串操作方法的清單，請參閱 [字串操作摘要](../../../language-reference/keywords/string-manipulation-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="337d7-110">For a list of Visual Basic string manipulation methods, see [String Manipulation Summary](../../../language-reference/keywords/string-manipulation-summary.md).</span></span>  
  
### <a name="shared-methods-and-instance-methods"></a><span data-ttu-id="337d7-111">共用方法與實例方法</span><span class="sxs-lookup"><span data-stu-id="337d7-111">Shared Methods and Instance Methods</span></span>  

 <span data-ttu-id="337d7-112">您也可以使用類別的方法來操作字串 `String` 。</span><span class="sxs-lookup"><span data-stu-id="337d7-112">You can also manipulate strings with the methods of the `String` class.</span></span> <span data-ttu-id="337d7-113">中有兩種類型的方法 `String` ： *共用* 方法和 *實例* 方法。</span><span class="sxs-lookup"><span data-stu-id="337d7-113">There are two types of methods in `String`: *shared* methods and *instance* methods.</span></span>  
  
#### <a name="shared-methods"></a><span data-ttu-id="337d7-114">共用方法</span><span class="sxs-lookup"><span data-stu-id="337d7-114">Shared Methods</span></span>  

 <span data-ttu-id="337d7-115">共用方法是源自類別本身的方法，不 `String` 需要該類別的實例就能運作。</span><span class="sxs-lookup"><span data-stu-id="337d7-115">A shared method is a method that stems from the `String` class itself and does not require an instance of that class to work.</span></span> <span data-ttu-id="337d7-116">您可以使用類別的名稱來限定這些方法 (`String`) ，而不是類別的實例 `String` 。</span><span class="sxs-lookup"><span data-stu-id="337d7-116">These methods can be qualified with the name of the class (`String`) rather than with an instance of the `String` class.</span></span> <span data-ttu-id="337d7-117">例如：</span><span class="sxs-lookup"><span data-stu-id="337d7-117">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 <span data-ttu-id="337d7-118">在上述範例中， <xref:System.String.Copy%2A?displayProperty=nameWithType> 方法是靜態方法，它會在其所指定的運算式上運作，並將產生的值指派給 `bString` 。</span><span class="sxs-lookup"><span data-stu-id="337d7-118">In the preceding example, the <xref:System.String.Copy%2A?displayProperty=nameWithType> method is a static method, which acts upon an expression it is given and assigns the resulting value to `bString`.</span></span>  
  
#### <a name="instance-methods"></a><span data-ttu-id="337d7-119">實例方法</span><span class="sxs-lookup"><span data-stu-id="337d7-119">Instance Methods</span></span>  

 <span data-ttu-id="337d7-120">相反地，實例方法是來自特定的實例， `String` 而且必須使用實例名稱來限定。</span><span class="sxs-lookup"><span data-stu-id="337d7-120">Instance methods, by contrast, stem from a particular instance of `String` and must be qualified with the instance name.</span></span> <span data-ttu-id="337d7-121">例如：</span><span class="sxs-lookup"><span data-stu-id="337d7-121">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 <span data-ttu-id="337d7-122">在此範例中， <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法是 (實例的方法 `String` ，也就是 `aString`) 。</span><span class="sxs-lookup"><span data-stu-id="337d7-122">In this example, the <xref:System.String.Substring%2A?displayProperty=nameWithType> method is a method of the instance of `String` (that is, `aString`).</span></span> <span data-ttu-id="337d7-123">它會對執行運算 `aString` ，並將該值指派給 `bString` 。</span><span class="sxs-lookup"><span data-stu-id="337d7-123">It performs an operation on `aString` and assigns that value to `bString`.</span></span>  
  
 <span data-ttu-id="337d7-124">如需詳細資訊，請參閱類別的檔 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="337d7-124">For more information, see the documentation for the <xref:System.String> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="337d7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="337d7-125">See also</span></span>

- [<span data-ttu-id="337d7-126">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="337d7-126">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
