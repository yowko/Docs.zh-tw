---
title: 作法：建立 GenericPrincipal 和 GenericIdentity 物件
ms.date: 07/15/2020
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
ms.openlocfilehash: 903d636938c47850951330d7936d95470441607e
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87557212"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="f0ae2-102">作法：建立 GenericPrincipal 和 GenericIdentity 物件</span><span class="sxs-lookup"><span data-stu-id="f0ae2-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>

> [!NOTE]
> <span data-ttu-id="f0ae2-103">本文適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="f0ae2-104">如需 ASP.NET Core 的詳細資訊，請參閱[ASP.NET Core 安全性的總覽](https://docs.microsoft.com/aspnet/core/security/)。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-104">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](https://docs.microsoft.com/aspnet/core/security/).</span></span>

<span data-ttu-id="f0ae2-105">您可以 <xref:System.Security.Principal.GenericIdentity> 搭配類別使用類別 <xref:System.Security.Principal.GenericPrincipal> ，以建立獨立于 Windows 網域的授權配置。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-105">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>

### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="f0ae2-106">建立 GenericPrincipal 物件</span><span class="sxs-lookup"><span data-stu-id="f0ae2-106">To create a GenericPrincipal object</span></span>

1. <span data-ttu-id="f0ae2-107">建立身分識別類別的新執行個體，並以您想要它保留的名稱進行初始化。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-107">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="f0ae2-108">下列程式碼會建立新的 **GenericIdentity** 物件並以名稱 `MyUser` 進行初始化。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-108">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>

    ```vb
    Dim myIdentity As New GenericIdentity("MyUser")
    ```

    ```csharp
    GenericIdentity myIdentity = new GenericIdentity("MyUser");
    ```

2. <span data-ttu-id="f0ae2-109">建立 **GenericPrincipal** 類別的新執行個體，並以先前建立的 **GenericIdentity** 物件和代表您要與此主體建立關聯之角色的字串陣列進行初始化。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-109">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="f0ae2-110">下列程式碼範例會指定代表系統管理員角色和使用者角色的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-110">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="f0ae2-111">然後會使用先前的 **GenericIdentity** 和字串陣列初始化 **GenericPrincipal**。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-111">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>

    ```vb
    Dim myStringArray As String() = {"Manager", "Teller"}
    DIm myPrincipal As New GenericPrincipal(myIdentity, myStringArray)
    ```

    ```csharp
    String[] myStringArray = {"Manager", "Teller"};
    GenericPrincipal myPrincipal = new GenericPrincipal(myIdentity, myStringArray);
    ```

3. <span data-ttu-id="f0ae2-112">使用下列程式碼將主體附加至目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-112">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="f0ae2-113">這在主體必須經過多次驗證的情況下很有用，必須由應用程式中執行的其他程式碼進行驗證，或者必須由 <xref:System.Security.Permissions.PrincipalPermission> 物件驗證。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-113">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="f0ae2-114">您仍然可以在主體物件上執行角色型驗證，而不需將它附加至執行緒。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-114">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="f0ae2-115">如需詳細資訊，請參閱[取代 Principal 物件](replacing-a-principal-object.md)。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-115">For more information, see [Replacing a Principal Object](replacing-a-principal-object.md).</span></span>

    ```vb
    Thread.CurrentPrincipal = myPrincipal
    ```

    ```csharp
    Thread.CurrentPrincipal = myPrincipal;
    ```

## <a name="example"></a><span data-ttu-id="f0ae2-116">範例</span><span class="sxs-lookup"><span data-stu-id="f0ae2-116">Example</span></span>

<span data-ttu-id="f0ae2-117">下列程式碼範例示範如何建立 **GenericPrincipal** 和 **GenericIdentity** 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-117">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="f0ae2-118">此程式碼會在主控台中顯示這些物件的值。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-118">This code displays the values of these objects to the console.</span></span>

```vb
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

<span data-ttu-id="f0ae2-119">執行後，應用程式會顯示與下列類似的輸出。</span><span class="sxs-lookup"><span data-stu-id="f0ae2-119">When executed, the application displays output similar to the following.</span></span>

```console
The Name is: MyIdentity
The IsAuthenticated is: True
Is this a Manager? True
```

## <a name="see-also"></a><span data-ttu-id="f0ae2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0ae2-120">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>
- <xref:System.Security.Principal.GenericPrincipal>
- <xref:System.Security.Permissions.PrincipalPermission>
- [<span data-ttu-id="f0ae2-121">取代 Principal 物件</span><span class="sxs-lookup"><span data-stu-id="f0ae2-121">Replacing a Principal Object</span></span>](replacing-a-principal-object.md)
- [<span data-ttu-id="f0ae2-122">Principal 和 Identity 物件</span><span class="sxs-lookup"><span data-stu-id="f0ae2-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
