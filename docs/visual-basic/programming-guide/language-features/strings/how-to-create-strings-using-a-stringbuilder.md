---
title: 如何：在 Visual Basic 中使用 StringBuilder 建立字串
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0e15c7df07822ee104a88525c209768c05470e3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="90fa1-102">如何：在 Visual Basic 中使用 StringBuilder 建立字串</span><span class="sxs-lookup"><span data-stu-id="90fa1-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="90fa1-103">這個範例會建構從許多較小的字串使用長字串<xref:System.Text.StringBuilder>類別。</span><span class="sxs-lookup"><span data-stu-id="90fa1-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="90fa1-104"><xref:System.Text.StringBuilder>類別是更有效率`&=`運算子來串連多個字串。</span><span class="sxs-lookup"><span data-stu-id="90fa1-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90fa1-105">範例</span><span class="sxs-lookup"><span data-stu-id="90fa1-105">Example</span></span>  
 <span data-ttu-id="90fa1-106">下列範例會建立的執行個體<xref:System.Text.StringBuilder>類別，將 1000 的字串附加至該執行個體，，，然後傳回其字串表示。</span><span class="sxs-lookup"><span data-stu-id="90fa1-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="90fa1-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90fa1-107">See Also</span></span>  
 [<span data-ttu-id="90fa1-108">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="90fa1-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)  
 [<span data-ttu-id="90fa1-109">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="90fa1-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="90fa1-110">字串</span><span class="sxs-lookup"><span data-stu-id="90fa1-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [<span data-ttu-id="90fa1-111">建立新字串</span><span class="sxs-lookup"><span data-stu-id="90fa1-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)  
 [<span data-ttu-id="90fa1-112">操作字串</span><span class="sxs-lookup"><span data-stu-id="90fa1-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)  
 <span data-ttu-id="90fa1-113">[字串的範例](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="90fa1-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
