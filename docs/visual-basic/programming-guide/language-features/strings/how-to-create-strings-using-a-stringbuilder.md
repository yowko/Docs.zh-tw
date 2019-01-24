---
title: HOW TO：在 Visual Basic 中使用 StringBuilder 建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 84f0f41cf8ee23466d47dae3b1068c3bc5334072
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528442"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="10788-102">HOW TO：在 Visual Basic 中使用 StringBuilder 建立字串</span><span class="sxs-lookup"><span data-stu-id="10788-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="10788-103">此範例會建構從許多較小的字串，使用一長串<xref:System.Text.StringBuilder>類別。</span><span class="sxs-lookup"><span data-stu-id="10788-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="10788-104"><xref:System.Text.StringBuilder>類別的效率高於`&=`將許多字串串連運算子。</span><span class="sxs-lookup"><span data-stu-id="10788-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10788-105">範例</span><span class="sxs-lookup"><span data-stu-id="10788-105">Example</span></span>  
 <span data-ttu-id="10788-106">下列範例建立的執行個體<xref:System.Text.StringBuilder>類別，將 1000 的字串附加至該執行個體，並接著會傳回它的字串表示。</span><span class="sxs-lookup"><span data-stu-id="10788-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="10788-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10788-107">See also</span></span>
- [<span data-ttu-id="10788-108">使用 StringBuilder 類別</span><span class="sxs-lookup"><span data-stu-id="10788-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="10788-109">&= 運算子</span><span class="sxs-lookup"><span data-stu-id="10788-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="10788-110">字串</span><span class="sxs-lookup"><span data-stu-id="10788-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="10788-111">建立新字串</span><span class="sxs-lookup"><span data-stu-id="10788-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="10788-112">操作字串</span><span class="sxs-lookup"><span data-stu-id="10788-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
- <span data-ttu-id="10788-113">[字串範例](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10788-113">[Strings Sample](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))</span></span>
