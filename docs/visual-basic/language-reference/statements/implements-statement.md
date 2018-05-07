---
title: Implements 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 5afc7e4e3a03dfab1288e50e65e5076bdd438f7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="implements-statement"></a>Implements 陳述式
指定一或多個介面，或必須在類別中實作的介面成員或結構定義中的出現。  
  
## <a name="syntax"></a>語法  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>組件  
 `interfacename`  
 必要。 其屬性、 程序和事件會由對應的成員類別或結構中實作介面。  
  
 `interfacemember`  
 必要。 所實作之介面的成員。  
  
## <a name="remarks"></a>備註  
 介面是集合的原型代表成員 （屬性、 程序和事件） 封裝的介面。 介面包含宣告的成員;類別和結構實作這些成員。 如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 `Implements`陳述式必須緊接`Class`或`Structure`陳述式。  
  
 當您實作的介面時，您必須實作介面中宣告的所有成員。 省略任何成員會被視為語法錯誤。 若要實作的個別成員，指定[實作](../../../visual-basic/language-reference/statements/implements-clause.md)關鍵字 (也就是從個別`Implements`陳述式) 當您宣告類別或結構中的成員。 如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 類別可以使用[私人](../../../visual-basic/language-reference/modifiers/private.md)實作的屬性和程序，但這些成員都只能由實作類別的執行個體放入變數宣告為介面的型別轉型存取。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`Implements`陳述式來實作介面的成員。 它會定義名為介面`ICustomerInfo`事件、 屬性，與程序。 類別`customerInfo`實作介面中定義的所有成員。  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 請注意，類別`customerInfo`使用`Implements`陳述式表示類別實作的所有成員的個別的原始程式碼行上`ICustomerInfo`介面。 在類別中的每個成員接著會使用`Implements`關鍵字做為其成員宣告，以表示它會實作該介面成員的一部分。  
  
## <a name="example"></a>範例  
 下列兩個程序顯示如何使用上述範例中實作的介面。 若要測試的實作，將這些程序加入至您的專案，並呼叫`testImplements`程序。  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
