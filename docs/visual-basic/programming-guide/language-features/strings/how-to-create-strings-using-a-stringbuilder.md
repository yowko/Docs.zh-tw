---
title: "如何：在 Visual Basic 中使用 StringBuilder 建立字串"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9def5da754d9075a8b498ac80e624caae5c97b96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="7dfb4-102">如何：在 Visual Basic 中使用 StringBuilder 建立字串</span><span class="sxs-lookup"><span data-stu-id="7dfb4-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="7dfb4-103">這個範例會建構從許多較小的字串使用長字串<xref:System.Text.StringBuilder>類別。</span><span class="sxs-lookup"><span data-stu-id="7dfb4-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="7dfb4-104"><xref:System.Text.StringBuilder>類別是更有效率`&=`運算子來串連多個字串。</span><span class="sxs-lookup"><span data-stu-id="7dfb4-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dfb4-105">範例</span><span class="sxs-lookup"><span data-stu-id="7dfb4-105">Example</span></span>  
 <span data-ttu-id="7dfb4-106">下列範例會建立的執行個體<xref:System.Text.StringBuilder>類別，將 1000 的字串附加至該執行個體，，，然後傳回其字串表示。</span><span class="sxs-lookup"><span data-stu-id="7dfb4-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7dfb4-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="7dfb4-107">See Also</span></span>  
 [<span data-ttu-id="7dfb4-108">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="7dfb4-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="7dfb4-109">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="7dfb4-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="7dfb4-110">字串</span><span class="sxs-lookup"><span data-stu-id="7dfb4-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="7dfb4-111">建立新字串</span><span class="sxs-lookup"><span data-stu-id="7dfb4-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="7dfb4-112">操作字串</span><span class="sxs-lookup"><span data-stu-id="7dfb4-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 [<span data-ttu-id="7dfb4-113">字串的範例</span><span class="sxs-lookup"><span data-stu-id="7dfb4-113">Strings Sample</span></span>](http://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02)
