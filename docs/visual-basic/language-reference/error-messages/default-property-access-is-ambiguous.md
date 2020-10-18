---
title: 在介面 '<defaultpropertyname>' 的繼承介面成員 '<interfacename1>' 和介面 '<defaultpropertyname>' 的 '<interfacename2>' 之間，Default 屬性存取是模稜兩可的
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: b7c4c9c75de1b3777f34a70470b89f323a5699f9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162059"
---
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a>BC30686：在介面 ' ' 的繼承介面成員 ' \<defaultpropertyname> ' \<interfacename1> 和 \<defaultpropertyname> 介面 ' \<interfacename2> ' 的 ' ' 之間，預設屬性存取不明確

介面繼承自兩個介面，每個介面都會宣告具有相同名稱的預設屬性。 編譯器無法在沒有限定的情況下解析此預設屬性的存取。 下列範例將說明這點。

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

當您指定時 `testObj(1)` ，編譯器會嘗試將它解析為預設屬性。 不過，由於繼承的介面，因此有兩個可能的預設屬性，因此編譯器會發出此錯誤。

**錯誤識別碼：** BC30686

## <a name="to-correct-this-error"></a>更正這個錯誤

- 避免繼承任何具有相同名稱的成員。 在上述範例中，如果不 `testObj` 需要的任何成員（例如），請依照 `Iface2` 下列方式宣告：

  ```vb
  Dim testObj As Iface1
  ```

  \-或-

- 在類別中執行繼承介面。 然後，您可以使用不同的名稱來執行每個繼承的屬性。 但是，其中只有一個可以是實類別的預設屬性。 下列範例將說明這點。

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
