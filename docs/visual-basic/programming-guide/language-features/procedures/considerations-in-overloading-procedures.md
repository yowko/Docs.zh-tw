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
ms.openlocfilehash: bd5b0032ca63ccb2f2cc30d72a5b3f3c7eb3c346
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775728"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>多載化程序的考慮因素 (Visual Basic)
當您多載程式時，您必須針對每個多載版本使用*不同的簽*章。 這通常表示每個版本都必須指定不同的參數清單。 如需詳細資訊，請參閱程式多載[中的「不同的簽](./procedure-overloading.md)章」。  
  
 您可以使用 `Sub` 程式來多載 `Function` 程式，反之亦然，前提是它們有不同的簽章。 兩個多載不能有不同的差異，只有其中一個具有傳回值，另一個則沒有。  
  
 您可以使用與多載程式相同的方式來多載屬性，而且具有相同的限制。 但是，您無法使用屬性來多載程式，反之亦然。  
  
## <a name="alternatives-to-overloaded-versions"></a>多載版本的替代專案  
 有時候，您會有多載版本的替代專案，特別是當引數的存在是選擇性或其數位為變數時。  
  
 請記住，所有語言都不一定支援選擇性引數，而且參數陣列僅限於 Visual Basic。 如果您撰寫的程式可能會從以多種不同語言撰寫的程式碼中呼叫，則多載版本提供最大的彈性。  
  
### <a name="overloads-and-optional-arguments"></a>多載和選擇性引數  
 當呼叫程式碼可以選擇性地提供或省略一或多個引數時，您可以定義多個多載版本或使用選擇性參數。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載版本的時機  
 在下列情況下，您可以考慮定義一連串的多載版本：  
  
- 程式碼中的邏輯會根據呼叫程式碼是否提供選擇性引數而有很大的差異。  
  
- 程式碼無法可靠地測試呼叫程式碼是否已提供選擇性引數。 例如，如果沒有可供呼叫程式碼無法提供的預設值，就會發生這種情況。  
  
#### <a name="when-to-use-optional-parameters"></a>使用選擇性參數的時機  
 在下列情況中，您可能會偏好使用一或多個選擇性參數：  
  
- 當呼叫程式碼未提供選擇性引數時，唯一必要的動作是將參數設定為預設值。 在這種情況下，如果您定義具有一或多個 `Optional` 參數的單一版本，程式碼可能會比較不復雜。  
  
 如需詳細資訊，請參閱[選擇性參數](./optional-parameters.md)。  
  
### <a name="overloads-and-paramarrays"></a>多載和 ParamArrays  
 當呼叫程式碼可以傳遞可變數目的引數時，您可以定義多個多載版本，或使用參數陣列。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載版本的時機  
 在下列情況下，您可以考慮定義一連串的多載版本：  
  
- 您知道呼叫程式碼絕對不會將一個以上的值傳遞給參數陣列。  
  
- 程式碼中的邏輯會明顯不同，這取決於呼叫程式碼傳遞多少個值。  
  
- 呼叫程式碼可以傳遞不同資料類型的值。  
  
#### <a name="when-to-use-a-parameter-array"></a>使用參數陣列的時機  
 在下列情況下，`ParamArray` 參數會提供較佳的服務：  
  
- 您無法預測呼叫程式碼可以傳遞給參數陣列的值數目，而且可能是很大的數位。  
  
- 程式邏輯可自行逐一查看呼叫程式碼所通過的所有值，對每個值基本上執行相同的作業。  
  
 如需詳細資訊，請參閱[參數陣列](./parameter-arrays.md)。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>選擇性參數的隱含多載  
 具有[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)參數的程式相當於兩個多載的程式，一個包含選擇性參數，另一個則沒有。 您無法使用對應于其中任一項的參數清單來多載這類程式。 下列宣告說明這種情況。  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 針對具有多個選擇性參數的程式，會有一組隱含的多載，並以類似上述範例中的邏輯抵達。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray 參數的隱含多載  
 編譯器會將具有[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)參數的程式視為具有無限數量的多載，並在呼叫程式碼傳遞給參數陣列的內容中彼此不同，如下所示：  
  
- 呼叫程式碼未提供引數給 `ParamArray` 時的一個多載  
  
- 當呼叫程式碼提供 `ParamArray` 專案類型的一維陣列時，一個多載  
  
- 針對每個正整數，當呼叫程式碼提供該數目的引數時，一個多載，其中每個都是 `ParamArray` 的元素類型  
  
 下列宣告說明這些隱含多載。  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 您無法使用參數清單來多載這類程式，其中會採用一維陣列做為參數陣列。 不過，您可以使用其他隱含多載的簽章。 下列宣告說明這種情況。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>無程式設計是多載的替代方法  
 如果您想要允許呼叫程式碼將不同的資料類型傳遞給參數，另一個替代方法是無類型的程式設計。 您可以使用[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)或[-optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)編譯器選項，將類型檢查參數設定為 `Off`。 然後您就不需要宣告參數的資料類型。 不過，相較于多載，此方法具有下列缺點：  
  
- 無語言程式設計會產生較不有效率的執行程式碼。  
  
- 此程式必須針對預期傳遞的每個資料類型進行測試。  
  
- 如果呼叫程式碼傳遞程式不支援的資料類型，編譯器就無法通知錯誤。  
  
## <a name="see-also"></a>請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載解析](./overload-resolution.md)
- [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
