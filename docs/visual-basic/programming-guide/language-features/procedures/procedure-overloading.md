---
title: 程序多載化 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 0d1f2c4d8c88922659b3d91ed41d5e760e6e5233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653910"
---
# <a name="procedure-overloading-visual-basic"></a>程序多載化 (Visual Basic)
*多載*程序會表示定義在多個版本中，使用相同名稱但不同參數清單。 多載的用途是定義程序的數個密切相關的版本，而不需要加以區分名稱。 您可以不同的參數清單。  
  
## <a name="overloading-rules"></a>多載規則  
 當您多載程序時，適用下列規則：  
  
-   **相同名稱**。 每個多載的版本必須使用相同的程序名稱。  
  
-   **不同的簽章**。 每個多載的版本必須與所有其他多載版本中至少一個下列方面不同：  
  
    -   參數數目  
  
    -   參數的順序  
  
    -   參數的資料類型  
  
    -   （適用於泛型程序） 的型別參數數目  
  
    -   （僅適用於轉換運算子） 的傳回型別  
  
     統稱為 「 程序名稱，以及先前的項目*簽章*程序。 當您呼叫多載的程序時，編譯器會用來檢查呼叫正確符合定義的簽章。  
  
-   **項目不屬於簽章**。 您無法多載程序，而不改變簽章。 特別是，您無法只改變一個或多個下列項目來多載程序：  
  
    -   程序修飾詞關鍵字，例如`Public`， `Shared`，和 `Static`  
  
    -   參數或型別參數名稱  
  
    -   類型參數條件約束 （適用於泛型程序）  
  
    -   參數修飾詞關鍵字，例如`ByRef`和 `Optional`  
  
    -   傳回值  
  
    -   傳回值 （除了轉換運算子） 的資料類型  
  
     上述清單中的項目不是簽章的一部分。 雖然您無法使用它們來區別多載版本，您可以將它們異正確簽章來區分的多載版本。  
  
-   **晚期繫結引數**。 如果您想要將晚期繫結的物件變數傳遞給一個多載版本，您必須宣告適當的參數為<xref:System.Object>。  
  
## <a name="multiple-versions-of-a-procedure"></a>多個版本的程序  
 假設您要撰寫`Sub`程序以公佈交易中針對客戶的平衡，而您想要能夠依名稱或帳戶是指客戶。 若要做到這一點，您可以定義兩個不同`Sub`程序，如下列範例所示：  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a>多載的版本  
 替代方法是將多載的單一程序名稱。 您可以使用[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字來定義為每個參數清單中，程序的版本，如下所示：  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a>其他多載  
 如果您也想要接受在交易量`Decimal`或`Single`，您無法進一步多載`post`以便進行這項差異。 如果您已將每個在上述範例中的多載有四個`Sub`程序有相同的名稱，但具有四個不同的簽章。  
  
## <a name="advantages-of-overloading"></a>多載的優點  
 多載化程序的優點是在呼叫的彈性。 若要使用`post`程序宣告在上述範例中，呼叫程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下呼叫相同的程序。 下面這個範例可說明這點：  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)  
 [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)  
 [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)  
 [多載解析](./overload-resolution.md)  
 [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
