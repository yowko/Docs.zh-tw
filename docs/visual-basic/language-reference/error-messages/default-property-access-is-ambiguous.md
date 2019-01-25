---
title: 預設屬性存取模稜兩可繼承的介面成員&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 1>.<&gt; &#39;和&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 2&gt&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30686
- bc30686
helpviewer_keywords:
- BC30686
ms.assetid: 784fefec-ef57-48cf-b960-957df419b439
ms.openlocfilehash: 1fae63506a35eb046676214a2b6c52977f24645d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518640"
---
# <a name="default-property-access-is-ambiguous-between-the-inherited-interface-members-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename1gt39-and-39ltdefaultpropertynamegt39-of-interface-39ltinterfacename2gt39"></a><span data-ttu-id="99e2a-102">預設屬性存取模稜兩可繼承的介面成員&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 1>.<&gt; &#39;和&#39; &lt;defaultpropertyname&gt; &#39;介面的&#39;&lt;介面名稱 2&gt&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="99e2a-102">Default property access is ambiguous between the inherited interface members &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename1&gt;&#39; and &#39;&lt;defaultpropertyname&gt;&#39; of interface &#39;&lt;interfacename2&gt;&#39;</span></span>
<span data-ttu-id="99e2a-103">介面繼承自兩個介面，其中每個宣告預設屬性具有相同名稱。</span><span class="sxs-lookup"><span data-stu-id="99e2a-103">An interface inherits from two interfaces, each of which declares a default property with the same name.</span></span> <span data-ttu-id="99e2a-104">編譯器無法解析此預設屬性，但是不限定存取。</span><span class="sxs-lookup"><span data-stu-id="99e2a-104">The compiler cannot resolve an access to this default property without qualification.</span></span> <span data-ttu-id="99e2a-105">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="99e2a-105">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="99e2a-106">當您指定`testObj(1)`，編譯器會嘗試將它解析為預設屬性。</span><span class="sxs-lookup"><span data-stu-id="99e2a-106">When you specify `testObj(1)`, the compiler tries to resolve it to the default property.</span></span> <span data-ttu-id="99e2a-107">不過，有兩個可能的預設屬性因為繼承的介面，所以編譯器會發出此錯誤。</span><span class="sxs-lookup"><span data-stu-id="99e2a-107">However, there are two possible default properties because of the inherited interfaces, so the compiler signals this error.</span></span>  
  
 <span data-ttu-id="99e2a-108">**錯誤 ID:** BC30686</span><span class="sxs-lookup"><span data-stu-id="99e2a-108">**Error ID:** BC30686</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="99e2a-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="99e2a-109">To correct this error</span></span>  
  
-   <span data-ttu-id="99e2a-110">避免繼承任何具有相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="99e2a-110">Avoid inheriting any members with the same name.</span></span> <span data-ttu-id="99e2a-111">在上述範例中，如果`testObj`不需要任何的成員，例如， `Iface2`，然後將它宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="99e2a-111">In the preceding example, if `testObj` does not need any of the members of, say, `Iface2`, then declare it as follows:</span></span>  
  
    ```  
    Dim testObj As Iface1  
    ```  
  
     <span data-ttu-id="99e2a-112">-或-</span><span class="sxs-lookup"><span data-stu-id="99e2a-112">-or-</span></span>  
  
-   <span data-ttu-id="99e2a-113">在類別中實作繼承的介面。</span><span class="sxs-lookup"><span data-stu-id="99e2a-113">Implement the inheriting interface in a class.</span></span> <span data-ttu-id="99e2a-114">然後您可以實作每個具有不同名稱的繼承屬性。</span><span class="sxs-lookup"><span data-stu-id="99e2a-114">Then you can implement each of the inherited properties with different names.</span></span> <span data-ttu-id="99e2a-115">不過，其中只有一個元件可以實作類別的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="99e2a-115">However, only one of them can be the default property of the implementing class.</span></span> <span data-ttu-id="99e2a-116">下列範例將說明這點。</span><span class="sxs-lookup"><span data-stu-id="99e2a-116">The following example illustrates this.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99e2a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99e2a-117">See also</span></span>
- [<span data-ttu-id="99e2a-118">介面</span><span class="sxs-lookup"><span data-stu-id="99e2a-118">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
