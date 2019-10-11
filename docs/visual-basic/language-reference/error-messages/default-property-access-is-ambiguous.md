---
title: 在介面 '<defaultpropertyname>' 的繼承介面成員 '<interfacename1>' 和介面 '<defaultpropertyname>' 的 '<interfacename2>' 之間，Default 屬性存取是模稜兩可的
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: f76163d58f3f11d3ca946525a1604abc3ebba68d
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250375"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>在介面 ' \<interfacename2 > ' 的介面 ' \<interfacename1 > ' 和 ' \<defaultpropertyname > ' 的繼承介面成員 ' \<defaultpropertyname > ' 之間，預設屬性存取不明確

介面繼承自兩個介面，每一個都宣告具有相同名稱的預設屬性。 編譯器無法解析此預設屬性的存取權，而不需要限定。 下列範例將說明這點。

```vb
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

當您指定 `testObj(1)` 時，編譯器會嘗試將它解析為預設屬性。 不過，因為繼承的介面，所以有兩個可能的預設屬性，因此編譯器會發出此錯誤的信號。

**錯誤識別碼：** BC30686

## <a name="to-correct-this-error"></a>更正這個錯誤

- 避免繼承具有相同名稱的任何成員。 在上述範例中，如果 `testObj` 不需要任何成員（例如 `Iface2`），請依照下列方式將它宣告如下：

  ```vb
  Dim testObj As Iface1
  ```

  \-或-

- 在類別中執行繼承介面。 然後，您可以使用不同的名稱來執行每個繼承的屬性。 不過，只有其中一個可以是實作為類別的預設屬性。 下列範例將說明這點。

  ```vb
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

- [介面](../../programming-guide/language-features/interfaces/index.md)
