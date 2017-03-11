---
title: "如何：使用泛型類別 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "型別參數, 定義"
  - "資料類型引數, 定義"
  - "引數 [Visual Basic], 資料類型"
  - "Of 關鍵字, 使用"
  - "泛型參數"
  - "資料型別參數"
  - "泛型 [Visual Basic], 關於泛型"
  - "資料類型 [Visual Basic], 作為參數"
  - "資料類型 [Visual Basic], 作為引數"
  - "參數, 類型"
  - "類型 [Visual Basic], 泛型"
  - "參數, 泛型"
  - "泛型 [Visual Basic], 建立泛型類型"
  - "資料型別引數"
  - "參數, 資料類型"
  - "資料型別參數, 定義"
  - "類型引數, 定義"
  - "引數 [Visual Basic], 類型"
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# 如何：使用泛型類別 (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

採用 *「類型參數」* (type parameter) 的類別稱為 *「泛型類別」*(generic class)。 如果您使用泛型類別，則可以透過它產生 *「建構類別」* (constructed class)，方法是提供所有這些參數的 *「類型引數」* (type argument)。 您接著可以宣告所建構類別類型的變數，而且可以建立所建構類別的執行個體，並將它指派給該變數。  
  
 除了類別之外，您還可以定義和使用泛型結構、介面、程序和委派。  
  
 下列程序會採用 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] 中所定義的泛型類別，並透過它建立執行個體。  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>使用採用類型參數的類別  
  
1.  在您的原始程式檔開頭，包含 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) 以匯入 <xref:System.Collections.Generic?displayProperty=fullName> 命名空間。 這可讓您參考 <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> 類別，而不需要完整限定它就區分它與其他佇列類別 (例如 <xref:System.Collections.Queue?displayProperty=fullName>)。  
  
2.  以一般方式建立物件，但是在類別名稱之後立即新增 `(Of` `type``)` 。  
  
     下列範例使用相同的類別 (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) 來建立保留不同資料類型之項目的兩個佇列物件。 它會將項目新增至每個佇列的結尾，然後移除，並顯示每個佇列前端的項目。  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [如何：定義可以在不同資料型別上提供完全相同功能的類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [迭代器](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)