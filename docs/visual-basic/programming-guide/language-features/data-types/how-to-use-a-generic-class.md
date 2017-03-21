---
title: "如何︰ 使用泛型類別 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- type parameters, defining
- data type arguments, defining
- arguments [Visual Basic], data types
- Of keyword, using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters, type
- types [Visual Basic], generic
- parameters, generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters, data type
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eeb55be1c368e9ca80ab94de814a5e2ba9bc9f1f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-a-generic-class-visual-basic"></a>如何：使用泛型類別 (Visual Basic)
採用 *「類型參數」* (type parameter) 的類別稱為 *「泛型類別」*(generic class)。 如果您使用泛型類別，則可以透過它產生 *「建構類別」* (constructed class)，方法是提供所有這些參數的 *「類型引數」* (type argument)。 您接著可以宣告所建構類別類型的變數，而且可以建立所建構類別的執行個體，並將它指派給該變數。  
  
 除了類別之外，您還可以定義和使用泛型結構、介面、程序和委派。  
  
 下列程序會採用 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 中所定義的泛型類別，並透過它建立執行個體。  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>使用採用類型參數的類別  
  
1.  在原始程式檔的開頭，包括[Imports 陳述式 （.NET 命名空間和類型）](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)匯入<xref:System.Collections.Generic?displayProperty=fullName>命名空間。</xref:System.Collections.Generic?displayProperty=fullName> 這可讓您參考的<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>類別，而不必完整限定它從其他佇列類別，例如<xref:System.Collections.Queue?displayProperty=fullName>。</xref:System.Collections.Queue?displayProperty=fullName>區別</xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
2.  以一般方式建立物件，但是在類別名稱之後立即新增 `(Of` `type``)` 。  
  
     下列範例會使用相同的類別 (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) 來建立兩個佇列物件的不同資料類型的項目。</xref:System.Collections.Generic.Queue%601?displayProperty=fullName> 它會將項目新增至每個佇列的結尾，然後移除，並顯示每個佇列前端的項目。  
  
     [!code-vb[VbVbalrDataTypes #&9;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [如何：定義可以在不同資料型別上提供完全相同功能的類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [迭代器](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
