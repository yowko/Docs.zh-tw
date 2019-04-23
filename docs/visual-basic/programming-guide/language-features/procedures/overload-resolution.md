---
title: 多載解析 (Visual Basic)
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
ms.openlocfilehash: 4f81c7377423899c142c4270f325bbd7ed20b877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312237"
---
# <a name="overload-resolution-visual-basic"></a>多載解析 (Visual Basic)
當 Visual Basic 編譯器遇到定義在數個多載版本的程序的呼叫時，編譯器必須決定要呼叫的多載。 它會執行下列步驟：  
  
1. **協助工具。** 它會排除任何多載，以防止呼叫程式碼呼叫它的存取層級。  
  
2. **參數的數目。** 它會排除任何在呼叫中定義不同數目的參數所提供的多載。  
  
3. **參數資料類型。** 編譯器會提供於延伸方法的執行個體方法的喜好設定。 如果找不到需要僅限於擴展轉換，來比對程序呼叫的任何執行個體方法，會卸除所有擴充方法，編譯器會繼續進行 僅執行個體方法候選對象。 如果找不到任何這類執行個體方法，它會繼續與執行個體和擴充方法。  
  
     在此步驟中，它會排除任何多載的呼叫的引數的資料類型無法轉換至多載中定義的參數類型。  
  
4. **縮小轉換。** 它會排除任何多載，必須呼叫的引數型別定義的參數類型是縮小轉換。 這是 true 不論類型檢查參數 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`或`Off`。  
  
5. **最小的擴展。** 編譯器會考慮在配對中剩餘的多載。 針對每一組，它會比較定義之參數的資料類型。 如果中其中一個所有多載的型別會擴展為其他對應的型別，則編譯器會排除後者。 也就是說，它會保留需要最少擴展的多載。  
  
6. **單一的候選項目。** 它會繼續考量之前只有一個配對中的多載多載會保留，且能解決該多載的呼叫。 如果編譯器無法減少為單一的候選者的多載，它會產生錯誤。  
  
 下圖顯示決定哪一個多載版本，以呼叫一組程序。  
  
 ![多載解析程序流程圖](./media/overload-resolution/determine-overloaded-version.gif "解析多載的版本")    
  
 下列範例說明此多載解析程序。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 在第一個呼叫中，編譯器會排除第一個多載因為第一個引數的類型 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。 它然後排除第三個多載，因為每個引數類型中的第二個多載 (`Short`並`Single`) 可擴展為對應的型別中的第三個多載 (`Integer`和`Single`)。 第二個多載都需要較少的擴展，因此編譯器會將它用於呼叫。  
  
 在第二個呼叫中，編譯器無法排除任何根據縮小的多載。 基於相同理由，如同第一次呼叫中中,，因為它可以呼叫第二個多載，較不需要擴展的引數類型，它會排除第三個多載。 不過，編譯器無法解析的第一個和第二個多載之間。 各有一個定義的參數類型可擴展成其他對應的類型 (`Byte`來`Short`，但`Single`至`Double`)。 因此，編譯器會產生多載解析錯誤。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>選擇性的多載和 ParamArray 引數  
 如果程序的兩個多載具有相同簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)其中一並[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)在另一個，編譯器會解析為該程序的呼叫如下所示：  
  
|如果呼叫所提供作為最後一個引數|編譯器會解析宣告做為最後一個引數的多載的呼叫|  
|---|---|  
|沒有值 （省略的引數）|`Optional`|  
|單一值|`Optional`|  
|以逗號分隔的清單中的兩個或多個值|`ParamArray`|  
|（包括空的陣列） 任何長度的陣列|`ParamArray`|  
  
## <a name="see-also"></a>另請參閱

- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [程序多載化](./procedure-overloading.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義多個版本的程序](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：多載會採用選擇性參數的程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載不定數目參數的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)
- [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [擴充方法](./extension-methods.md)
