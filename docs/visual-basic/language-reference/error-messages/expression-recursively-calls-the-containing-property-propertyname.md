---
title: "Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42026"
  - "BC42026"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42026"
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

某個屬性定義的 `Set` 程序中的陳述式 \(Statement\)，將值存入屬性的名稱。  
  
 保留屬性值的建議方法是，在屬性的容器 \(Container\) 中定義 `Private` 變數，然後同時在 `Get` 和 `Set` 程序中使用它。  接著，`Set` 程序應該會將收到的值存入這個 `Private` 變數。  
  
 `Get` 程序的行為與 `Function` 程序類似，所以它可以指派一值給屬性名稱，並在遇到 `End Get` 陳述式時傳回控制權。  然而，建議的方法是將 `Private` 變數當做值，併入 [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)。  
  
 `Set` 程序的行為與 `Sub` 程序類似，不會傳回值。  因此，程序或屬性名稱在 `Set` 程序內沒有任何特殊意義，所以您無法將值存入其中。  
  
 下列範例將說明可能會導致這個錯誤的方法，其後則為建議的處理方法。  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 根據預設，這是一個警告訊息。  如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[在 Visual Basic 中設定警告](/visual-studio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID：**BC42026  
  
### 若要更正這個錯誤  
  
-   重新撰寫屬性定義，採用上述範例中說明的建議方法。  
  
## 請參閱  
 [屬性程序](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)