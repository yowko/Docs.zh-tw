---
title: "Object Variable Declaration (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "early binding"
  - "declarations, class"
  - "classes [Visual Basic], declaring"
  - "binding, late and early"
  - "object variables, declaring"
  - "variables [Visual Basic], object"
  - "declaring variables, object variables"
  - "declaring classes"
  - "late binding"
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 33
---
# Object Variable Declaration (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

使用一般宣告陳述式來宣告物件變數。  至於資料型別，請指定 `Object` \(也就是 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)\) 或比較特定的類別 \(該物件將要從類別建立\)。  
  
 將變數宣告為 `Object` 與將它宣告為 <xref:System.Object?displayProperty=fullName> 一樣。  
  
 當您使用特定的物件類別宣告變數時，它可以存取該類別及其所繼承的類別公開之所有方法和屬性。  如果您使用 <xref:System.Object> 宣告變數，則它只能存取 <xref:System.Object> 類別的成員，除非您將 `Option Strict Off` 改變為允許晚期繫結。  
  
## 宣告語法  
 用下列語法來宣告物件變數：  
  
```  
Dim variablename As [New] { objectclass | Object }  
```  
  
 您也可在宣告當中指定 [Public](../../../../visual-basic/language-reference/modifiers/public.md)、[Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)、`Protected Friend`、[Private](../../../../visual-basic/language-reference/modifiers/private.md)、[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) 或 [Static](../../../../visual-basic/language-reference/modifiers/static.md)。  下列是有效的範例宣告：  
  
```  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## 晚期繫結與早期繫結  
 有時候特定類別在程式碼執行之前都是未知的。  在這個情況下，您必須以 `Object` 資料型別來宣告物件變數。  這樣可以建立對任何型別物件的一般參考，且會在執行階段指定特定類別。  這稱為「*晚期繫結*」\(Late Binding\)。  晚期繫結需要額外的執行時間。  這也會將您的程式碼限制於最近指派給它的類別方法和屬性。  若您的程式碼試圖存取不同類別的成員，會導致執行階段錯誤。  
  
 當您在編譯期間知道特定的物件時，應該將物件變數宣告為該類別。  這就稱為「*早期繫結*」\(Early Binding\)。  早期繫結可以改善效能，並保證程式碼可以存取所有特定類別的方法和屬性。  在之前的範例宣告中，如果變數 `objA` 僅會使用類別 <xref:System.Windows.Forms.Label?displayProperty=fullName> 的物件，您應該在其宣告中指定 `As System.Windows.Forms.Label`。  
  
### 早期繫結的優點  
 將物件變數宣告為特定的類別有幾個優點：  
  
-   自動型別檢查  
  
-   可以確保能夠存取特定類別的所有成員  
  
-   程式碼編輯器中的 Microsoft IntelliSense 支援  
  
-   改善程式碼的可讀性  
  
-   較少程式碼錯誤  
  
-   在編譯時期而非在執行階段找出錯誤  
  
-   更快的程式碼執行  
  
## 存取物件變數成員  
 當 `Option Strict` 已轉為 `On` 時，物件變數僅能存取在您宣告其類別的方法和屬性。  下列範例將說明這點。  
  
```  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 在此範例中，`p` 僅能使用 <xref:System.Object> 類別本身的成員，其並未包含 `Left` 屬性。  另一方面，將 `q` 宣告為 <xref:System.Windows.Forms.Label> 型別，如此就可使用 <xref:System.Windows.Forms> 命名空間內 <xref:System.Windows.Forms.Label> 類別的所有方法和屬性。  
  
## 物件變數彈性  
 使用繼承階層架構 \(Inheritance Hierarchy\) 中的物件時，您可以選擇用哪一個類別來宣告您的物件變數。  在選擇時，您必須平衡物件指派的彈性和類別成員的存取權限。  例如，考慮指向 <xref:System.Windows.Forms.Form?displayProperty=fullName> 類別的繼承階層架構：  
  
 <xref:System.Object>  
  
 `` <xref:System.ComponentModel.Component>  
  
 `` <xref:System.Windows.Forms.Control>  
  
 `` <xref:System.Windows.Forms.ScrollableControl>  
  
 `` <xref:System.Windows.Forms.ContainerControl>  
  
 `` <xref:System.Windows.Forms.Form>  
  
 假設您的應用程式定義了繼承自 <xref:System.Windows.Forms.Form> 類別的表單類別，稱為 `specialForm`。  您可以宣告一個特別參考 `specialForm` 的物件變數，如下列範例所示。  
  
```  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 上面範例中的宣告會將變數 `nextForm` 限制為 `specialForm` 類別的物件，但是也讓 `specialForm` 的所有方法與屬性可以供 `nextForm` 使用，也可以供繼承自 `specialForm` 的所有類別之所有成員使用。  
  
 您可以將物件變數宣告為 <xref:System.Windows.Forms.Form> 型別，使它較為一般化，如下列範例所示。  
  
```  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 上面範例中的宣告可以讓您將應用程式內的任何表單指派給 `anyForm`。  不過，雖然 `anyForm` 可以存取 <xref:System.Windows.Forms.Form> 類別的所有成員，但是卻不能使用定義給特定表單 \(像是 `specialForm`\) 的其他方法或屬性。  
  
 基底類別 \(Base Class\) 的所有成員都可用於衍生類別 \(Derived Class\)，但衍生類別的其他成員不可用於基底類別。  
  
## 請參閱  
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Assignment](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Declare an Object Variable and Assign an Object to It in Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)   
 [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)