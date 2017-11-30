---
title: "如何：建立屬性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d140e6a10061f7fabe3d12c6cce5d0c201e103d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-property-visual-basic"></a>如何：建立屬性 (Visual Basic)
您將屬性定義之間`Property`陳述式和`End Property`陳述式。 在您定義這個定義內`Get`程序，`Set`程序，或兩者。 所有屬性的程式碼位於這些程序內。  
  
 `Get`程序會擷取屬性值和`Set`程序儲存值。 如果您想要擁有讀/寫存取的屬性，您必須定義兩個程序。 唯讀屬性，只定義`Get`，並為唯寫屬性，只定義`Set`。  
  
### <a name="to-create-a-property"></a>若要建立屬性  
  
1.  任何屬性或程序中，外部使用[Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)，後面接著`End Property`陳述式。  
  
2.  如果此屬性會採用參數，請遵循`Property`關鍵字的程序，則參數清單括號括住名稱。  
  
3.  括號後面`As`子句來指定屬性值的資料類型。 您必須指定即使的唯寫屬性的資料類型。  
  
4.  新增`Get`和`Set`程序，視需要。 請參閱下列指示。  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>若要建立擷取屬性值的 Get 程序  
  
1.  之間`Property`和`End Property`陳述式中，撰寫[Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)，後面接著`End Get`陳述式。 您不需要定義任何參數`Get`程序。  
  
2.  將程式碼陳述式來擷取屬性的值之間放`Get`和`End Get`陳述式。 此程式碼可包含其他計算和資料操作，除了產生並傳回屬性的值。  
  
3.  使用`Return`屬性的值傳回至呼叫的程式碼陳述式。  
  
 您必須撰寫`Get`讀 / 寫屬性和唯讀屬性的程序。 您必須定義`Get`唯寫屬性的程序。  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>若要建立的設定程序，將寫入屬性的值  
  
1.  之間`Property`和`End Property`陳述式中，撰寫[Set 陳述式](../../../../visual-basic/language-reference/statements/set-statement.md)，後面接著`End Set`陳述式。  
  
2.  在`Set`陳述式，請遵循`Set`使用的參數清單括號括住關鍵字。 這個參數清單必須包含至少一個值參數呼叫程式碼傳遞之值。 這個值參數的預設名稱是`Value`，但是如果適當的話，您可以使用不同的名稱。 Value 參數必須有相同的資料類型與屬性本身。  
  
3.  將值儲存之間的屬性中的程式碼陳述式`Set`和`End Set`陳述式。 此程式碼可包含其他計算和資料操作，除了驗證和儲存屬性的值。  
  
4.  您可以使用 value 參數來接受呼叫程式碼所提供的值。 您可以直接在指派陳述式，會將這個值或計算要儲存的內部值的運算式中使用。  
  
 您必須撰寫`Set`讀 / 寫屬性和唯寫屬性的程序。 您必須定義`Set`唯讀屬性的程序。  
  
## <a name="example"></a>範例  
 下列範例會建立將儲存為兩個構成的名稱、 名字和姓氏的完整名稱的讀/寫屬性。 當呼叫程式碼讀取`fullName`、`Get`程序結合了兩個構成的名稱，並傳回的完整名稱。 當呼叫程式碼會指派新的完整名稱，`Set`程序會嘗試將它切為兩個構成的名稱。 如果找不到一個空格，則會儲存它全部都做為第一個名稱。  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 下列範例示範典型的屬性程序呼叫`fullName`。 第一次呼叫設定屬性值，第二個呼叫會擷取它。  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [屬性程序](./property-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)  
 [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)  
 [如何： 宣告及呼叫在 Visual Basic 中的預設屬性](./how-to-declare-and-call-a-default-property.md)  
 [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)  
 [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
