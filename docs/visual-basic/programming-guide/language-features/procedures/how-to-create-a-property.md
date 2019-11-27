---
title: 如何：建立屬性
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349706"
---
# <a name="how-to-create-a-property-visual-basic"></a>如何：建立屬性 (Visual Basic)
您可以將屬性定義括在 `Property` 語句和 `End Property` 語句之間。 在此定義中，您可以定義 `Get` 程式、`Set` 程式或兩者。 所有屬性的程式碼都位於這些程式內。  
  
 `Get` 程式會抓取屬性的值，而 `Set` 程式會儲存值。 如果您想要屬性具有讀取/寫入存取權，您必須定義這兩個程式。 針對唯讀屬性，您只會定義 `Get`，而對於僅限寫入屬性，只會定義 `Set`。  
  
### <a name="to-create-a-property"></a>建立屬性  
  
1. 在任何屬性或程式之外，請使用[Property 語句](../../../../visual-basic/language-reference/statements/property-statement.md)，後面接著 `End Property` 語句。  
  
2. 如果屬性接受參數，請在 `Property` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單。  
  
3. 請在括弧後面加上 `As` 子句，以指定屬性值的資料類型。 您必須指定資料類型，即使是僅限寫入的屬性。  
  
4. 視需要新增 `Get` 和 `Set` 程式。 請參閱下列指示。  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>若要建立可抓取屬性值的 Get 程式  
  
1. 在 `Property` 和 `End Property` 語句之間，撰寫[Get 語句](../../../../visual-basic/language-reference/statements/get-statement.md)，後面接著 `End Get` 語句。 您不需要定義 `Get` 程式的任何參數。  
  
2. 放置程式碼語句，以在 `Get` 和 `End Get` 語句之間抓取屬性的值。 除了產生並傳回屬性的值之外，此程式碼還可以包含其他計算和資料操作。  
  
3. 使用 `Return` 語句，將屬性的值傳回給呼叫程式碼。  
  
 您必須針對讀寫屬性和唯讀屬性撰寫 `Get` 程式。 您不能定義僅限寫入屬性的 `Get` 程式。  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>建立寫入屬性值的 Set 程式  
  
1. 在 `Property` 和 `End Property` 語句之間，撰寫[Set 語句](../../../../visual-basic/language-reference/statements/set-statement.md)，後面接著 `End Set` 語句。  
  
2. 在 `Set` 語句中，以括弧括住參數清單的 `Set` 關鍵字。 此參數清單必須至少包含呼叫端程式碼所傳遞值的值參數。 此值參數的預設名稱為 `Value`，但您可以視需要使用不同的名稱。 Value 參數必須與屬性本身具有相同的資料類型。  
  
3. 將程式碼語句放在 `Set` 和 `End Set` 語句之間的屬性中儲存值。 除了驗證和儲存屬性的值之外，此程式碼還可以包含其他計算和資料操作。  
  
4. 使用 value 參數來接受呼叫程式碼所提供的值。 您可以直接將此值儲存在指派語句中，或在運算式中使用它來計算要儲存的內部值。  
  
 您必須針對讀寫屬性和寫入屬性撰寫 `Set` 程式。 您不能為唯讀屬性定義 `Set` 程式。  
  
## <a name="example"></a>範例  
 下列範例會建立讀取/寫入屬性，將完整名稱儲存為兩個組成名稱、名字和姓氏。 當呼叫程式碼讀取 `fullName`時，`Get` 程式會結合兩個組成名稱，並傳回完整名稱。 當呼叫程式碼指派新的完整名稱時，`Set` 程式會嘗試將它分成兩個組成的名稱。 如果找不到空間，則會將它全部儲存為名字。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 下列範例會顯示 `fullName`的屬性程式的一般呼叫。 第一個呼叫會設定屬性值，而第二個呼叫會將它抓取。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Visual Basic 中的屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
