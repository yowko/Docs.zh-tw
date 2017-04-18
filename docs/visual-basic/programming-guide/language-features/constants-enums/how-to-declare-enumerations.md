---
title: "如何︰ 宣告列舉 (Visual Basic) |Microsoft 文件"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 8ff8bf2df39bed0597740bcda968283ec854f447
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a>如何：宣告列舉 (Visual Basic)
建立列舉型別與`Enum`類別或模組的陳述式的宣告區段中。 您無法宣告列舉型別方法內。 若要指定適當的存取層級，請使用`Private`， `Protected`， `Friend`，或`Public`。  
  
 `Enum`型別具有名稱、 基礎型別，以及一組欄位，各代表一個常數。 名稱必須是有效[!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]限定詞。 基礎型別必須是整數類型的其中一個 —`Byte`， `Short`，`Long`或`Integer`。 `Integer` 是預設值。 列舉型別一律強型別，並不能互換使用整數的數字類型。  
  
 列舉型別不能有浮點值。 如果列舉型別指派的浮點值`Option Strict On`，造成編譯器錯誤。 如果`Option Strict`是`Off`，值會自動轉換為`Enum`型別。  
  
 如需名稱及如何使用`Imports`陳述式，讓名稱限定不必要的請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
### <a name="to-declare-an-enumeration"></a>若要宣告列舉類型  
  
1.  撰寫包含程式碼存取層級宣告`Enum`關鍵字，且有效的名稱，如下列範例中，其中每個宣告不同`Enum`。  
  
     [!code-vb[VbEnumsTask #&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  列舉中定義常數。 根據預設，列舉型別的第一個常數會初始化為`0`，而之後的常數會初始化為值&1; 的上一個常數。 例如，以下列舉`Days`，包含名為常數`Sunday`值`0`，名為常數`Monday`值`1`，名為常數`Tuesday`值是`2`，依此類推。  
  
     [!code-vb[VbEnumsTask #&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  您可以使用在指派陳述式明確地指派列舉型別常數的值。 您可以指派任何整數值，包括負數。 例如，您可以常數的值小於零來表示錯誤狀況。 在下列的列舉常數`Invalid`已明確指派值`–1`，和常數`Sunday`會指派值`0`。 因為它是列舉型別，第一個常數`Saturday`也會初始化為值`0`。 值`Monday`是`1`(的值大於`Sunday`); 的值`Tuesday`是`2`，依此類推。  
  
     [!code-vb[VbEnumsTask #&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>若要宣告明確的型別為列舉型別  
  
-   使用指定的列舉類型`As`子句，如下列範例所示。  
  
     [!code-vb[VbEnumsTask #&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [如何︰ 參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [如何︰ 逐一查看在 Visual Basic 中列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [如何︰ 決定與列舉值關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [何時使用列舉型別](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [常數的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)
