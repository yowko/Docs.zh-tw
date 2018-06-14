---
title: 預設屬性存取是模稜兩可繼承的介面成員之間&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 1>.<&gt; &#39;和&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 2>&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 65a10067284cad3bf56ecdc441ebefa0a740ef53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590851"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a>預設屬性存取是模稜兩可繼承的介面成員之間&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 1>.<&gt; &#39;和&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 2>&gt;&#39;
介面繼承自兩個介面，其中每個宣告預設屬性具有相同名稱。 編譯器無法解析存取無限制的這個預設屬性。 下列範例將說明這點。  
  
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
  
 當您指定`testObj(1)`，編譯器會嘗試將它解析為預設屬性。 不過，有兩個可能的預設屬性因為繼承的介面，所以編譯器會發出這項錯誤。  
  
 **錯誤 ID:** BC30686  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   避免繼承任何成員具有相同名稱。 在上述範例中，如果`testObj`不需要任何的成員，例如， `Iface2`，然後將它宣告，如下所示：  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     -或-  
  
-   類別中實作繼承的介面。 然後您可以實作每個具有不同名稱的繼承屬性。 不過，其中只有一個元件可以實作類別的預設屬性。 下列範例將說明這點。  
  
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
 [介面](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
