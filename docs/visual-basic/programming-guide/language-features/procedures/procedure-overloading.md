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
ms.openlocfilehash: 4d90b81049197fbbf4a767b17399d3e9c80be0f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975468"
---
# <a name="procedure-overloading-visual-basic"></a>程序多載化 (Visual Basic)
*多載*程序可讓您表示定義在多個版本中，使用相同名稱但不同的參數清單。 多載的用途是定義程序的數個密切相關的版本，而不需要依名稱加以區隔。 您可以不同的參數清單。  
  
## <a name="overloading-rules"></a>多載規則  
 當您多載程序時，適用下列規則：  
  
-   **相同名稱**。 每個多載的版本必須使用相同的程序名稱。  
  
-   **不同的簽章**。 每個多載的版本必須與所有其他多載版本至少要有一個下列方面不同：  
  
    -   參數數目  
  
    -   參數的順序  
  
    -   參數的資料類型  
  
    -   （適用於泛型程序） 的型別參數數目  
  
    -   （僅適用於轉換運算子） 的傳回型別  
  
     統稱為程序名稱，連同上述項目*簽章*程序。 當您呼叫多載的程序時，編譯器會用來檢查呼叫正確地符合定義的簽章。  
  
-   **項目不屬於簽章**。 您無法多載程序，而不需要不同的簽章。 特別是，您無法只改變一個或多個下列項目來多載程序：  
  
    -   程序修飾詞關鍵字，例如`Public`， `Shared`，及 `Static`  
  
    -   參數或型別參數名稱  
  
    -   （適用於泛型程序） 的類型參數條件約束  
  
    -   參數修飾詞關鍵字，例如`ByRef`和 `Optional`  
  
    -   是否會傳回值  
  
    -   傳回值 （除了轉換運算子） 的資料類型  
  
     上述清單中的項目不是簽章的一部分。 雖然您無法使用它們來區別多載版本，您可以將它們異適當地加以區分它們的簽章的多載版本。  
  
-   **晚期繫結引數**。 如果您想要將晚期繫結的物件變數傳遞給的多載版本，您必須宣告適當的參數為<xref:System.Object>。  
  
## <a name="multiple-versions-of-a-procedure"></a>多個版本的程序  
 假設您正在撰寫`Sub`程序來張貼交易中的針對客戶餘額，以及您想要能夠依名稱或帳戶，請參閱給客戶。 若要做到這一點，您可以定義兩個不同`Sub`程序，如下列範例所示：  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a>多載的版本  
 替代方法是多載是單一的程序名稱。 您可以使用[多載](../../../../visual-basic/language-reference/modifiers/overloads.md)關鍵字來定義每個參數清單，此程序的版本，如下所示：  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a>其他多載  
 如果您也想要接受在交易量`Decimal`或是`Single`，您可以進一步多載`post`以便進行這項差異。 如果您這麼做會以每個多載，在上述範例中，有四個`Sub`程序，所有具有相同名稱但具有四個不同的簽章。  
  
## <a name="advantages-of-overloading"></a>多載的優點  
 多載化程序的優點是在呼叫的彈性。 若要使用`post`程序的宣告是在上述範例中，而呼叫的程式碼可以取得客戶識別為`String`或`Integer`，然後在任一情況下呼叫相同的程序。 下面這個範例可說明這點：  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>另請參閱
- [程序](./index.md)
- [如何：定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：多載會採用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載解析](./overload-resolution.md)
- [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
