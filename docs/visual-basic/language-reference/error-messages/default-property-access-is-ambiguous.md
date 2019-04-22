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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836346"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-defaultpropertyname-of-interface-interfacename1-and-defaultpropertyname-of-interface-interfacename2"></a><span data-ttu-id="48d36-102">預設屬性存取模稜兩可繼承的介面成員\<defaultpropertyname >' 的介面 '\<介面名稱 1>.< >' 和'\<defaultpropertyname >' 的介面 '\<介面名稱 2&gt >'</span><span class="sxs-lookup"><span data-stu-id="48d36-102">Default property access is ambiguous between the inherited interface members '\<defaultpropertyname>' of interface '\<interfacename1>' and '\<defaultpropertyname>' of interface '\<interfacename2>'</span></span>
<span data-ttu-id="48d36-103">介面繼承自兩個介面，其中每個宣告預設屬性具有相同名稱。</span><span class="sxs-lookup"><span data-stu-id="48d36-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="48d36-104">編譯器無法解析此預設屬性，但是不限定存取。</span><span class="sxs-lookup"><span data-stu-id="48d36-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="48d36-105">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="48d36-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="48d36-106">當您指定`testObj(1)`，編譯器會嘗試將它解析為預設屬性。</span><span class="sxs-lookup"><span data-stu-id="48d36-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="48d36-107">不過，有兩個可能的預設屬性因為繼承的介面，所以編譯器會發出此錯誤。</span><span class="sxs-lookup"><span data-stu-id="48d36-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="48d36-108">**錯誤 ID:** BC30686</span><span class="sxs-lookup"><span data-stu-id="48d36-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="48d36-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="48d36-109">To correct this error</span></span>  
  
-   <span data-ttu-id="48d36-110">避免繼承任何具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="48d36-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="48d36-111">在上述範例中，如果`testObj`不需要任何的成員，例如， `Iface2`，然後將它宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="48d36-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="48d36-112">-或-</span><span class="sxs-lookup"><span data-stu-id="48d36-112">-or-</span></span>  
  
-   <span data-ttu-id="48d36-113">在類別中實作繼承的介面。</span><span class="sxs-lookup"><span data-stu-id="48d36-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="48d36-114">然後您可以實作每個具有不同名稱的繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="48d36-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="48d36-115">不過，其中只有一個元件可以實作類別的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="48d36-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="48d36-116">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="48d36-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48d36-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48d36-117">See also</span></span>

- [<span data-ttu-id="48d36-118">介面</span><span class="sxs-lookup"><span data-stu-id="48d36-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
