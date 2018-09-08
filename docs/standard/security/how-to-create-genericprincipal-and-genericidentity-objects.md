---
title: 如何：建立 GenericPrincipal 和 GenericIdentity 物件
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
ms.openlocfilehash: 79b5e05fe9133eb2282eedefa001e64ece5e0f57
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183794"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="89f50-102">如何：建立 GenericPrincipal 和 GenericIdentity 物件</span><span class="sxs-lookup"><span data-stu-id="89f50-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>
<span data-ttu-id="89f50-103">您可以使用<xref:System.Security.Principal.GenericIdentity>類別搭配<xref:System.Security.Principal.GenericPrincipal>類別來建立獨立的 Windows 網域的授權配置。</span><span class="sxs-lookup"><span data-stu-id="89f50-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>  
  
### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="89f50-104">建立 GenericPrincipal 物件</span><span class="sxs-lookup"><span data-stu-id="89f50-104">To create a GenericPrincipal object</span></span>  
  
1.  <span data-ttu-id="89f50-105">建立身分識別類別的新執行個體，並以您想要它保留的名稱進行初始化。</span><span class="sxs-lookup"><span data-stu-id="89f50-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="89f50-106">下列程式碼會建立新的 **GenericIdentity** 物件並以名稱 `MyUser` 進行初始化。</span><span class="sxs-lookup"><span data-stu-id="89f50-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  <span data-ttu-id="89f50-107">建立 **GenericPrincipal** 類別的新執行個體，並以先前建立的 **GenericIdentity** 物件和代表您要與此主體建立關聯之角色的字串陣列進行初始化。</span><span class="sxs-lookup"><span data-stu-id="89f50-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="89f50-108">下列程式碼範例會指定代表系統管理員角色和使用者角色的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="89f50-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="89f50-109">然後會使用先前的 **GenericIdentity** 和字串陣列初始化 **GenericPrincipal**。</span><span class="sxs-lookup"><span data-stu-id="89f50-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  <span data-ttu-id="89f50-110">使用下列程式碼將主體附加至目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="89f50-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="89f50-111">這會在其中的主體必須驗證數次、 必須經過您的應用程式中執行其他程式碼或它必須通過驗證的情況下很有用<xref:System.Security.Permissions.PrincipalPermission>物件。</span><span class="sxs-lookup"><span data-stu-id="89f50-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="89f50-112">您仍然可以在主體物件上執行角色型驗證，而不需將它附加至執行緒。</span><span class="sxs-lookup"><span data-stu-id="89f50-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="89f50-113">如需詳細資訊，請參閱[取代 Principal 物件](../../../docs/standard/security/replacing-a-principal-object.md)。</span><span class="sxs-lookup"><span data-stu-id="89f50-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a><span data-ttu-id="89f50-114">範例</span><span class="sxs-lookup"><span data-stu-id="89f50-114">Example</span></span>  
 <span data-ttu-id="89f50-115">下列程式碼範例示範如何建立 **GenericPrincipal** 和 **GenericIdentity** 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="89f50-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="89f50-116">此程式碼會在主控台中顯示這些物件的值。</span><span class="sxs-lookup"><span data-stu-id="89f50-116">This code displays the values of these objects to the console.</span></span>  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim MyIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim MyStringArray As String() =  {"Manager", "Teller"}  
        Dim MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = MyPrincipal  
  
        ' Print values to the console.  
        Dim Name As String = MyPrincipal.Identity.Name  
        Dim Auth As Boolean = MyPrincipal.Identity.IsAuthenticated  
        Dim IsInRole As Boolean = MyPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The Name is: {0}", Name)  
        Console.WriteLine("The IsAuthenticated is: {0}", Auth)  
        Console.WriteLine("Is this a Manager? {0}", IsInRole)  
  
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
    GenericIdentity MyIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal =   
        new GenericPrincipal(MyIdentity, MyStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = MyPrincipal;  
  
    // Print values to the console.  
    String Name =  MyPrincipal.Identity.Name;  
    bool Auth =  MyPrincipal.Identity.IsAuthenticated;   
    bool IsInRole =  MyPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The Name is: {0}", Name);  
    Console.WriteLine("The IsAuthenticated is: {0}", Auth);  
    Console.WriteLine("Is this a Manager? {0}", IsInRole);  
  
    return 0;  
    }  
}  
```  
  
 <span data-ttu-id="89f50-117">執行後，應用程式會顯示與下列類似的輸出。</span><span class="sxs-lookup"><span data-stu-id="89f50-117">When executed, the application displays output similar to the following.</span></span>  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a><span data-ttu-id="89f50-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89f50-118">See also</span></span>

- <xref:System.Security.Principal.GenericIdentity>  
- <xref:System.Security.Principal.GenericPrincipal>  
- <xref:System.Security.Permissions.PrincipalPermission>  
- [<span data-ttu-id="89f50-119">取代 Principal 物件</span><span class="sxs-lookup"><span data-stu-id="89f50-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)  
- [<span data-ttu-id="89f50-120">Principal 和 Identity 物件</span><span class="sxs-lookup"><span data-stu-id="89f50-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
