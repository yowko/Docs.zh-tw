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
ms.openlocfilehash: e2e279b2c935dd082cbf832265a8ad09e6dffe9e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351143"
---
# <a name="implements-statement"></a>Implements 陳述式
指定一個或多個介面或介面成員，必須在其出現所在的類別或結構定義中執行。  
  
## <a name="syntax"></a>語法  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>組件  
 `interfacename`  
 必要。 介面，其屬性、程式和事件會由類別或結構中的對應成員來執行。  
  
 `interfacemember`  
 必要。 正在執行之介面的成員。  
  
## <a name="remarks"></a>備註  
 「介面」（interface）是原型的集合，代表介面封裝的成員（屬性、程式和事件）。 介面只包含成員的宣告;類別和結構會執行這些成員。 如需詳細資訊，請參閱 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)中定義的介面的私用 C++ 專屬實作。  
  
 `Implements` 語句必須緊接在 `Class` 或 `Structure` 語句之後。  
  
 當您執行介面時，您必須執行介面中宣告的所有成員。 省略任何成員會被視為語法錯誤。 若要執行個別成員，當您在類別或結構中宣告成員時，可以指定[Implements](../../../visual-basic/language-reference/statements/implements-clause.md)關鍵字（與 `Implements` 語句分開）。 如需詳細資訊，請參閱 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)中定義的介面的私用 C++ 專屬實作。  
  
 類別可以使用屬性和程式的[私](../../../visual-basic/language-reference/modifiers/private.md)用實作為，但只有將實做類別的實例轉換成宣告為介面類別型的變數，才能存取這些成員。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用 `Implements` 語句來執行介面的成員。 它會定義名為 `ICustomerInfo` 的介面，其中包含事件、屬性和程式。 類別 `customerInfo` 會執行介面中定義的所有成員。  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 請注意，類別 `customerInfo` 在不同的源程式碼上使用 `Implements` 語句，表示該類別會執行 `ICustomerInfo` 介面的所有成員。 然後，類別中的每個成員都會使用 `Implements` 關鍵字做為其成員宣告的一部分，以表示它會實作為該介面成員。  
  
## <a name="example"></a>範例  
 下列兩個程式顯示如何使用上述範例中所實的介面。 若要測試執行，請將這些程式新增至您的專案，並呼叫 `testImplements` 程式。  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>請參閱

- [Sub New](../../../visual-basic/language-reference/statements/implements-clause.md)
- [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)
- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
