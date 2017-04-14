---
title: "How to: Create GenericPrincipal and GenericIdentity Objects | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Creating Generic Identity Objects"
  - "GenericPrincipal Objects"
  - "Creating GenericPrincipal Objects"
  - "GenericIdentity Objects"
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# How to: Create GenericPrincipal and GenericIdentity Objects
您可以將 <xref:System.Security.Principal.GenericIdentity> 類別與 <xref:System.Security.Principal.GenericPrincipal> 類別配合使用，以建立獨立存在於 Windows NT 或 Windows 2000 網域之外的授權配置。  
  
### 若要建立 GenericPrincipal 物件  
  
1.  建立識別類別的新執行個體，並以您想要它保留的名稱將它初始化。  下列程式碼會建立新的 **GenericIdentity** 物件，並以 `MyUser` 名稱將它初始化。  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  建立 **GenericPrincipal** 類別的新執行個體，並以先前建立的 **GenericIdentity** 物件和表示您要與此主體相關的角色之字串陣列加以初始化。  下列程式碼範例指定代表系統管理員角色和使用者角色的字串陣列。  接著以先前的 **GenericIdentity** 和字串陣列初始化 **GenericPrincipal**。  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  使用下列程式碼將主體附加至目前執行緒。  因為這一點在主體必須經過驗證許多次的情況下，是很重要的，所以該主體必須經過被應用程式中執行的其他程式碼驗證，或是必須經過 <xref:System.Security.Permissions.PrincipalPermission> 物件驗證。  您仍然可以在主體物件上執行角色架構驗證，而不將它附加到執行緒。  如需詳細資訊，請參閱[取代主體物件](../../../docs/standard/security/replacing-a-principal-object.md)。  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## 範例  
 下列程式碼範例示範如何建立 **GenericPrincipal** 和 **GenericIdentity** 的執行個體。  這個程式碼將這些物件的值顯示到主控台。  
  
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
  
 執行後，應用程式顯示類似下列的輸出。  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## 請參閱  
 <xref:System.Security.Principal.GenericIdentity>   
 <xref:System.Security.Principal.GenericPrincipal>   
 <xref:System.Security.Permissions.PrincipalPermission>   
 [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md)   
 [Principal and Identity Objects](../../../docs/standard/security/principal-and-identity-objects.md)