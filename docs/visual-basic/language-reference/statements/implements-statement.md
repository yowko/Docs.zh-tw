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
ms.openlocfilehash: b982057d2094f807b68d5190dfad388fb9a2c65a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873242"
---
# <a name="implements-statement"></a>Implements 陳述式

指定必須在出現之類別或結構定義中實作為的一或多個介面或介面成員。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>組件  

 `interfacename`  
 必要。 介面，其屬性、程式和事件是由類別或結構中的對應成員所執行。  
  
 `interfacemember`  
 必要。 正在執行之介面的成員。  
  
## <a name="remarks"></a>備註  

 「介面」（interface）是代表介面所封裝)  (屬性、程式和事件之成員的原型集合。 介面只包含成員的宣告;類別和結構會執行這些成員。 如需詳細資訊，請參閱[介面](../../programming-guide/language-features/interfaces/index.md)。  
  
 `Implements`語句必須緊接在 `Class` 或語句後面 `Structure` 。  
  
 當您執行介面時，您必須執行介面中宣告的所有成員。 省略任何成員都會被視為語法錯誤。 若要執行個別成員，請指定 [Implements](implements-clause.md) 關鍵字 (`Implements` 當您在類別或結構中宣告成員時，會與語句) 分開。 如需詳細資訊，請參閱[介面](../../programming-guide/language-features/interfaces/index.md)。  
  
 類別可以使用屬性和程式的 [私](../modifiers/private.md) 用實作為，但這些成員只能藉由將實類別的實例轉換為宣告為介面型別的變數來存取。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用 `Implements` 語句來執行介面的成員。 它會定義一個名為的介面，該介面 `ICustomerInfo` 具有事件、屬性和程式。 類別會執行 `customerInfo` 介面中定義的所有成員。  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 請注意，類別會 `customerInfo` `Implements` 在個別的源程式碼上使用語句，以指出該類別會實作為介面的所有成員 `ICustomerInfo` 。 然後，類別中的每個成員 `Implements` 都會使用關鍵字做為其成員宣告的一部分，以表示它會執行該介面成員。  
  
## <a name="example"></a>範例  

 下列兩個程式示範如何使用在上述範例中所執行的介面。 若要測試執行，請將這些程式加入至您的專案，並呼叫程式 `testImplements` 。  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>另請參閱

- [實作](implements-clause.md)
- [Interface 陳述式](interface-statement.md)
- [介面](../../programming-guide/language-features/interfaces/index.md)
