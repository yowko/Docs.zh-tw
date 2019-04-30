---
title: HOW TO：在 Visual Basic 中使用 StringBuilder 建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 00fefcc138164288d872cd339f165dc6ffc0131a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032120"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="b6739-102">HOW TO：在 Visual Basic 中使用 StringBuilder 建立字串</span><span class="sxs-lookup"><span data-stu-id="b6739-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="b6739-103">此範例會建構從許多較小的字串，使用一長串<xref:System.Text.StringBuilder>類別。</span><span class="sxs-lookup"><span data-stu-id="b6739-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="b6739-104"><xref:System.Text.StringBuilder>類別的效率高於`&=`將許多字串串連運算子。</span><span class="sxs-lookup"><span data-stu-id="b6739-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6739-105">範例</span><span class="sxs-lookup"><span data-stu-id="b6739-105">Example</span></span>  
 <span data-ttu-id="b6739-106">下列範例建立的執行個體<xref:System.Text.StringBuilder>類別，將 1000 的字串附加至該執行個體，並接著會傳回它的字串表示。</span><span class="sxs-lookup"><span data-stu-id="b6739-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="b6739-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6739-107">See also</span></span>

- [<span data-ttu-id="b6739-108">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="b6739-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="b6739-109">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="b6739-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="b6739-110">字串</span><span class="sxs-lookup"><span data-stu-id="b6739-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="b6739-111">建立新字串</span><span class="sxs-lookup"><span data-stu-id="b6739-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="b6739-112">操作字串</span><span class="sxs-lookup"><span data-stu-id="b6739-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
