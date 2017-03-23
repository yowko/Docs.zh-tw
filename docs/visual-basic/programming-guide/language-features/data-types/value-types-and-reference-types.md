---
title: "實值型別和參考型別 |Microsoft 文件"
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
- reference data types
- reference types
- value types
- value data types
- types [Visual Basic]
- data types [Visual Basic], value types
- data types [Visual Basic], reference types
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: de8016b4b2a5550b32373a41c89a484fa996c596
ms.lasthandoff: 03/13/2017

---
# <a name="value-types-and-reference-types"></a>Value Types and Reference Types
在 Visual Basic 中的資料型別會實作其分類為基礎。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]可依特定類型的變數是否儲存自己的資料或資料指標分類資料型別。 如果它自己的資料會儲存為*實值型別*; 如果它是的記憶體中其他位置的資料會保留指標*參考型別*。  
  
## <a name="value-types"></a>實值類型  
 資料型別是*實值型別*它存放在自己的記憶體配置中的資料。 實值型別包括︰  
  
-   所有的數值資料類型  
  
-   `Boolean`、`Char` 和 `Date`  
  
-   所有的結構，即使它們的成員是參考型別  
  
-   列舉型別，因為其基礎型別永遠為`SByte`， `Short`， `Integer`， `Long`， `Byte`， `UShort`， `UInteger`，或`ULong`  
  
 每個結構是實值型別，即使它包含參考型別成員。 基於這個理由，值型別，例如`Char`和`Integer`由.NET Framework 結構。  
  
 您可以使用的保留的關鍵字，例如，宣告實值型別`Decimal`。 您也可以使用`New`關鍵字初始化實值型別。 這是特別有用，如果型別參數的建構函式。 這個範例是<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>建構函式，會建置新`Decimal`值從提供的部分。</xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29>  
  
## <a name="reference-types"></a>參考類型  
 A*參考型別*包含保存資料的另一個記憶體位置的指標。 參考型別包括︰  
  
-   `String`  
  
-   所有的陣列，即使其元素為實值類型  
  
-   類別類型例如<xref:System.Windows.Forms.Form></xref:System.Windows.Forms.Form>  
  
-   委派  
  
 類別是*參考型別*。 基於這個理由，參考型別例如`Object`和`String`支援[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]類別。 請注意每個陣列是參考型別，即使其成員都是實值型別。  
  
 由於每個參考型別代表基礎的.NET Framework 類別，您必須使用[New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)關鍵字時將它初始化。 下列陳述式中初始化陣列。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## <a name="elements-that-are-not-types"></a>不是類型的項目  
 下列的程式設計項目不會限定為型別，因為您無法將它們指定為資料類型的宣告的項目︰  
  
-   命名空間  
  
-   模組  
  
-   事件  
  
-   屬性和程序  
  
-   變數、 常數和欄位  
  
## <a name="working-with-the-object-data-type"></a>使用物件資料類型  
 您可以將參考類型或實值型別指派給變數`Object`資料型別。 `Object`變數一律會保留指標的資料，永遠不會將資料本身。 不過，如果您指派的值型別`Object`變數時，它就會當做它會保留它自己的資料。 如需詳細資訊，請參閱[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 您可以找出是否`Object`變數做為參考類型或實值型別傳遞至<xref:Microsoft.VisualBasic.Information.IsReference%2A>方法中的<xref:Microsoft.VisualBasic.Information>類別<xref:Microsoft.VisualBasic?displayProperty=fullName>命名空間。</xref:Microsoft.VisualBasic?displayProperty=fullName> </xref:Microsoft.VisualBasic.Information> </xref:Microsoft.VisualBasic.Information.IsReference%2A> <xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>傳回`True`如果內容`Object`變數代表參考型別。</xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>另請參閱  
 [可為 null 的實值型別](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
