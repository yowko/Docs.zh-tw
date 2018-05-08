---
title: 多載化程序的考慮因素 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: e1768d0ac03cb6730c4337d7476ae163e75adfd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>多載化程序的考慮因素 (Visual Basic)
當您多載程序時，您必須使用不同*簽章*每個多載版本。 這通常表示每個版本都必須指定不同的參數清單。 如需詳細資訊，請參閱 「 不同簽章 」[程序多載](./procedure-overloading.md)。  
  
 您可以多載`Function`程序，並`Sub`程序中，且反之亦然，提供它們有不同的簽章。 兩個多載不能不同只在於一個具有傳回值，其他則否。  
  
 您可以如同您多載程序中，多載屬性和相同的限制。 不過，您無法多載程序與屬性，反之亦然。  
  
## <a name="alternatives-to-overloaded-versions"></a>多載版本的替代方案  
 尤其是選擇性的引數存在，或他們的數目是變數中，有時會有多載版本，替代方案。  
  
 請注意選擇性引數不一定支援所有的語言，而且僅限於使用 Visual Basic 的參數陣列。 如果您正在撰寫可能以任何有幾種不同語言所撰寫的程式碼呼叫的程序，多載版本就可以提供最大的彈性。  
  
### <a name="overloads-and-optional-arguments"></a>多載和選擇性引數  
 當呼叫程式碼可以選擇性地提供，或略過一個或多個引數時，您可以定義多個多載的版本，或使用選擇性參數。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載的版本的時機  
 您可以考慮在下列情況下定義一系列多載版本：  
  
-   程序程式碼中的邏輯是根據呼叫的程式碼是否提供選擇性引數會大幅不同。  
  
-   程序程式碼無法可靠地測試是否呼叫的程式碼已提供選擇性引數。 這種情況，比方說，如果沒有任何可能的候選項的預設值，呼叫程式碼可能不需要提供。  
  
#### <a name="when-to-use-optional-parameters"></a>當使用選擇性參數  
 您可能會偏好在下列情況中的一個或多個選擇性參數：  
  
-   若要將參數設定為預設值是唯一必要的動作時呼叫的程式碼並不提供選擇性引數。 在這種情況下中, 程序程式碼可能較不複雜，如果您定義一或多個單一版本`Optional`參數。  
  
 如需詳細資訊，請參閱[選擇性參數](./optional-parameters.md)。  
  
### <a name="overloads-and-paramarrays"></a>多載和參數陣列  
 當呼叫程式碼可以傳遞可變引數數目時，您可以定義多個多載的版本，或使用參數陣列。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載的版本的時機  
 您可以考慮在下列情況下定義一系列多載版本：  
  
-   您知道，呼叫程式碼永遠不會傳遞多個少數值至參數陣列。  
  
-   程序程式碼中的邏輯是根據呼叫的程式碼傳遞的值數目會大幅不同。  
  
-   呼叫程式碼可以傳遞不同的資料類型的值。  
  
#### <a name="when-to-use-a-parameter-array"></a>使用參數陣列的時機  
 您服務會比較好`ParamArray`參數，在下列情況：  
  
-   您不能預測多少值呼叫的程式碼可以傳遞至參數陣列，並很大的數字。  
  
-   程序邏輯本身來逐一查看所有的值通過，呼叫程式碼，執行每個值基本上相同的作業。  
  
 如需詳細資訊，請參閱[參數陣列](./parameter-arrays.md)。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>選擇性參數的隱含多載  
 程序時使用[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數相當於兩個多載的程序，一個選擇性參數，另一個則沒有。 您無法多載參數清單，對應到的其中一個這類程序。 下列宣告來說明這點。  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 對於具有一個以上的選擇性參數的程序，沒有一組隱含的多載，類似於上述範例中的邏輯抵達。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray 參數的隱含多載  
 編譯器會考慮的程序有[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數具有無限個多載，與彼此不同，在所呼叫的程式碼將傳遞至參數陣列，如下所示：  
  
-   一個多載時，呼叫程式碼並不提供的引數 `ParamArray`  
  
-   一個多載的呼叫端程式碼時提供的一維陣列`ParamArray`項目類型  
  
-   對每一個正整數，其中一個多載時，呼叫程式碼提供該數目之引數，每個`ParamArray`項目類型  
  
 下列宣告會說明這些隱含的多載。  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 您無法多載會採用參數陣列的一維陣列的參數清單具有這類的程序。 不過，您可以使用其他隱含多載的簽章。 下列宣告來說明這點。  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>做為多載替代的無類型程式設計  
 如果您想要允許不同的資料型別傳遞至參數呼叫的程式碼，另一個方法是無類型程式設計。 您可以設定型別檢查切換到`Off`其中一種[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項。 然後您沒有宣告參數的資料類型。 不過，這個方法有下列缺點相較於多載：  
  
-   無類型程式設計會產生較有效率的執行程式碼。  
  
-   此程序必須測試它預期傳遞的每一個資料型別。  
  
-   編譯器無法通知發生錯誤，如果呼叫程式碼會將傳遞程序不支援的資料類型。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [程序的疑難排解](./troubleshooting-procedures.md)  
 [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)  
 [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)  
 [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [多載解析](./overload-resolution.md)  
 [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
