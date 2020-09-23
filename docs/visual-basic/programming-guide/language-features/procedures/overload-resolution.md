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
ms.openlocfilehash: 9b83eba8efc8dfe14b6ec1cbab270984977198e5
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071360"
---
# <a name="overload-resolution-visual-basic"></a>多載解析 (Visual Basic)

當 Visual Basic 編譯器遇到數個多載版本中定義的程式呼叫時，編譯器必須決定要呼叫的多載。 它會執行下列步驟來執行此動作：  
  
1. **協助工具。** 它會消除具有存取層級的任何多載，以防止呼叫程式碼呼叫它。  
  
2. **參數的數目。** 它會排除定義與呼叫中所提供之參數數目不同的任何多載。  
  
3. **參數資料類型。** 編譯器會針對擴充方法提供實例方法喜好設定。 如果找到的任何實例方法只需要擴輾轉換來符合程序呼叫，則會卸載所有的擴充方法，而且編譯器只會以實例方法候選項目繼續。 如果找不到這類實例方法，它會繼續執行實例和擴充方法。  
  
     在這個步驟中，它會排除呼叫引數的資料類型無法轉換成多載中所定義之參數類型的任何多載。  
  
4. **縮小轉換。** 它會消除任何需要從呼叫引數型別轉換成已定義參數類型的多載。 不論類型檢查參數 ([Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)) 是或，都是 `On` 如此 `Off` 。  
  
5. **最小擴展。** 編譯器會考慮成對的其餘多載。 它會針對每個配對，比較所定義參數的資料類型。 如果其中一個多載中的型別全部擴展至另一個多載中的對應類型，則編譯器會排除後者。 也就是說，它會保留需要最少量擴展的多載。  
  
6. **單一候選。** 它會繼續考慮成對的多載，直到只剩下一個多載，並解析對該多載的呼叫。 如果編譯器無法將多載縮減為單一候選項，則會產生錯誤。  
  
 下圖顯示的程式會判斷要呼叫的一組多載版本。  
  
 ![多載解析程序流程圖](./media/overload-resolution/determine-overloaded-version.gif "在多載版本之間解析")
  
 下列範例說明此多載解析程式。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 在第一個呼叫中，編譯器會排除第一個多載，因為第一個引數 (的類型 `Short`) 會縮小為對應參數 (`Byte`) 的類型。 然後，它會消除第三個多載，因為第二個多載中的每個引數類型 (`Short` ，且 `Single`) 擴大為第三個多載 (`Integer` 和) 中的對應類型 `Single` 第二個多載需要較少的擴展，因此編譯器會使用它來進行呼叫。  
  
 在第二個呼叫中，編譯器無法在縮小的基礎上消除任何多載。 它會將第三個多載排除在第一個呼叫中的相同原因，因為它可以使用較少的引數類型擴展來呼叫第二個多載。 不過，編譯器無法在第一個和第二個多載之間解析。 每個都有一個定義的參數類型，可擴大至其他 (中的對應類型 `Byte` `Short` ，但 `Single` `Double`) 。 因此，編譯器會產生多載解析錯誤。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>多載的選擇性和 ParamArray 引數  

 如果程式的兩個多載具有相同的簽章，但最後一個參數是在另一個[參數中宣告](../../../language-reference/modifiers/paramarray.md)為[選擇性](../../../language-reference/modifiers/optional.md)，則編譯器會解析該程式的呼叫，如下所示：  
  
|如果呼叫將最後一個引數提供為|編譯器會將宣告最後一個引數的多載呼叫解析為|  
|---|---|  
|未省略值 (引數) |`Optional`|  
|單一值|`Optional`|  
|逗點分隔清單中的兩個或多個值|`ParamArray`|  
|任何長度的陣列 (包括空陣列) |`ParamArray`|  
  
## <a name="see-also"></a>另請參閱

- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載](../../../language-reference/modifiers/overloads.md)
- [擴充方法](./extension-methods.md)
