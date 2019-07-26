---
title: 在介面 '<defaultpropertyname>' 的繼承介面成員 '<interfacename1>' 和介面 '<defaultpropertyname>' 的 '<interfacename2>' 之間，Default 屬性存取是模稜兩可的
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: a36cfe8e5496bbfd1941afa8a46086491ae96a2a
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512744"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="8d819-102">在介面 '\<介面名稱 1> > ' 和 '\<defaultpropertyname > '\<介面 '\<的繼承介面成員 ' defaultpropertyname > ' 之間, 預設屬性存取不明確介面名稱 2> > '</span><span class="sxs-lookup"><span data-stu-id="8d819-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>

<span data-ttu-id="8d819-103">介面繼承自兩個介面, 每一個都宣告具有相同名稱的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="8d819-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="8d819-104">編譯器無法解析此預設屬性的存取權, 而不需要限定。</span><span class="sxs-lookup"><span data-stu-id="8d819-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="8d819-105">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="8d819-105">The following example illustrates this.</span></span>

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

<span data-ttu-id="8d819-106">當您指定`testObj(1)`時, 編譯器會嘗試將它解析為預設屬性。</span><span class="sxs-lookup"><span data-stu-id="8d819-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="8d819-107">不過, 因為繼承的介面, 所以有兩個可能的預設屬性, 因此編譯器會發出此錯誤的信號。</span><span class="sxs-lookup"><span data-stu-id="8d819-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>

<span data-ttu-id="8d819-108">**錯誤識別碼:** BC30686</span><span class="sxs-lookup"><span data-stu-id="8d819-108">**Error ID:** BC30686</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8d819-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8d819-109">To correct this error</span></span>

- <span data-ttu-id="8d819-110">避免繼承具有相同名稱的任何成員。</span><span class="sxs-lookup"><span data-stu-id="8d819-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="8d819-111">在上述範例中, 如果`testObj`不需要的任何成員 (例如) `Iface2`, 請將它宣告如下:</span><span class="sxs-lookup"><span data-stu-id="8d819-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>

  ```vb
  Dim testObj As Iface1
  ```

  <span data-ttu-id="8d819-112">\-或-</span><span class="sxs-lookup"><span data-stu-id="8d819-112">\-or-</span></span>

- <span data-ttu-id="8d819-113">在類別中執行繼承介面。</span><span class="sxs-lookup"><span data-stu-id="8d819-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="8d819-114">然後, 您可以使用不同的名稱來執行每個繼承的屬性。</span><span class="sxs-lookup"><span data-stu-id="8d819-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="8d819-115">不過, 只有其中一個可以是實作為類別的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="8d819-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="8d819-116">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="8d819-116">The following example illustrates this.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8d819-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d819-117">See also</span></span>

- [<span data-ttu-id="8d819-118">介面</span><span class="sxs-lookup"><span data-stu-id="8d819-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
