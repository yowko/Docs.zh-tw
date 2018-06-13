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
ms.openlocfilehash: d95589eb16f45eeff10692cdc897bf65ebe2d84e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653425"
---
# <a name="overload-resolution-visual-basic"></a>多載解析 (Visual Basic)
當 Visual Basic 編譯器遇到定義在數個多載版本的程序的呼叫時，編譯器必須決定要呼叫的多載。 它會執行下列步驟：  
  
1.  **協助工具。** 這可避免多載可防止呼叫程式碼呼叫它的存取層級。  
  
2.  **參數數目。** 這可避免在呼叫中定義不同的參數數目所提供的任何多載。  
  
3.  **參數資料類型。** 編譯器會提供執行個體方法的喜好設定，透過擴充方法。 如果找不到，只需要擴展轉換來比對程序呼叫的任何執行個體方法，會卸除所有擴充方法，編譯器會繼續進行 僅執行個體方法的候選項目。 如果找不到任何這類執行個體方法，它會繼續與執行個體和擴充方法。  
  
     在此步驟中，它會排除其呼叫之引數的資料類型無法轉換成在多載定義的參數類型的任何多載。  
  
4.  **縮小轉換。** 這可避免必須呼叫的引數型別定義的參數類型是縮小轉換的任何多載。 這是，則為 true 的型別檢查是否切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`或`Off`。  
  
5.  **最小的擴展。** 編譯器會考慮在配對中其餘的多載。 針對每一組，它會比較定義之參數的資料型別。 如果其中一種所有多載的型別擴展為其他對應的型別，編譯器會排除後者。 也就是說，它會保留需要最少擴展的多載。  
  
6.  **單一的候選項目。** 它會繼續直到只有一個配對中的多載多載會維持為，，並會將該多載呼叫解析考量。 如果編譯器無法減少為單一的候選項目多載，它會產生錯誤。  
  
 下圖顯示決定哪一組多載版本，呼叫的程序。  
  
 ![多載解析程序流程圖](./media/overloadres.gif "OverloadRes")  
在多載版本中進行解析  
  
 下列範例說明這個多載解析程序。  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 在第一個呼叫中，編譯器會排除第一個多載因為第一個引數的類型 (`Short`) 的範圍縮小，對應參數的型別 (`Byte`)。 它然後排除第三個多載，因為每個引數類型中的第二個多載 (`Short`和`Single`) 可擴展為對應的型別中的第三個多載 (`Integer`和`Single`)。 第二個多載都需要較少的擴展，因此編譯器會使用它的呼叫。  
  
 在第二個呼叫中，編譯器無法排除任何多載根據縮小。 它也消除了第三個多載基於相同理由，如同第一個呼叫，因為它可以呼叫具有較少的擴展引數類型的第二個多載。 不過，編譯器無法解析的第一個和第二個多載之間。 各有一個定義的參數類型可擴展成中的其他對應的類型 (`Byte`至`Short`，但`Single`至`Double`)。 因此，編譯器會產生多載解析錯誤。  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>選擇性的多載和 ParamArray 引數  
 如果程序的兩個多載具有相同的簽章，不同之處在於最後一個參數宣告[選擇性](../../../../visual-basic/language-reference/modifiers/optional.md)之一和[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) ，則編譯器會解析與該程序呼叫如下所示：  
  
|如果呼叫可提供做為最後的引數|編譯器將呼叫解析為宣告做為最後的引數的多載|  
|---|---|  
|沒有值 （省略的引數）|`Optional`|  
|單一值|`Optional`|  
|以逗號分隔的清單中的兩個或多個值|`ParamArray`|  
|陣列的長度 （包括空的陣列）|`ParamArray`|  
  
## <a name="see-also"></a>另請參閱  
 [選擇性參數](./optional-parameters.md)  
 [參數陣列](./parameter-arrays.md)  
 [程序多載化](./procedure-overloading.md)  
 [程序的疑難排解](./troubleshooting-procedures.md)  
 [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)  
 [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)  
 [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [多載化程序的考慮因素](./considerations-in-overloading-procedures.md)  
 [多載](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [擴充方法](./extension-methods.md)
