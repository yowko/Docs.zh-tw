---
title: Implements 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: 805813506b957afb326c71ee4bbb15837726e4e5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425946"
---
# <a name="implements-statement"></a>Implements 陳述式
指定一個或多個介面，或介面成員必須實作在類別中出現的結構定義。  
  
## <a name="syntax"></a>語法  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>組件  
 `interfacename`  
 必要。 其屬性、 程序和事件會由對應的成員，在類別或結構實作介面。  
  
 `interfacemember`  
 必要。 目前正在實作介面成員。  
  
## <a name="remarks"></a>備註  
 介面是集合的原型代表的成員 （屬性、 程序和事件） 封裝的介面。 介面包含宣告的成員;類別和結構實作這些成員。 如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 `Implements`陳述式必須緊接`Class`或`Structure`陳述式。  
  
 當您實作的介面時，您必須實作的介面中宣告的所有成員。 省略任何成員會被視為語法錯誤。 若要實作的個別成員，指定[Implements](../../../visual-basic/language-reference/statements/implements-clause.md)關鍵字 (這是分開`Implements`陳述式) 當您宣告類別或結構中的成員。 如需詳細資訊，請參閱[介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)。  
  
 類別可以使用[私人](../../../visual-basic/language-reference/modifiers/private.md)實作的屬性和程序，但這些成員都只能由實作類別的執行個體放入變數宣告為介面的型別轉型存取。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`Implements`陳述式來實作介面的成員。 它會定義名為的介面`ICustomerInfo`事件、 屬性，與程序。 此類別`customerInfo`實作介面中定義的所有成員。  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 請注意，類別`customerInfo`會使用`Implements`陳述式來指示此類別會實作的所有成員的個別的原始程式碼行上`ICustomerInfo`介面。 接著會使用類別中的每個成員`Implements`關鍵字做為其成員宣告，以表示它會實作該介面成員的一部分。  
  
## <a name="example"></a>範例  
 下列兩個程序顯示如何使用在上述範例中實作的介面。 若要測試實作，將這些程序新增到專案，並呼叫`testImplements`程序。  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
