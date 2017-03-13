---
title: "Overload Resolution (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, procedures"
  - "overload resolution"
  - "procedures, overloading"
  - "procedures, calling"
  - "procedure overloading, overload resolution"
  - "signatures, procedure"
  - "overloads, resolution"
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Overload Resolution (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

當 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器遇到在數個多載版本中定義的程序呼叫時，編譯器必須決定要呼叫哪一個多載。  編譯器會執行下列步驟以達到這個目的：  
  
1.  **可及性：** 如果存取層級會導致無法從編譯器呼叫程式碼，編譯器會排除這種情況的多載。  
  
2.  **參數的數目：** 如果所定義的參數數目與呼叫中所提供的不同，編譯器會排除這種情況的多載。  
  
3.  **參數資料型別：** 編譯器會先選擇執行個體方法 \(Instance Method\)，再選擇擴充方法。  如果找到任何執行個體方法只需要擴展轉換即可符合程序呼叫，就會捨棄所有擴充方法，編譯器將繼續只使用執行個體方法候選項。  如果找不到上述方法，則會繼續同時使用執行個體和擴充方法。  
  
     在這個步驟中，如果進行呼叫之引數的資料型別無法轉換為多載中所定義的參數型別，編譯器會排除這種情況的多載。  
  
4.  **縮小轉換：** 如果從進行呼叫之引數型別到定義參數型別的轉換，需要使用縮小轉換，編譯器會排除這種情況的多載。  無論型別檢查參數 \([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) 為 `On` 或 `Off`，這都為 true。  
  
5.  **最小擴展：** 編譯器會以成對的方式，考慮如何處理剩餘的多載。  編譯器會比較每對多載的定義參數之資料型別。  如果其中一個多載的型別全部擴大為另一個的對應型別，編譯器會排除後者。  也就是說，它會保留需要最少擴大量的多載。  
  
6.  **單一候選項：** 編譯器會繼續以成對方式考慮多載的處理方式，直到只剩下最後一個多載，然後會將呼叫解析為那一個多載。  如果編譯器無法將多載減少為單一的候選者，則會產生錯誤。  
  
 下圖將說明決定要呼叫其中哪一組多載版本的程序。  
  
 ![多載解析程序流程圖](../../../../visual-basic/programming-guide/language-features/procedures/media/overloadres.gif "OverloadRes")  
在多載版本中進行解析  
  
 下列範例可說明多載解析的處理過程。  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 在第一個呼叫中，因為第一個引數的型別 \(`Short`\) 會縮小對應參數的型別 \(`Byte`\)，所以編譯器會排除第一個多載。  然後，因為第二個多載中的每個引數型別 \(`Short` 和 `Single`\) 都擴展成第三個多載中的對應型別 \(`Integer` 和 `Single`\)，所以會排除第三個多載。  第二個多載需要較少的擴展，因此編譯器會將它用於呼叫。  
  
 在第二個呼叫中，編譯器無法以縮小為基礎來排除任何多載。  因為它可呼叫較不需要擴展引數型別的第二個多載，所以它會用第一個呼叫中的相同理由來排除第三個多載。  不過，編譯器無法在第一個與第二個多載之間進行解析。  每個多載都會有一個定義的參數型別，此型別會擴展為其他多載中的對應型別 \(`Byte` 至 `Short`，但 `Single` 至 `Double`\)。  編譯器因此產生多載解析錯誤。  
  
## 多載的 Optional 和 ParamArray 引數  
 如果程序的兩個多載有相同的簽章，但最後一個參數在某個多載中宣告為 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)，而在另一個多載中宣告為 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)，編譯器會將該程序的呼叫解析如下：  
  
|||  
|-|-|  
|如果呼叫所提供最後一個引數為|編譯器將呼叫解析為宣告最後一個引數的多載，引數為|  
|無數值 \(省略引數\)|`Optional`|  
|單一值|`Optional`|  
|兩個以上在逗號分隔清單內的數值|`ParamArray`|  
|任何長度的陣列 \(包括空陣列\)|`ParamArray`|  
  
## 請參閱  
 [Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)