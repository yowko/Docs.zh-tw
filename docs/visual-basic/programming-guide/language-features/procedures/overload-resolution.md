---
title: Overload Resolution
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266868"
---
# <a name="overload-resolution-visual-basic"></a>多載解析 (Visual Basic)
當 Visual Basic 編譯器遇到對在多個重載版本中定義的過程的調用時，編譯器必須決定調用的重載。 它通過執行以下步驟來完成此工作：  
  
1. **協助工具。** 它通過阻止調用代碼調用它的存取層級消除了任何重載。  
  
2. **參數數。** 它消除了定義與調用中提供的參數數不同的任何重載。  
  
3. **參數資料類型。** 編譯器給予實例方法優先于擴充方法。 如果發現任何實例方法只需要加寬轉換以匹配程序呼叫，則所有擴充方法都將被刪除，編譯器僅繼續使用實例方法候選項。 如果未找到此類實例方法，則繼續使用實例和擴充方法。  
  
     在此步驟中，它消除了調用參數的資料類型無法轉換為重載中定義的參數類型的任何重載。  
  
4. **縮小轉換。** 它消除了任何需要從調用參數類型到定義的參數類型進行縮小轉換的重載。 無論類型檢查開關（[選項嚴格語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)）是`On`還是`Off`，都是如此。  
  
5. **最小加寬。** 編譯器將剩餘的重載成對。 對於每對，它比較已定義參數的資料類型。 如果其中一個重載中的類型都擴展到另一個重載中的相應類型，編譯器將消除後者。 也就是說，它保留需要最少加寬量的重載。  
  
6. **單位候選人。** 它繼續考慮成對的重載，直到只剩下一個重載，並且它解決了對該重載的調用。 如果編譯器無法將重載減少到單個候選項，則會建置錯誤。  
  
 下圖顯示了確定要調用的一組重載版本中哪個的過程。  
  
 ![多載解析程序流程圖](./media/overload-resolution/determine-overloaded-version.gif "在重載版本之間解決")
  
 下面的示例說明了此重載解決過程。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 在第一個調用中，編譯器消除了第一個重載，因為第一個參數`Short`（ ） 的類型縮小到相應參數 （`Byte`的類型）。 然後，它消除了第三個重載，因為第二個重載`Short` `Single`（和 ） 中的每個參數類型在第三個重`Integer`載`Single`（和 ） 中擴展到相應的類型。 第二個重載需要較少的擴展，因此編譯器使用它進行調用。  
  
 在第二個調用中，編譯器不能在縮小的基礎上消除任何重載。 它消除了第三個重載的原因與第一個調用相同，因為它可以調用第二個重載，而參數類型的擴展更少。 但是，編譯器無法在第一個重載和第二個重載之間解析。 每個參數類型都有一個已定義的參數類型，該參數類型將擴展到另`Byte`一`Short`個類型`Single`（`Double`到 ，但為 ） 因此，編譯器生成重載解析錯誤。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>重載可選參數和參數參數  
 如果過程的兩個重載具有相同的簽名，但最後一個參數在一個參數中聲明[為可選](../../../../visual-basic/language-reference/modifiers/optional.md)，另一個參數為[ParamArray，](../../../../visual-basic/language-reference/modifiers/paramarray.md)則編譯器將按如下方式解析對該過程的調用：  
  
|如果調用提供最後一個參數為|編譯器解析對重載的調用，將最後一個參數聲明為|  
|---|---|  
|無值（省略參數）|`Optional`|  
|單個值|`Optional`|  
|逗號分隔清單中的兩個或多個值|`ParamArray`|  
|任何長度的陣列（包括空陣列）|`ParamArray`|  
  
## <a name="see-also"></a>另請參閱

- [可選參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [重載](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [擴充方法](./extension-methods.md)
