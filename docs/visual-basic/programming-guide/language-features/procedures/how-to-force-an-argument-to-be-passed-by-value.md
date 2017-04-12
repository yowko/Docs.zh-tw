---
title: "如何︰ 強制以傳值 (Visual Basic) 引數 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], in parentheses
- procedure arguments, in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eea3466534f1797170ae4bc72afbcba899929911
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>如何：強制以傳值方式傳遞引數 (Visual Basic)
程序宣告決定傳遞機制。 如果參數宣告[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]預期相對應的引數傳址方式傳遞。 這可讓變更的基礎呼叫程式碼中的引數的程式設計項目值的程序。 如果您想要保護對應的項目，針對這類變更，您可以覆寫`ByRef`程序中的傳遞機制來呼叫以括號括住的引數名稱。 這些括號是封閉的呼叫中引數清單的括號。  
  
 呼叫程式碼無法覆寫[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)機制。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>若要強制以傳值方式傳遞引數  
  
-   如果對應的參數宣告`ByVal`在程序中，您不需要採取任何額外的步驟。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]已預期傳值方式傳遞引數。  
  
-   如果對應的參數宣告`ByRef`在程序，將括在括號內的程序呼叫的引數。  
  
## <a name="example"></a>範例  
 下列範例會覆寫`ByRef`參數宣告。 在呼叫中，以強制`ByVal`，請注意括號括住的兩個層級。  
  
 [!code-vb[VbVbcnProcedures #&39;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&40;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 當`str`在引數清單中，額外的括號括住`setNewString`程序無法變更呼叫的程式碼，其值和`MsgBox`顯示"如果傳遞 ByVal 無法取代 」。 當`str`未隨附在額外的括號中的程序能夠加以修改，和`MsgBox`會顯示 「 這是 inString 引數的新值 」。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 當您由參考傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。  
  
 在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。 不過，它是良好的程式設計作法包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。 這可讓您的程式碼更容易讀取。  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果程序會宣告參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，正確執行的程式碼可能相依於不能變更呼叫的程式碼對應的項目。 如果呼叫程式碼覆寫此呼叫的機制以括號括住引數，或將不可修改引數傳遞，此程序無法變更對應的項目。 這可能會產生非預期的結果，在呼叫程式碼。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 允許的程序來變更對應的引數呼叫的程式碼中的值總是有潛在的風險。 請確定您預期此變更，並準備好檢查它的有效性，然後再將它的值。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)   
 [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md)   
 [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [以傳值或參考所傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [如何︰ 變更程序引數的值](./how-to-change-the-value-of-a-procedure-argument.md)   
 [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)   
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
