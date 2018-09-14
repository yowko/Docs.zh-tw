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
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517069"
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a>如何：建立 GenericPrincipal 和 GenericIdentity 物件
您可以使用<xref:System.Security.Principal.GenericIdentity>類別搭配<xref:System.Security.Principal.GenericPrincipal>類別來建立獨立的 Windows 網域的授權配置。  
  
### <a name="to-create-a-genericprincipal-object"></a>建立 GenericPrincipal 物件  
  
1.  建立身分識別類別的新執行個體，並以您想要它保留的名稱進行初始化。 下列程式碼會建立新的 **GenericIdentity** 物件並以名稱 `MyUser` 進行初始化。  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  建立 **GenericPrincipal** 類別的新執行個體，並以先前建立的 **GenericIdentity** 物件和代表您要與此主體建立關聯之角色的字串陣列進行初始化。 下列程式碼範例會指定代表系統管理員角色和使用者角色的字串陣列。 然後會使用先前的 **GenericIdentity** 和字串陣列初始化 **GenericPrincipal**。  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  使用下列程式碼將主體附加至目前的執行緒。 這會在其中的主體必須驗證數次、 必須經過您的應用程式中執行其他程式碼或它必須通過驗證的情況下很有用<xref:System.Security.Permissions.PrincipalPermission>物件。 您仍然可以在主體物件上執行角色型驗證，而不需將它附加至執行緒。 如需詳細資訊，請參閱[取代 Principal 物件](../../../docs/standard/security/replacing-a-principal-object.md)。  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何建立 **GenericPrincipal** 和 **GenericIdentity** 的執行個體。 此程式碼會在主控台中顯示這些物件的值。  
  
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
  
 執行後，應用程式會顯示與下列類似的輸出。  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Principal.GenericIdentity>  
- <xref:System.Security.Principal.GenericPrincipal>  
- <xref:System.Security.Permissions.PrincipalPermission>  
- [取代 Principal 物件](../../../docs/standard/security/replacing-a-principal-object.md)  
- [Principal 和 Identity 物件](../../../docs/standard/security/principal-and-identity-objects.md)
