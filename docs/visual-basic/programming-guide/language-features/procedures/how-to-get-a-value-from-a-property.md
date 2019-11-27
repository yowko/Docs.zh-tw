---
title: 如何：取得屬性值
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 85512d4311d3e731a2c4e129d6a01f9b3273b333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339820"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>如何：取得屬性值 (Visual Basic)
您可以藉由在運算式中包含屬性名稱，來抓取屬性的值。  
  
 屬性的 `Get` 程式會抓取值，但您不會依名稱明確地呼叫它。 您可以使用屬性，就像使用變數一樣。 Visual Basic 會呼叫屬性的程式。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>從屬性取得值  
  
1. 在運算式中使用屬性名稱，方法與使用變數名稱的方式相同。 您可以在任何可使用變數或常數的地方使用屬性。  
  
     -或-  
  
     在指派語句中的等號（`=`）後面，使用屬性名稱。  
  
     下列範例會讀取 Visual Basic `Now` 屬性的值，並隱含地呼叫其 `Get` 程式。  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. 如果屬性接受引數，請在屬性名稱後面加上括弧，以括住引數清單。 如果沒有引數，您可以選擇性地省略括弧。  
  
3. 將引數放在括弧內的引數清單中，並以逗號分隔。 請務必以屬性定義對應參數的相同順序來提供引數。  
  
 屬性的值會當做變數或常數來參與運算式，或是儲存在指派語句左側的變數或屬性中。  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Visual Basic 中的屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
