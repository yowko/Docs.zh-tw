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
# <a name="bc30686-default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="73b36-102">BC30686：在介面 ' ' 的繼承介面成員 ' \<defaultpropertyname> ' \<interfacename1> 和 \<defaultpropertyname> 介面 ' \<interfacename2> ' 的 ' ' 之間，預設屬性存取不明確</span><span class="sxs-lookup"><span data-stu-id="73b36-102">BC30686: Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="73b36-103">介面繼承自兩個介面，每個介面都會宣告具有相同名稱的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="73b36-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="73b36-104">編譯器無法在沒有限定的情況下解析此預設屬性的存取。</span><span class="sxs-lookup"><span data-stu-id="73b36-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="73b36-105">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="73b36-105">The following example illustrates this.</span></span>

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

<span data-ttu-id="73b36-106">當您指定時 `testObj(1)` ，編譯器會嘗試將它解析為預設屬性。</span><span class="sxs-lookup"><span data-stu-id="73b36-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="73b36-107">不過，由於繼承的介面，因此有兩個可能的預設屬性，因此編譯器會發出此錯誤。</span><span class="sxs-lookup"><span data-stu-id="73b36-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="73b36-108">**錯誤識別碼：** BC30686</span><span class="sxs-lookup"><span data-stu-id="73b36-108">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="73b36-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="73b36-109">To correct this error</span></span>

- <span data-ttu-id="73b36-110">避免繼承任何具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="73b36-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="73b36-111">在上述範例中，如果不 `testObj` 需要的任何成員（例如），請依照 `Iface2` 下列方式宣告：</span><span class="sxs-lookup"><span data-stu-id="73b36-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="73b36-112">\-或-</span><span class="sxs-lookup"><span data-stu-id="73b36-112">\-or-</span></span>

- <span data-ttu-id="73b36-113">在類別中執行繼承介面。</span><span class="sxs-lookup"><span data-stu-id="73b36-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="73b36-114">然後，您可以使用不同的名稱來執行每個繼承的屬性。</span><span class="sxs-lookup"><span data-stu-id="73b36-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="73b36-115">但是，其中只有一個可以是實類別的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="73b36-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="73b36-116">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="73b36-116">The following example illustrates this.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="73b36-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73b36-117">See also</span></span>

- [<span data-ttu-id="73b36-118">介面</span><span class="sxs-lookup"><span data-stu-id="73b36-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
