---
title: 程式碼存取安全性的基本概念
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c41becaa149b933d46a01f6ada0ea4b29b68fe8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66488027"
---
# <a name="code-access-security-basics"></a>程式碼存取安全性的基本概念

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

以 Common Language Runtime 為目標的每個應用程式 (亦即，每個 Managed 應用程式)，都必須與執行階段的安全性系統互動。 當 Managed 應用程式載入時，其主機會自動授與其權限集合。 這些權限是由主機的本機安全性設定，或是由應用程式所在的沙箱決定。 根據這些權限，應用程式會正確執行，或是產生安全性例外狀況。

桌面應用程式的預設主機可允許程式碼在完全信任中執行。 因此，如果您的應用程式是以桌面為目標，則有不受限制的權限集合。 其他主機或沙箱則為應用程式提供有限的權限集合。 由於權限集合可以在主機之間變更，因此，您必須將應用程式設計為只使用目標主機允許的權限。

您必須熟悉下列程式碼存取安全性概念，才能撰寫以 Common Language Runtime 為目標的有效應用程式：

- **類型安全程式碼**:類型安全程式碼是只以妥善定義、 可允許的方式存取類型的程式碼。 例如，如果有一個有效的物件參考，類型安全程式碼就可以在對應至實際欄位成員的固定位移上存取記憶體。 如果程式碼存取的記憶體，是在屬於該物件公開欄位之記憶體範圍外的任意位移，則不是類型安全程式碼。 若要讓程式碼受益於程式碼存取安全性，您必須使用會產生可驗證類型安全程式碼的編譯器。 如需詳細資訊，請參閱 <<c0> [ 撰寫可驗證的型別安全程式碼](#typesafe_code)本主題稍後的章節。

- **命令式和宣告式語法**:程式碼的要求權限，要求呼叫端擁有指定的權限，並覆寫特定安全性設定 （要有足夠的權限） 與安全性系統互動的 common language runtime 為目標。 您可以使用兩種形式的語法，以程式設計方式來與 .NET Framework 安全性系統互動：宣告式語法和命令式語法。 宣告式呼叫是使用屬性來執行，命令式呼叫是使用程式碼中新的類別執行個體來執行。 有些呼叫只能以命令方式執行，有些呼叫只能以宣告方式執行，而有些呼叫能以其中任一方式執行。

- **安全類別庫**:安全類別庫會使用安全性要求，以確保程式庫的呼叫端擁有存取程式庫公開的資源的權限。 例如，安全類別庫可能有一個用來建立檔案的方法，要求 (demand) 其呼叫端要有權限才能建立檔案。 .NET Framework 由安全類別庫組成。 您應該要知道需要哪些權限，才能存取您的程式碼所使用的任何類別庫。 如需詳細資訊，請參閱 <<c0> [ 使用安全類別庫](#secure_library)本主題稍後的章節。

- **透明程式碼**:從.NET Framework 4 中，除了識別特定的權限，您也必須決定是否執行安全性透明程式碼。 安全性透明程式碼無法呼叫被識別為安全性關鍵的類型或成員。 這個規則適用於完全信任的應用程式，也適用於部分信任的應用程式。 如需詳細資訊，請參閱 <<c0> [ 安全性透明程式碼](../../../docs/framework/misc/security-transparent-code.md)。

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>撰寫可驗證的類型安全程式碼

Just-In-Time (JIT) 編譯會執行驗證程序來檢查程式碼，並嘗試判斷程式碼是否為類型安全。 型別安全的驗證期間證明的程式碼會呼叫*可驗證的類型安全程式碼*。 因為驗證程序或編譯器的限制，程式碼可能是類型安全，但不一定是可驗證的類型安全。 並非所有語言都是類型安全，而某些語言編譯器，例如 Microsoft Visual C++，就無法產生可驗證的類型安全 Managed 程式碼。 若要判斷您使用的語言編譯器是否會產生可驗證的類型安全程式碼，請參閱編譯器的文件。 如果您使用的語言編譯器，避免某些語言建構時，才會產生可驗證的類型安全程式碼時，您可能想要使用[PEVerify 工具](../../../docs/framework/tools/peverify-exe-peverify-tool.md)來判斷您的程式碼是否可驗證的型別安全。

非可驗證的類型安全程式碼，可以在安全性原則允許程式碼略過驗證時，嘗試執行。 不過，因為在執行階段用來隔離組件的機制中，類型安全是不可或缺的一部分，所以如果程式碼違反類型安全的規則，就無法可靠地強制執行安全性。 根據預設，非類型安全的程式碼必須源自本機電腦，才能執行。 因此，行動程式碼應該是類型安全程式碼。

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>使用安全類別庫

如果您的程式碼要求並且被授與類別庫所需的權限，就可以存取類別庫，而類別庫所公開的資源會被保護，以防未經授權的存取。 如果您的程式碼沒有適當的權限，將無法存取類別庫，而惡意程式碼將無法使用您的程式碼來間接存取受保護的資源。 呼叫您的程式碼的其他程式碼，也必須要有類別庫的存取權。 如果沒有，您的程式碼也會被限制執行。

程式碼存取安全性並不會消除撰寫程式碼時發生人為錯誤的可能性。 不過，如果您的應用程式使用安全類別庫來存取受保護的資源，應用程式程式碼的安全性風險就會減少，因為類別庫會仔細檢查潛在的安全性問題。

## <a name="declarative-security"></a>宣告式安全性

宣告式安全性語法會使用[屬性](../../../docs/standard/attributes/index.md)放置安全性資訊[中繼資料](../../../docs/standard/metadata-and-self-describing-components.md)的程式碼。 屬性可以放在組件、類別或成員層級，以指出您想要使用的要求 (request)、要求 (demand) 或覆寫類型。 以 Common Language Runtime 為目標的應用程式中會使用要求 (request) 來通知執行階段安全性系統有關應用程式需要或不想要之權限的資訊。 程式庫中會使用要求 (demand) 和覆寫，以協助保護資源，不讓呼叫端存取，或是覆寫預設安全性行為。

> [!NOTE]
> 在.NET Framework 4 中，已對.NET Framework 安全性模型和術語的重要變更。 如需有關這些變更的詳細資訊，請參閱 <<c0> [ 安全性變更](../../../docs/framework/security/security-changes.md)。

若要使用宣告式安全性呼叫，您必須初始化權限物件的狀態資料，使其表示您需要的特定權限形式。 每個內建權限都有一個被傳遞 <xref:System.Security.Permissions.SecurityAction> 列舉的屬性，以描述您想要執行之安全性作業的類型。 不過，權限也會接受其本身專用的參數。

下列程式碼片段顯示的宣告式語法，可用來要求 (request) 您的程式碼呼叫端必須擁有名為 `MyPermission` 的自訂權限。 此權限是假設的自訂權限，並不存在於 .NET Framework 中。 在此範例中，宣告式呼叫是直接放在類別定義前面，指定此權限會套用到類別層級。 屬性會被傳遞**SecurityAction.Demand**結構，以指定呼叫端必須具備此權限才能執行。

```vb
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1

   Public Sub New()
      'The constructor is protected by the security call.
   End Sub

   Public Sub MyMethod()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'This method is protected by the security call.
   End Sub
End Class
```

```csharp
[MyPermission(SecurityAction.Demand, Unrestricted = true)]
public class MyClass
{
   public MyClass()
   {
      //The constructor is protected by the security call.
   }

   public void MyMethod()
   {
      //This method is protected by the security call.
   }

   public void YourMethod()
   {
      //This method is protected by the security call.
   }
}
```

## <a name="imperative-security"></a>命令式安全性

命令式安全性語法會藉由建立您想要叫用之權限物件的新執行個體來發出安全性呼叫。 您可以使用命令式語法來執行要求 (demand) 和覆寫，但不能執行要求 (request)。

在進行安全性呼叫之前，您必須先初始化權限物件的狀態資料，使其表示您需要的特定權限形式。 例如，建立<xref:System.Security.Permissions.FileIOPermission>物件，您可以使用建構函式來初始化**FileIOPermission**物件，使其表示無限制的存取所有的檔案或無法存取檔案。 或者，您可以使用不同**FileIOPermission**物件，並傳遞參數來指出您想要的存取類型的物件，以代表 （亦即，讀取、 附加或撰寫），而且您想要保護之物件的哪些檔案。

命令式安全性語法除了可以用來叫用單一安全性物件，還可以用來初始化權限集合中的權限群組。 比方說，這項技術是可靠地執行的唯一辦法[判斷提示](../../../docs/framework/misc/using-the-assert-method.md)呼叫一個方法中的多個權限。 使用 <xref:System.Security.PermissionSet> 和 <xref:System.Security.NamedPermissionSet> 類別來建立權限群組，然後呼叫適當的方法來叫用所需的安全性呼叫。

您可以使用命令式語法來執行要求 (demand) 和覆寫，但不能執行要求 (request)。 如果只有在執行階段才會知道初始化權限狀態所需的資訊，您可以使用命令式語法來執行要求 (demand) 和覆寫，而不要使用宣告式語法。 例如，如果您想要確定呼叫端擁有讀取特定檔案的權限，但是在執行階段之前，都不知道該檔案的名稱，請使用命令式要求 (demand)。 當您需要在執行階段判斷某條件是否成立，以及根據測試結果，是否產生安全性要求 (demand) 時，您可能也會選擇使用命令式檢查，而不是宣告式檢查，

下列程式碼片段所顯示的命令式語法，可用來要求 (request) 您的程式碼呼叫端必須擁有名為 `MyPermission` 的自訂權限。 此權限是假設的自訂權限，並不存在於 .NET Framework 中。 `MyMethod` 中建立了一個新的 `MyPermission` 執行個體，只保護具有安全性呼叫的這個方法。

```vb
Public Class MyClass1

   Public Sub New()

   End Sub

   Public Sub MyMethod()
      'MyPermission is demanded using imperative syntax.
      Dim Perm As New MyPermission()
      Perm.Demand()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'YourMethod 'This method is not protected by the security call.
   End Sub
End Class
```

```csharp
public class MyClass {
   public MyClass(){

   }

   public void MyMethod() {
       //MyPermission is demanded using imperative syntax.
       MyPermission Perm = new MyPermission();
       Perm.Demand();
       //This method is protected by the security call.
   }

   public void YourMethod() {
       //This method is not protected by the security call.
   }
}
```

## <a name="using-managed-wrapper-classes"></a>使用 Managed 包裝函式類別

大部分應用程式和元件 (安全程式庫除外) 都不應該直接呼叫 Unmanaged 程式碼。 這有幾個原因。 如果程式碼直接呼叫 Unmanaged 程式碼，可能在許多情況下都不允許它執行，因為程式碼必須被授與高度信任，才能呼叫原生程式碼。 如果將原則修改為可允許這類應用程式執行，可能會大幅降低系統的安全性，而讓應用程式能夠自由執行幾乎任何作業。

此外，有權存取 Unmanaged 程式碼的程式碼可能可以藉由呼叫 Unmanaged API，來執行幾乎任何作業。 比方說，有權呼叫 unmanaged 程式碼的程式碼就不用<xref:System.Security.Permissions.FileIOPermission>存取檔案; 它可以直接呼叫 unmanaged (Win32) 檔案 API，略過受管理的檔案需要的 API **FileIOPermission**。 如果 Managed 程式碼有權呼叫 Unmanaged 程式碼，並且真的直接呼叫 Unmanaged 程式碼，安全性系統將無法可靠地強制執行安全性限制，因為執行階段無法對 Unmanaged 程式碼強制執行這類限制。

如果您想要讓應用程式執行需要存取 Unmanaged 程式碼的作業，其應透過包裝所需功能的受信任 Managed 類別 (如果這種類別存在的話) 來執行。 如果安全類別庫中已經有包裝函式類別存在，請不要建立您自己的包裝函式類別。 包裝函式類別 (必須被授與高度信任，才能呼叫 Unmanaged 程式碼) 負責要求 (demand) 其呼叫端擁有適當的權限。 如果您使用包裝函式類別，您的程式碼只需要要求 (request) 以及被授與包裝函式類別所要求 (demand) 的權限。

## <a name="see-also"></a>另請參閱

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](../../../docs/framework/misc/using-the-assert-method.md)
- [程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)
- [程式碼存取安全性的基本概念](../../../docs/framework/misc/code-access-security-basics.md)
- [屬性](../../../docs/standard/attributes/index.md)
- [中繼資料和自我描述元件](../../../docs/standard/metadata-and-self-describing-components.md)
