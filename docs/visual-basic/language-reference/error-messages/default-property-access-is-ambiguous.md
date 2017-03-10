---
title: "Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30686"
  - "bc30686"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30686"
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

介面繼承自兩個介面，而這兩個介面都有以相同的名稱宣告預設屬性。  在不使用完整名稱的情況下，編譯器無法解析這個預設屬性的存取。  下列範例將說明這點。  
  
```  
Public Interface Iface1  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface2  
    Default Property prop(ByVal arg As Integer) As Integer  
End Interface  
Public Interface Iface3  
    Inherits Iface1, Iface2  
End Interface  
Public Class testClass  
    Public Sub accessDefaultProperty()  
        Dim testObj As Iface3  
        Dim testInt As Integer = testObj(1)  
    End Sub  
End Class  
```  
  
 當您指定 `testObj(1)` 時，編譯器會嘗試將其解析為預設屬性。  然而，由於繼承介面的關係，有可能出現兩個預設屬性，所以編譯器會發出這個錯誤。  
  
 **錯誤 ID**：BC30686  
  
### 若要更正這個錯誤  
  
-   避免繼承有相同名稱的任何成員。  在前面的範例中，如果 `testObj` 並不需要 `Iface2` 的任何成員，那麼請以下列方式宣告：  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     \-或\-  
  
-   在類別中實作繼承介面。  然後，您可以使用不同的名稱實作每個繼承屬性。  然而，其中只有一項可以是實作類別的預設屬性。  下列範例將說明這點。  
  
    ```  
    Public Class useIface3  
        Implements Iface3  
        Default Public Property prop1(ByVal arg As Integer) As Integer Implements Iface1.prop  
            ' Insert code to define Get and Set procedures for prop1.  
        End Property  
        Public Property prop2(ByVal arg As Integer) As Integer Implements Iface2.prop  
            ' Insert code to define Get and Set procedures for prop2.  
        End Property  
    End Class  
    ```  
  
## 請參閱  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)