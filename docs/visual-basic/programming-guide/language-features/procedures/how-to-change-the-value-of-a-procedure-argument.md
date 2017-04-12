---
title: "如何︰ 變更程序引數 (Visual Basic) 的值 |Microsoft 文件"
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
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
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
ms.openlocfilehash: 6c42a50b75bcc70ae0a3f70771b9e1f85626004b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>如何：變更程序引數的值 (Visual Basic)
當您呼叫程序時，您提供每個引數會對應至其中一個程序中所定義的參數。 在某些情況下，程序程式碼可以變更對應的引數呼叫的程式碼中的值。 在其他情況下，此程序可以變更引數其本機複本。  
  
 當您呼叫程序，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]讓每個傳遞的引數的本機副本[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)。 每個引數傳遞[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供程序程式碼直接呼叫程式碼中的引數的程式設計項目參考。  
  
 如果呼叫程式碼對應的項目設定為可修改的項目，並傳遞引數的`ByRef`，程序程式碼可以使用直接參考來變更呼叫的程式碼中的項目的值。  
  
## <a name="changing-the-underlying-value"></a>變更基礎值  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>若要變更基礎值的程序中的引數呼叫的程式碼  
  
1.  在程序宣告中，指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)參數對應至引數。  
  
2.  在呼叫的程式碼，將傳遞做為引數的可修改的程式設計項目。  
  
3.  在呼叫的程式碼，不要使用引數清單中的括號括住的引數。  
  
4.  在程序程式碼中使用參數名稱來指派值給呼叫程式碼對應的項目。  
  
 請參閱範例進一步示範。  
  
## <a name="changing-local-copies"></a>變更本機複本  
 如果呼叫程式碼對應的項目不可修改的項目，或如果引數傳遞`ByVal`，程序無法變更其呼叫的程式碼中的值。 不過，此程序可以變更這類引數的本機複本。  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>若要變更的程序中的引數的程序程式碼複製  
  
1.  在程序宣告中，指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)參數對應至引數。  
  
     -或-  
  
     在呼叫程式碼中，括住引數清單中的括號括住的引數。 這會強制[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]至引數傳值方式傳遞，即使對應的參數會指定`ByRef`。  
  
2.  在程序程式碼中，使用參數名稱來指派值給引數的本機複本。 不會變更呼叫的程式碼中的對應值。  
  
## <a name="example"></a>範例  
 下列範例會顯示兩個程序取得陣列變數和操作其項目上。 `increase`程序只會加入至每個項目。 `replace`程序會將新的陣列指派給參數`a()`並將每個項目。  
  
 [!code-vb[VbVbcnProcedures #&35;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures #&36;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 第一個`MsgBox`呼叫會顯示 「 後 increase(n): 11、 21、 31、 41 」。 因為陣列`n`是參考型別，`replace`可以變更其成員，即使傳遞機制`ByVal`。  
  
 第二個`MsgBox`呼叫會顯示 「 後 replace(n): 101、 201、 301 」。 因為`n`傳遞`ByRef`，`replace`可以修改變數`n`呼叫程式碼和指派給它的新陣列中。 因為`n`是參考型別，`replace`也可以變更其成員。  
  
 您可以防止程序修改呼叫程式碼本身的變數。 請參閱[如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 當您由參考傳遞的變數時，您必須使用`ByRef`關鍵字來指定這項機制。  
  
 在預設[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]是以傳值方式傳遞引數。 不過，它是良好的程式設計作法包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)關鍵字與每個宣告的參數。 這可讓您的程式碼更容易讀取。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 允許的程序來變更對應的引數呼叫的程式碼中的值總是有潛在的風險。 請確定您預期此變更，並準備好檢查它的有效性，然後再將它的值。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [如何︰ 將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)   
 [傳遞引數以傳值或傳址](./passing-arguments-by-value-and-by-reference.md)   
 [可修改和不可修改引數之間的差異](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [以傳值或參考所傳遞引數之間的差異](./differences-between-passing-an-argument-by-value-and-by-reference.md)   
 [如何︰ 防止程序引數的值變更](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [如何︰ 強制以傳值方式傳遞引數](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)   
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
