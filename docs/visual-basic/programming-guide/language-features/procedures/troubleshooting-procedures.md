---
title: 疑難排解程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 1a8cd568f1a9a05721f311cc72a22bfc2b6bcfc9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625462"
---
# <a name="troubleshooting-procedures-visual-basic"></a>疑難排解程序 (Visual Basic)
此頁面會列出處理程序時所發生的一些常見問題。  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>從函式程序傳回陣列類型  
 如果`Function`程序會傳回陣列資料型別，您不能使用`Function`將值儲存在陣列的元素名稱。 如果您嘗試執行這項操作時，編譯器就會將它解譯為要呼叫`Function`。 下列範例會產生編譯器錯誤。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 陳述式`allOnes(i) = 1`會產生編譯器錯誤，因為它看起來像是呼叫`allOnes`具有錯誤的資料類型的引數 (單一`Integer`而不是`Integer`陣列)。 陳述式`Return allOnes()`會產生編譯器錯誤，因為它看起來像是呼叫`allOnes`但沒有引數。  
  
 **正確的方法：** 若要能夠修改要傳回之陣列的項目，定義內部陣列做為本機變數。 下列範例會編譯無誤。  
  
 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>引數不修改程序呼叫  
 如果您想要允許的程序來變更基礎呼叫程式碼中的引數的程式設計項目，您必須將它傳遞的參考。 但一個程序可以存取的參考型別引數的項目，即使您傳值方式傳遞。  
  
- **基礎變數**。 若要允許的程序來取代基礎變數項目本身的值，此程序必須宣告的參數[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)。 此外，呼叫程式碼必須沒有引數括號括住，因為，將會覆寫`ByRef`傳遞機制。  
  
- **參考型別項目**。 如果您宣告的參數[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)，程序無法修改基礎變數項目本身。 不過，如果引數是參考類型，程序可以修改它所指向，物件的成員即使它不能取代變數的值。 比方說，如果引數陣列變數，程序無法將新的陣列指派給它，但它可以變更一或多個子項目。 已變更的項目會反映在呼叫程式碼中的陣列變數。  
  
 下列範例會定義兩個程序，以傳值方式取得陣列變數和操作其項目上。 程序`increase`直接新增至每個項目。 程序`replace`將新的陣列指派給參數`a()`，然後新增一個每個項目。 不過，重新指派不會影響呼叫端程式碼中的陣列變數因為`a()`宣告`ByVal`。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 下列範例會呼叫`increase`和`replace`。  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 第一個`MsgBox`呼叫會顯示 「 increase(n) 之後：11, 21, 31, 41". 因為`n`是參考型別`increase`可以變更其成員，即使它傳遞`ByVal`。  
  
 第二個`MsgBox`呼叫會顯示 「 replace(n) 之後：11, 21, 31, 41". 因為`n`傳遞`ByVal`，`replace`不能修改變數`n`藉由將新的陣列指派給它。 當`replace`建立新的陣列執行個體`k`並將它指派給區域變數`a`，就會失去參考`n`傳入呼叫的程式碼。 它會遞增的成員`a`，只有本機陣列`k`會受到影響。  
  
 **正確的方法：** 若要能夠修改對應的變數項目本身，傳址方式傳遞。 下列範例顯示的宣告中的變更`replace`可取代呼叫的程式碼中的另一個陣列。  
  
 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]  
  
## <a name="unable-to-define-an-overload"></a>無法定義多載  
 如果您想要定義的程序的多載的版本，您必須使用相同名稱但不同的簽章。 如果編譯器無法區分您的宣告，從相同的簽章的多載，它會產生錯誤。  
  
 *簽章*程序取決於程序名稱和參數清單。 每個多載必須有相同的名稱，為所有其他的多載，但必須不同於全部都放在至少一個簽章的其他元件。 如需詳細資訊，請參閱 [Procedure Overloading](./procedure-overloading.md)。  
  
 下列項目，即使它們屬於 [參數] 清單中，不是元件的程序的簽章：  
  
- 程序修飾詞關鍵字，例如`Public`， `Shared`，及 `Static`  
  
- 參數名稱  
  
- 參數修飾詞關鍵字，例如`ByRef`和 `Optional`  
  
- 傳回值 （除了轉換運算子） 的資料類型  
  
 若要多載程序，不能只改變一個或多個先前的項目。  
  
 **正確的方法：** 若要定義的程序多載，您必須變更簽章。 因為您必須使用相同的名稱，您必須變更數目、 順序或參數的資料類型。 在一般的程序中，您可以變更類型參數的數目。 在 轉換運算子 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md))，您可以變更傳回型別。  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>多載使用選擇性的解析度和 ParamArray 引數  
 如果您多載具有一或多個的程序[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數或[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數，您必須避免重複任何*隱含的多載*。 如需資訊，請參閱[多載化程序中的考量](./considerations-in-overloading-procedures.md)。  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>呼叫的多載的程序的版本錯誤  
 如果程序有數個多載的版本，您應該先熟悉所有的參數清單，並了解 Visual Basic 如何解析多載之間的呼叫。 否則，您可以呼叫非預期的多載。  
  
 當您已經決定您想要呼叫哪個多的載時，請務必遵守下列規則：  
  
- 請提供正確數目的引數，並以正確的順序。  
  
- 在理想情況下，您的引數應該完全相同的資料類型與對應的參數。 在任何情況下，每個引數的資料類型必須擴展為，其對應參數。 這是 true，即使[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定為`Off`。 如果多載都需要任何引數清單，請多載的縮小轉換不符合資格，來呼叫。  
  
- 如果您提供需要擴展的引數，請為對應的參數資料類型，盡可能接近其資料類型。 如果兩個或多個多載會接受引數的資料型別，編譯器會解析您最少擴展的呼叫多載的呼叫。  
  
 您可以使用，以降低可能發生的資料類型不符[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)轉換關鍵字，準備您的引數時。  
  
### <a name="overload-resolution-failure"></a>多載解析失敗  
 當您呼叫多載的程序時，編譯器會嘗試排除所有只留下其中一個多載。 如果成功，它會解析該多載的呼叫。 它會排除所有多載，則它無法縮小到單一的候選資格的多載，它會產生錯誤。  
  
 下列範例說明多載解析程序。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 在第一個呼叫中，編譯器會排除第一個多載因為第一個引數的類型 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。 它然後排除第三個多載，因為每個引數類型中的第二個多載 (`Short`並`Single`) 可擴展為對應的型別中的第三個多載 (`Integer`和`Single`)。 第二個多載都需要較少的擴展，因此編譯器會將它用於呼叫。  
  
 在第二個呼叫中，編譯器無法排除任何根據縮小的多載。 基於相同理由，如同第一次呼叫中中,，因為它可以呼叫第二個多載，較不需要擴展的引數類型，它會排除第三個多載。 不過，編譯器無法解析的第一個和第二個多載之間。 各有一個定義的參數類型可擴展成其他對應的類型 (`Byte`來`Short`，但`Single`至`Double`)。 因此，編譯器會產生多載解析錯誤。  
  
 **正確的方法：** 若要能夠呼叫沒有模稜兩可的多載程序，使用[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)來比對引數資料類型與參數類型。 下列範例示範呼叫`z`，強制第二個多載解析。  
  
 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>多載使用選擇性的解析度和 ParamArray 引數  
 如果程序的兩個多載具有相同簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)其中一並[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)在另一個，編譯器會解析該程序的呼叫根據最接近的相符項目。 如需詳細資訊，請參閱 [Overload Resolution](./overload-resolution.md)。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序多載化](./procedure-overloading.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載解析](./overload-resolution.md)
