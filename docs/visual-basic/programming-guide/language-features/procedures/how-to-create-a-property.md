---
title: 如何：建立屬性
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: bd138177d5f4b7ee1eb63833360d227baa54f66d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072739"
---
# <a name="how-to-create-a-property-visual-basic"></a>如何：建立屬性 (Visual Basic)

您可以將屬性定義放在 `Property` 語句和 `End Property` 語句之間。 在此定義中，您可以定義程式 `Get` 、程式 `Set` 或兩者。 所有屬性的程式碼都位於這些程式內。  
  
 此程式會抓取 `Get` 屬性的值，而且此程式會 `Set` 儲存值。 如果您希望屬性具有讀取/寫入存取權，您必須定義這兩個程式。 若為唯讀屬性，您只需定義 `Get` ，而針對僅限寫入屬性，則只會定義 `Set` 。  
  
### <a name="to-create-a-property"></a>建立屬性  
  
1. 在任何屬性或程式之外，請使用 [屬性語句](../../../language-reference/statements/property-statement.md)，後面接著 `End Property` 語句。  
  
2. 如果屬性接受參數，請在 `Property` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單。  
  
3. 在括弧後面加上 `As` 子句，以指定屬性值的資料類型。 您也必須針對僅限寫入屬性指定資料類型。  
  
4. `Get` `Set` 視需要新增和程式。 請參閱下列指示。  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>若要建立抓取屬性值的 Get 程式  
  
1. 在 `Property` 和 `End Property` 語句之間，撰寫 [Get 語句](../../../language-reference/statements/get-statement.md)，後面接著 `End Get` 語句。 您不需要為程式定義任何參數 `Get` 。  
  
2. 放置程式碼語句，以取得和語句之間的屬性 `Get` 值 `End Get` 。 除了產生和傳回屬性的值之外，此程式碼還可以包含其他計算和資料操作。  
  
3. 您 `Return` 可以使用語句，將屬性的值傳回給呼叫程式碼。  
  
 您必須撰寫 `Get` 讀寫屬性的程式，以及唯讀屬性的程式。 您不得 `Get` 為僅限寫入屬性定義程式。  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>若要建立可寫入屬性值的 Set 程式  
  
1. 在 `Property` 和 `End Property` 語句之間，撰寫 [Set 語句](../../../language-reference/statements/set-statement.md)，後面接著 `End Set` 語句。  
  
2. 在 `Set` 語句中，以 `Set` 括弧括住參數清單來執行關鍵字。 此參數清單必須至少包含一個值參數，以供呼叫端程式碼傳遞的值使用。 此值參數的預設名稱是 `Value` ，但您可以視需要使用不同的名稱。 Value 參數的資料類型必須與屬性本身相同。  
  
3. 放置程式碼語句，以將值儲存在和語句之間的屬性 `Set` `End Set` 。 除了驗證和儲存屬性的值之外，此程式碼還可以包含其他計算和資料操作。  
  
4. 使用 value 參數來接受呼叫程式碼所提供的值。 您可以將此值直接儲存在指派語句中，或在運算式中使用它來計算要儲存的內部值。  
  
 您必須撰寫 `Set` 讀寫屬性的程式，以及僅限寫入屬性的程式。 您不得 `Set` 為唯讀屬性定義程式。  
  
## <a name="example"></a>範例  

 下列範例會建立讀取/寫入屬性，將全名儲存為兩個組成名稱、名字和姓氏。 當呼叫程式碼讀取時 `fullName` ，此程式會 `Get` 結合兩個構成名稱並傳回完整名稱。 當呼叫程式碼指派新的完整名稱時，此程式 `Set` 會嘗試將它分成兩個組成的名稱。 如果找不到空間，則會將它儲存為第一個名稱。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 下列範例顯示一般的屬性程式呼叫 `fullName` 。 第一個呼叫會設定屬性值，而第二個呼叫則會加以捕獲。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Visual Basic 中屬性和變數的差異](./differences-between-properties-and-variables.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
