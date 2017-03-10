---
title: "Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30933"
  - "bc30933"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "overload resolution, with late-bound argument"
  - "BC30933"
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

編譯器 \(Compiler\) 正嘗試將參考解析為多載屬性或程序，但是因為引數型別為 `Object` 而參考的物件具有介面的資料型別，所以參考失敗。  `Object` 引數會強制編譯器將參考解析為晚期繫結。  
  
 在這些情況下，編譯器會透過實作類別解析多載，而非透過基礎介面。  如果類別重新命名其中一個多載版本，則因為名稱不同，編譯器不會將該版本視為多載。  這也會導致編譯器在解析參考時忽略重新命名的版本，即使重新命名的版本可能才是正確的選擇。  
  
 **錯誤 ID：**BC30933  
  
### 若要更正這個錯誤  
  
-   使用 `CType`，將引數從 `Object` 轉型為您要呼叫之多載簽章所指定的型別。  
  
     請注意，這對於將參考物件轉型為基礎介面並沒有幫助。  您必須轉型引數，避免發生這個錯誤。  
  
## 範例  
 下列範例會顯示在編譯時期造成這個錯誤的多載 `Sub` 程序。  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 在上述範例中，如果編譯器允許呼叫 `s1` 為寫入，則會透過類別 `c1` 執行解析，而非透過介面 `i1`。  這表示編譯器不會考慮 `s2`，因為即使 `i1` 所定義的才是正確選擇，但是它在 `c1` 中的名稱已經不同。  
  
 您可以變更下列其中一行程式碼的呼叫，更正這個錯誤：  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 上述程式碼中的每一行都會明確將 `Object` 變數 `o1` 轉型為針對多載所定義的其中一個參數型別。  
  
## 請參閱  
 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Overload Resolution](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)