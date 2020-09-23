---
title: 如何：使用物件初始設定式宣告物件
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 61f520a528c3d40b9d34807d517a9bf27ad40da8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075222"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>如何：使用物件初始設定式宣告物件 (Visual Basic)

物件初始化運算式可讓您在單一語句中宣告和具現化類別的實例。 此外，您可以同時初始化實例的一或多個成員，而不需要叫用參數化的函式。  
  
 當您使用物件初始化運算式來建立名為之型別的實例時，會呼叫該類別的無參數函式，接著依照您指定的順序初始化指定的成員。  
  
 下列程式顯示如何以三種不同的方式建立 `Student` 類別的實例。 類別具有 first name、last name 和 class year 屬性，還有其他屬性。 這三個宣告都會建立的新實例 `Student` ，其屬性 `First` 設定為 "Michael"、屬性 `Last` 設定為 "ilsi"，而其他所有成員則設為其預設值。 程式中每個宣告的結果都相當於下列範例，而不會使用物件初始化運算式。  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 如需類別的執行 `Student` 方式，請參閱 [如何：建立專案清單](../../concepts/linq/how-to-create-a-list-of-items.md)。 您可以從該主題複製程式碼來設定類別，並建立 `Student` 要使用的物件清單。  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>使用物件初始化運算式建立命名類別的物件  
  
1. 開始宣告，就像您計畫使用函式一樣。  
  
     `Dim student1 As New Student`  
  
2. 輸入關鍵字 `With` ，後面接著以大括弧括住的初始化清單。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. 在初始化清單中，包含您想要初始化的每個屬性，並為其指派初始值。 屬性的名稱前面會加上句號。  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     您可以初始化類別的一或多個成員。  
  
4. 或者，您可以宣告類別的新實例，然後將值指派給它。 首先，宣告的實例 `Student` ：  
  
     `Dim student2 As Student`  
  
5. `Student`以正常方式開始建立實例。  
  
     `Dim student2 As Student = New Student`  
  
6. 輸入 `With` ，然後輸入物件初始化運算式，以初始化新實例的一或多個成員。  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. 您可以省略上一個步驟中的定義，以簡化定義 `As Student` 。 如果您這樣做，編譯器 `student3` 會 `Student` 使用區欄位型別推斷來判斷是的實例。  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     如需詳細資訊，請參閱 [區欄位型別推斷](../variables/local-type-inference.md)。  
  
## <a name="see-also"></a>另請參閱

- [區域型別推斷](../variables/local-type-inference.md)
- [作法：建立項目清單](../../concepts/linq/how-to-create-a-list-of-items.md)
- [物件初始設定式：具名和匿名型別](object-initializers-named-and-anonymous-types.md)
- [匿名類型](anonymous-types.md)
