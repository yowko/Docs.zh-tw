---
title: "疑難排解程序 (Visual Basic) |Microsoft 文件"
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
- troubleshooting Visual Basic, procedures
- procedures, troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures, about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: a5445d6da982e4eea5b1047505e4bee3380ed472
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-procedures-visual-basic"></a>疑難排解程序 (Visual Basic)
此頁面會列出處理程序時所發生的一些常見問題。  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>從函式程序傳回的陣列型別  
 如果`Function`程序會傳回陣列的資料型別，您無法使用`Function`將值儲存在陣列元素的名稱。 如果您嘗試這樣做，編譯器會解譯為呼叫`Function`。 下列範例會產生編譯器錯誤。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 陳述式`allOnes(i) = 1`呼叫，所以會產生編譯器錯誤`allOnes`與錯誤的資料類型的引數 (單一`Integer`而不是`Integer`陣列)。 陳述式`Return allOnes()`呼叫，所以會產生編譯器錯誤`allOnes`但沒有引數。  
  
 **正確的方法︰**能夠修改要傳回之陣列的項目，定義內部陣列做為本機變數。 下列範例會編譯無誤。  
  
 [!code-vb[VbVbcnProcedures #&66;](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>未修改的引數的程序呼叫  
 如果您想要允許的程序來變更對應的引數呼叫程式碼的程式設計項目，您必須參考來傳遞。 但即使您傳值方式傳遞程序可以存取參考型別引數的項目。  
  
-   **基礎變數**。 若要允許的程序來取代對應變數項目本身的值，此程序必須宣告參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。 此外，呼叫程式碼必須沒有引數括號括住，因為，就會覆寫`ByRef`傳遞機制。  
  
-   **參考型別項目**。 如果您將參數宣告[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)，程序無法修改對應變數項目本身。 不過，如果引數是參考型別，此程序可以修改它所指向的物件的成員即使它無法取代變數的值。 比方說，如果引數陣列變數，程序無法將新的陣列指派給它，但可以變更一或多個項目。 已變更的項目會反映在呼叫程式碼中的陣列變數。  
  
 下列範例會定義兩個程序，以傳值方式取得陣列變數和操作其項目上。 程序`increase`直接加入至每個項目。 程序`replace`將新的陣列指派給參數`a()`並將每個項目。 不過，重新指派不會影響呼叫程式碼中的陣列變數因為`a()`宣告`ByVal`。  
  
 [!code-vb[VbVbcnProcedures #&35;](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 下列範例會呼叫`increase`和`replace`。  
  
 [!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 第一個`MsgBox`呼叫會顯示 「 後 increase(n): 11、 21、 31、 41 」。 因為`n`是參考型別，`increase`可以變更其成員，即使它傳遞`ByVal`。  
  
 第二個`MsgBox`呼叫會顯示 「 後 replace(n): 11、 21、 31、 41 」。 因為`n`傳遞`ByVal`，`replace`無法修改變數`n`指派給它的新陣列。 當`replace`建立新的陣列執行個體`k`並將它指派給本機變數`a`，它就不會參考`n`傳入呼叫程式碼。 它會遞增的成員`a`，只有本機陣列`k`會受到影響。  
  
 **正確的方法︰**能夠修改對應的變數項目本身，它傳址方式傳遞。 下列範例顯示的宣告中的變更`replace`，可讓它與另一個呼叫程式碼來取代一個陣列。  
  
 [!code-vb[VbVbcnProcedures #&64;](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a>無法定義多載  
 如果您想要定義的程序多載的版本，您必須使用相同名稱但不同的簽章。 如果編譯器無法辨識您的宣告與相同的簽章的多載，它會產生錯誤。  
  
 *簽章*程序由程序名稱和參數清單。 每個多載必須有同名的所有其他多載，但是必須不同於全部都在至少一個簽章的其他元件。 如需詳細資訊，請參閱[程序多載](./procedure-overloading.md)。  
  
 下列項目，即使它們屬於參數清單中，不是元件的程序的簽章︰  
  
-   程序的修飾詞關鍵字，例如`Public`， `Shared`，並`Static`  
  
-   參數名稱  
  
-   參數修飾詞關鍵字，例如`ByRef`和`Optional`  
  
-   傳回值 （除了轉換運算子） 的資料類型  
  
 您無法只改變一個或多個上述項目的多載程序。  
  
 **正確的方法︰**可以定義程序多載，所以必須改變簽章。 因為您必須使用相同的名稱，您必須變更數目、 順序或參數的資料類型。 在一般的程序，您可以更改類型參數的數目。 在轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md))，您可以變更傳回型別。  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>多載使用選擇性的解析度和 ParamArray 引數  
 如果您多載化程序時使用一或多個[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數或[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您必須避免重複的任何*隱含多載*。 如需資訊，請參閱[中多載化程序的考量](./considerations-in-overloading-procedures.md)。  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>呼叫的多載的程序的版本錯誤  
 如果程序有數個多載的版本，您應該先熟悉所有的參數清單，並了解如何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]解析多載之間的呼叫。 否則，您可以呼叫非預期的多載。  
  
 當您決定您想要呼叫的多載時，小心觀察下列規則︰  
  
-   請提供正確數目的引數，並以正確的順序。  
  
-   在理想情況下，您的引數應該有完全相同的資料類型與對應的參數。 在任何情況下，每個引數的資料型別必須擴展成其對應的參數。 這是即使有，則為 true [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設為`Off`。 如果多載需要任何引數清單，該多載，縮小轉換不能夠呼叫。  
  
-   如果您提供需要擴展的引數，請盡可能靠近彼此相對應的參數資料型別及其資料型別。 如果兩個或多個多載會接受引數的資料型別，編譯器會解析您對呼叫的擴展程度最少的多載的呼叫。  
  
 您可以使用，以降低資料型別不相符的機率[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)準備您的引數時，轉換關鍵字。  
  
### <a name="overload-resolution-failure"></a>多載解析失敗  
 當您呼叫多載的程序時，編譯器就會嘗試排除其中一個多載。 如果成功，它會解析該多載的呼叫。 如果它也消除了所有多載，或如果它不能減少為單一的候選者合格的多載，它會產生錯誤。  
  
 下列範例說明多載解析程序。  
  
 [!code-vb[VbVbcnProcedures #&62;](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures #&63;](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 在第一次呼叫時，編譯器會排除第一個多載因為第一個引數型別 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。 它接著排除第三個多載，因為每個引數型別中的第二個多載 (`Short`和`Single`) 擴展至對應的型別中的第三個多載 (`Integer`和`Single`)。 第二個多載需要較少的擴展，因此編譯器會將它的呼叫。  
  
 在第二個呼叫中，編譯器無法排除任何以縮小為基礎的多載。 它也消除了第三個多載基於相同理由，第一個呼叫，因為它可以呼叫第二個多載，較不需要擴展引數型別。 不過，編譯器無法解析的第一個和第二個多載之間。 每個都有擴展至對應的型別，在另一個定義的參數型別 (`Byte`至`Short`，但`Single`到`Double`)。 因此，編譯器會產生多載解析錯誤。  
  
 **正確的方法︰**能夠呼叫沒有模稜兩可的多載程序，請使用[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)以符合參數型別引數資料型別。 下列範例會示範呼叫`z`，強制第二個多載解析。  
  
 [!code-vb[VbVbcnProcedures #&65;](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>多載使用選擇性的解析度和 ParamArray 引數  
 如果程序的兩個多載具有相同的簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)一個和[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)中，編譯器會根據最符合該程序的呼叫。 如需詳細資訊，請參閱[多載解析](./overload-resolution.md)。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)   
 [Sub 程序](./sub-procedures.md)   
 [Function 程序](./function-procedures.md)   
 [Property 程序](./property-procedures.md)   
 [運算子程序](./operator-procedures.md)   
 [程序參數和引數](./procedure-parameters-and-arguments.md)   
 [多載化程序](./procedure-overloading.md)   
 [多載化程序的考量](./considerations-in-overloading-procedures.md)   
 [多載解析](./overload-resolution.md)
