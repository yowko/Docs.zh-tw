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
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>HOW TO：在 Visual Basic 中使用 StringBuilder 建立字串
此範例會建構從許多較小的字串，使用一長串<xref:System.Text.StringBuilder>類別。 <xref:System.Text.StringBuilder>類別的效率高於`&=`將許多字串串連運算子。  
  
## <a name="example"></a>範例  
 下列範例建立的執行個體<xref:System.Text.StringBuilder>類別，將 1000 的字串附加至該執行個體，並接著會傳回它的字串表示。  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [使用 StringBuilder 類別](../../../../standard/base-types/stringbuilder.md)
- [&= 運算子](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [建立新字串](../../../../standard/base-types/creating-new.md)
- [操作字串](../../../../standard/base-types/manipulating-strings.md)
- [字串範例](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))
