---
title: HOW TO：建立屬性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: 91f34de36e88724ccab21097bf54a4604f7eee37
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306712"
---
# <a name="how-to-create-a-property-visual-basic"></a>HOW TO：建立屬性 (Visual Basic)
您將屬性定義之間`Property`陳述式和`End Property`陳述式。 您在此定義中定義`Get`程序，`Set`程序，或兩者。 所有屬性的程式碼位於內這些程序。  
  
 `Get`程序會擷取屬性的值，而`Set`程序儲存值。 如果您想要讀取/寫入存取的屬性，您必須定義兩個程序。 唯讀屬性，您只會定義`Get`，和唯寫屬性，您只會定義`Set`。  
  
### <a name="to-create-a-property"></a>若要建立屬性  
  
1. 之外任何屬性或程序，使用[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)，後面接著`End Property`陳述式。  
  
2. 如果屬性不接受參數，請依照下列`Property`關鍵字的程序中，則參數清單括號括住名稱。  
  
3. 括號後面`As`子句來指定屬性的值的資料類型。 您必須指定資料類型，即使是針對唯寫屬性。  
  
4. 新增`Get`和`Set`程序，適當地。 請參閱下列指示。  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>若要建立 Get 的程序擷取的屬性值  
  
1. 之間`Property`並`End Property`陳述式，撰寫[Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)，後面接著`End Get`陳述式。 您不需要定義任何參數`Get`程序。  
  
2. 將程式碼陳述式，來擷取屬性的值之間放`Get`和`End Get`陳述式。 此程式碼可以包含其他計算和資料操作，除了產生，並傳回屬性的值。  
  
3. 使用`Return`屬性的值傳回至呼叫端程式碼的陳述式。  
  
 您必須撰寫`Get`讀 / 寫屬性和唯讀屬性的程序。 您必須定義`Get`唯寫屬性的程序。  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>若要建立的設定程序寫入屬性的值  
  
1. 之間`Property`並`End Property`陳述式，撰寫[Set 陳述式](../../../../visual-basic/language-reference/statements/set-statement.md)，後面接著`End Set`陳述式。  
  
2. 在 `Set`陳述式，請依照下列`Set`使用的參數清單括號括住關鍵字。 這個參數清單必須包含至少一個值參數呼叫的程式碼所傳遞的值。 此值參數的預設名稱是`Value`，但如果適用的話，您可以使用不同的名稱。 Value 參數必須有相同的資料類型與屬性本身。  
  
3. 將程式碼陳述式，將值儲存在屬性之間`Set`和`End Set`陳述式。 此程式碼可以包含其他計算和資料操作，除了驗證和儲存屬性的值。  
  
4. 您可以使用 value 參數來接受呼叫的程式碼所提供的值。 您可以直接在指派陳述式中儲存此值或計算儲存的內部值的運算式中使用。  
  
 您必須撰寫`Set`讀 / 寫屬性和唯寫屬性的程序。 您必須定義`Set`唯讀屬性的程序。  
  
## <a name="example"></a>範例  
 下列範例會建立將完整的名稱儲存為兩個組成的名稱、 名字和姓氏的讀取/寫入屬性。 當呼叫端程式碼的讀取`fullName`，則`Get`程序結合了兩個組成的名稱，並傳回的完整名稱。 當呼叫端程式碼會指派新的完整名稱，`Set`程序會嘗試將它分成兩個組成的名稱。 如果找不到一個空格，它會儲存它做為第一個名稱。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 下列範例示範一般呼叫屬性程序的`fullName`。 第一次呼叫設定屬性值，第二個呼叫會擷取它。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Visual Basic 中屬性和變數的差別](./differences-between-properties-and-variables.md)
- [HOW TO：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [HOW TO：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [HOW TO：宣告，並在 Visual Basic 中呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [HOW TO：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [HOW TO：取得屬性值](./how-to-get-a-value-from-a-property.md)
