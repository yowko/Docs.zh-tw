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
ms.openlocfilehash: f14cc28960af28530bda9a78c1309dea10c18b8f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58815585"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>多載化程序的考慮因素 (Visual Basic)
當您多載程序時，您必須使用不同*簽章*針對每個多載版本。 這通常表示每個版本必須指定不同的參數清單。 如需詳細資訊，請參閱 「 不同的簽章 」 中[程序多載](./procedure-overloading.md)。  
  
 您可以多載`Function`程序`Sub`程序中，而且反之亦然，提供它們有不同的簽章。 兩個多載無法差異只在於有傳回值及其他則否。  
  
 您可以多載程序中，相同的方式多載屬性和具有相同的限制。 不過，您無法多載程序與屬性，反之亦然。  
  
## <a name="alternatives-to-overloaded-versions"></a>多載版本的替代方案  
 是選擇性的引數存在，或其數目為變數時，特別是，有時候會有多載版本的替代方案。  
  
 請記住，選擇性引數不一定支援所有的語言，以及參數陣列僅限於使用 Visual Basic。 如果您正在撰寫可能從任何有幾種不同語言撰寫的程式碼呼叫的程序，多載版本的供應項目最大的彈性。  
  
### <a name="overloads-and-optional-arguments"></a>多載和選擇性引數  
 當呼叫程式碼可以選擇性地提供或省略一或多個引數時，您可以定義多個多載的版本，或使用選擇性參數。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載的版本的時機  
 在下列情況下，可以考慮一系列的多載版本：  
  
-   程序程式碼中的邏輯是根據呼叫的程式碼是否提供選擇性引數截然不同。  
  
-   是否呼叫程式碼已提供的選擇性引數，無法可靠地測試程序程式碼。 此情況下，比方說，如果有任何可能的候選項目的預設值，呼叫程式碼可能不需要提供。  
  
#### <a name="when-to-use-optional-parameters"></a>當使用選擇性參數  
 您可能會偏好在下列情況中的一或多個選擇性參數：  
  
-   若要將參數設定為預設值是唯一必要的動作時呼叫的程式碼中未提供選擇性引數。 在此情況下中的程序程式碼可以變得簡單許多，如果您定義具有一或多個單一版本`Optional`參數。  
  
 如需詳細資訊，請參閱 <<c0> [ 選擇性參數](./optional-parameters.md)。  
  
### <a name="overloads-and-paramarrays"></a>多載和參數陣列  
 當呼叫的程式碼可以傳遞可變數目的引數時，您可以定義多個多載的版本，或使用參數陣列。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載的版本的時機  
 在下列情況下，可以考慮一系列的多載版本：  
  
-   您知道，呼叫程式碼永遠不會傳遞多個一小部分的值給參數陣列。  
  
-   程序程式碼中的邏輯是根據呼叫的程式碼傳遞的值數目大幅不同。  
  
-   呼叫端程式碼可以傳遞不同的資料類型的值。  
  
#### <a name="when-to-use-a-parameter-array"></a>使用參數陣列的時機  
 您會取得更佳服務`ParamArray`參數，在下列情況：  
  
-   您不能預測多少值呼叫的程式碼可以傳遞給參數陣列，並可能是大的數字。  
  
-   程序邏輯可用於逐一查看通過呼叫程式碼，執行本質相同之作業的每個值上的所有值。  
  
 如需詳細資訊，請參閱 <<c0> [ 參數陣列](./parameter-arrays.md)。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>選擇性參數的隱含多載  
 使用的程序[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數相當於兩個多載的程序，一個選擇性參數，而不需要它的另一個。 您無法多載這樣的程序，使用對應至其中的參數清單。 下列宣告將說明這點。  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 一個以上的選擇性參數的程序，沒有一組隱含的多載，抵達類似於在上述範例中的邏輯。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray 參數的隱含多載  
 編譯器會考慮使用的程序[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數具有無限個多載，彼此不同項目呼叫的程式碼將傳遞給參數陣列，如下所示：  
  
-   其中一個多載的呼叫端程式碼時未提供的引數 `ParamArray`  
  
-   針對呼叫的程式碼時提供的一維陣列的其中一個多載`ParamArray`項目類型  
  
-   對每一個正整數，其中一個多載時呼叫的程式碼提供該數目的引數，每個`ParamArray`項目類型  
  
 下列宣告會說明這些隱含的多載。  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 您無法多載會採用參數陣列的一維陣列的參數清單的這類的程序。 不過，您可以使用其他隱含的多載的簽章。 下列宣告將說明這點。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>除了多載的無類型程式設計  
 如果您想要允許呼叫端的程式碼，來傳遞參數至不同的資料類型，另一個方法是無型別程式設計。 您可以設定類型檢查參數來`Off`與其中一個[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項。 然後您沒有宣告參數的資料類型。 不過，這個方法會有下列缺點相較於多載：  
  
-   無類型程式設計產生效率較低的執行程式碼。  
  
-   此程序必須測試它預期傳遞的每一個資料型別。  
  
-   編譯器無法通知發生錯誤，如果呼叫程式碼會將此程序不支援的資料類型。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：多載會採用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載解析](./overload-resolution.md)
- [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
