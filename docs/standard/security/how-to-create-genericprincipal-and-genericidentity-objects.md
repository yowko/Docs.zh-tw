---
title: HOW TO：建立 GenericPrincipal 和 GenericIdentity 物件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f768242bffe619051779f87e950138ae9fcec6c
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353181"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="d99a5-102">HOW TO：建立 GenericPrincipal 和 GenericIdentity 物件</span><span class="sxs-lookup"><span data-stu-id="d99a5-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

<span data-ttu-id="d99a5-103">您可以使用 <xref:System.Security.Principal.GenericIdentity> 類別搭配 <xref:System.Security.Principal.GenericPrincipal> 類別來建立獨立于 Windows 網域的授權配置。</span><span class="sxs-lookup"><span data-stu-id="d99a5-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="d99a5-104">建立 GenericPrincipal 物件</span><span class="sxs-lookup"><span data-stu-id="d99a5-104">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="d99a5-105">建立身分識別類別的新執行個體，並以您想要它保留的名稱進行初始化。</span><span class="sxs-lookup"><span data-stu-id="d99a5-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="d99a5-106">下列程式碼會建立新的 **GenericIdentity** 物件並以名稱 `MyUser` 進行初始化。</span><span class="sxs-lookup"><span data-stu-id="d99a5-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="d99a5-107">建立 **GenericPrincipal** 類別的新執行個體，並以先前建立的 **GenericIdentity** 物件和代表您要與此主體建立關聯之角色的字串陣列進行初始化。</span><span class="sxs-lookup"><span data-stu-id="d99a5-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="d99a5-108">下列程式碼範例會指定代表系統管理員角色和使用者角色的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="d99a5-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="d99a5-109">然後會使用先前的 **GenericIdentity** 和字串陣列初始化 **GenericPrincipal**。</span><span class="sxs-lookup"><span data-stu-id="d99a5-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="d99a5-110">使用下列程式碼將主體附加至目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="d99a5-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="d99a5-111">這在主體必須經過多次驗證的情況下很有用，必須由應用程式中執行的其他程式碼進行驗證，或者必須由 @no__t 0 物件驗證。</span><span class="sxs-lookup"><span data-stu-id="d99a5-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="d99a5-112">您仍然可以在主體物件上執行角色型驗證，而不需將它附加至執行緒。</span><span class="sxs-lookup"><span data-stu-id="d99a5-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="d99a5-113">如需詳細資訊，請參閱[取代 Principal 物件](../../../docs/standard/security/replacing-a-principal-object.md)。</span><span class="sxs-lookup"><span data-stu-id="d99a5-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="d99a5-114">範例</span><span class="sxs-lookup"><span data-stu-id="d99a5-114">Example</span></span>

<span data-ttu-id="d99a5-115">下列程式碼範例示範如何建立 **GenericPrincipal** 和 **GenericIdentity** 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d99a5-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="d99a5-116">此程式碼會在主控台中顯示這些物件的值。</span><span class="sxs-lookup"><span data-stu-id="d99a5-116">This code displays the values of these objects to the console.</span></span>

```vb
Imports System
Imports System.Security.Principal
Imports System.Threading

Public Class Class1

    Public Shared Sub Main()
        ' Create generic identity.
        Dim myIdentity As New GenericIdentity("MyIdentity")

        ' Create generic principal.
        Dim myStringArray As String() =  {"Manager", "Teller"}
        Dim myPrincipal As New GenericPrincipal(myIdentity, myStringArray)

        ' Attach the principal to the current thread.
        ' This is not required unless repeated validation must occur,
        ' other code in your application must validate, or the
        ' PrincipalPermission object is used.
        Thread.CurrentPrincipal = myPrincipal

        ' Print values to the console.
        Dim name As String = myPrincipal.Identity.Name
        Dim auth As Boolean = myPrincipal.Identity.IsAuthenticated
        Dim isInRole As Boolean = myPrincipal.IsInRole("Manager")

        Console.WriteLine("The name is: {0}", name)
        Console.WriteLine("The isAuthenticated is: {0}", auth)
        Console.WriteLine("Is this a Manager? {0}", isInRole)

    End Sub

End Class
```

```csharp
using System;
using System.Security.Principal;
using System.Threading;

public class Class1
{
    public static int Main(string[] args)
    {
    // Create generic identity.
    GenericIdentity myIdentity = new GenericIdentity("MyIdentity");

    // Create generic principal.
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal =
        new GenericPrincipal(myIdentity, myStringArray);

    // Attach the principal to the current thread.
    // This is not required unless repeated validation must occur,
    // other code in your application must validate, or the
    // PrincipalPermission object is used.
    Thread.CurrentPrincipal = myPrincipal;

    // Print values to the console.
    String name =  myPrincipal.Identity.Name;
    bool auth =  myPrincipal.Identity.IsAuthenticated;
    bool isInRole =  myPrincipal.IsInRole("Manager");

    Console.WriteLine("The name is: {0}", name);
    Console.WriteLine("The isAuthenticated is: {0}", auth);
    Console.WriteLine("Is this a Manager? {0}", isInRole);

    return 0;
    }
}
```

<span data-ttu-id="d99a5-117">執行後，應用程式會顯示與下列類似的輸出。</span><span class="sxs-lookup"><span data-stu-id="d99a5-117">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="d99a5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d99a5-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="d99a5-119">取代 Principal 物件</span><span class="sxs-lookup"><span data-stu-id="d99a5-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)
- [<span data-ttu-id="d99a5-120">Principal 和 Identity 物件</span><span class="sxs-lookup"><span data-stu-id="d99a5-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
