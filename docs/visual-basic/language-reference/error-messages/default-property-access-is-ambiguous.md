---
title: 在介面 '<defaultpropertyname>' 的繼承介面成員 '<interfacename1>' 和介面 '<defaultpropertyname>' 的 '<interfacename2>' 之間，Default 屬性存取是模稜兩可的
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 5f058c8e7d480b9145452ae85f186a6ac2ed0d56
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836346"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>預設屬性存取模稜兩可繼承的介面成員\<defaultpropertyname >' 的介面 '\<介面名稱 1>.< >' 和'\<defaultpropertyname >' 的介面 '\<介面名稱 2&gt >'
介面繼承自兩個介面，其中每個宣告預設屬性具有相同名稱。 編譯器無法解析此預設屬性，但是不限定存取。 下列範例將說明這點。  
  
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
  
 當您指定`testObj(1)`，編譯器會嘗試將它解析為預設屬性。 不過，有兩個可能的預設屬性因為繼承的介面，所以編譯器會發出此錯誤。  
  
 **錯誤 ID:** BC30686  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   避免繼承任何具有相同名稱的成員。 在上述範例中，如果`testObj`不需要任何的成員，例如， `Iface2`，然後將它宣告，如下所示：  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     -或-  
  
-   在類別中實作繼承的介面。 然後您可以實作每個具有不同名稱的繼承屬性。 不過，其中只有一個元件可以實作類別的預設屬性。 下列範例將說明這點。  
  
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
  
## <a name="see-also"></a>另請參閱

- [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
