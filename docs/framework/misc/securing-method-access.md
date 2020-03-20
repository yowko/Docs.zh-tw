---
title: 設定方法存取的安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- code security, method access
- secure coding, method access
- security [.NET Framework], method access
- method access security
ms.assetid: f7c2d6ec-3b18-4e0e-9991-acd97189d818
ms.openlocfilehash: a9e1226483eaa02dc8dc3dfb741e3df6b2985fbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181150"
---
# <a name="securing-method-access"></a>設定方法存取的安全性
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 有些方法可能不適合讓未受信任的任意程式碼呼叫。 這類方法會造成一些風險：方法可能會提供一些受限制的資訊；它可能會認定傳遞給它的任何資訊；它可能不會對參數執行錯誤檢查；它可能會因錯誤的參數發生問題或執行有害的動作。 您應該留意這些情況，並採取動作來協助保護方法。  
  
 在某些情況下，您可能需要限制不提供公用用途但仍必須是公用的方法。 例如，您可能會需要有跨您自己的 Dll 呼叫的介面，因此它必須是公用的，但為了防止客戶使用它，或惡意程式碼利用進入點進入您的元件，所以您不想將它公開。 另一個限制不提供公用用途 (但必須是公用) 方法的常見原因，是為了避免記錄和支援可能非常內部的介面。  
  
 Managed 程式碼提供數種方式以限制方法存取：  
  
- 限制類別、 組件、 或衍生類別的存取範圍，如果其可以信任。 這是最簡單限制方法存取權的方式。 請注意，一般而言，衍生類別可能比它們衍生自的類別還不可靠，雖然在某些情況下它們共用父類別的識別。 特別是，不要推斷來自**受保護**的關鍵字的信任，這不一定在安全上下文中使用。  
  
- 將方法訪問限制為指定標識的調用方，實質上是您選擇的任何特定[證據](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29)（強式名稱、發行者、區域等）。  
  
- 限制具有您選取權限之呼叫端的方法存取權。  
  
 同樣地，宣告式安全性可讓您控制類別的繼承。 您可以使用**繼承需求**執行以下操作：  
  
- 需要衍生類別以具有指定身分識別或權限。  
  
- 需要覆寫指定方法的衍生類別以具有指定身分識別或權限。  
  
 下列範例示範如何以要求呼叫端使用特定強勢名稱，來協助保護限制存取的公用類別。 此示例使用<xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute>具有強式名稱**的 Demand。** 有關如何使用強式名稱對程式集進行簽名的基於任務的資訊，請參閱[創建和使用強式名稱程式集](../../standard/assembly/create-use-strong-named.md)。  
  
```vb  
<StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey := "…hex…", Name := "App1", Version := "0.0.0.0")>  _  
Public Class Class1  
End Class  
```  
  
```csharp  
[StrongNameIdentityPermissionAttribute(SecurityAction.Demand, PublicKey="…hex…", Name="App1", Version="0.0.0.0")]  
public class Class1  
{  
  
}
```  
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a>將類別和成員排除在未受信任程式碼的使用之外  
 使用這一節中所示的宣告，來防止部分信任程式碼使用特定類別和方法，以及屬性和事件。 您可以藉由將這些宣告套用至類別，來為所有方法、 屬性和事件套用保護，不過請注意存取欄位不會受宣告式安全性影響。 也請注意，連結要求協助防範立即呼叫端，且可能還是會受到引誘攻擊。  
  
> [!NOTE]
> 在 .NET 框架 4 中引入了一種新的透明度模型。 [安全透明代碼，2 級](security-transparent-code-level-2.md)模型使用<xref:System.Security.SecurityCriticalAttribute>屬性標識安全代碼。 安全性關鍵的程式碼需要呼叫端和繼承者兩者都完全受信任。 從舊版 .NET Framework 程式碼存取安全性規則的組件可以呼叫層級 2 組件。 在此情況下，安全性關鍵屬性會被視為完全信任的連結要求。  
  
 在強命名程式集中[，LinkDemand](link-demands.md)應用於其中所有可公開訪問的方法、屬性和事件，以將其使用限制為完全受信任的調用方。 若要停用此功能，您必須套用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性。 因此，只有不帶正負號的組件或具有此屬性的組件需要明確地標示類別，以排除不受信任的呼叫端您可以使用這些宣告以標記非為不受信任的呼叫端之類型的子集。  
  
 下列範例示範如何防止不受信任的程式碼使用類別和成員。  
  
 針對公用未密封的類別：  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
Public Class CanDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public class CanDeriveFromMe  
{  
}  
```  
  
 針對公用密封的類別：  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
NotInheritable Public Class CannotDeriveFromMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public sealed class CannotDeriveFromMe  
{  
}  
```  
  
 針對公用抽象類別：  
  
```vb  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name := "FullTrust"), _  
System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name := "FullTrust")>  _  
MustInherit Public Class CannotCreateInstanceOfMe_CanCastToMe  
End Class  
```  
  
```csharp  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
public abstract class CannotCreateInstanceOfMe_CanCastToMe {}  
```  
  
 針對公用虛擬函式：  
  
```vb  
Class Base1
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overridable Sub CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Base1  
```  
  
```csharp  
class Base1
{  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name="FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]  
    public virtual void CanOverrideOrCallMe() {}  
}  
```  
  
 針對公用抽象函式：  
  
```vb  
MustInherit Class Base2  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Sub MustOverrideMe()  
    End Sub  
End Class 'Base2  
```  
  
```csharp  
abstract class Base2 {  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(  
System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
public abstract void MustOverrideMe();  
}  
```  
  
 針對基底類別並不要求完全信任的公用覆寫函式：  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe  
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.Demand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 針對基底類別要求完全信任的公用覆寫函式：  
  
```vb  
Class Derived  
    Inherits Base1  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")> _  
    Public Overrides Sub CanOverrideOrCallMe()  
        MyBase.CanOverrideOrCallMe()  
    End Sub 'CanOverrideOrCallMe
End Class 'Derived  
```  
  
```csharp  
class Derived : Base1  
{
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name="FullTrust")]
    public override void CanOverrideOrCallMe()
    {  
        base.CanOverrideOrCallMe();  
    }  
}  
```  
  
 針對公用介面：  
  
```vb  
Public Interface ICanCastToMe  
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
    Sub CanImplementMe()  
End Interface 'ICanCastToMe  
<System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust"), System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name:="FullTrust")> _  
Class Implemented  
    Implements ICanCastToMe  
    Public Sub CanImplementMe()  
    End Sub 'CanImplementMe  
```  
  
```csharp  
public interface ICanCastToMe
{  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
void CanImplementMe();  
}  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
[System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.InheritanceDemand, Name = "FullTrust")]  
class Implemented : ICanCastToMe  
{  
    public void CanImplementMe()  
    {  
    }  
}  
```  
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a>Virtual Internal 覆寫或 Overloads Overridable Friend  
  
> [!NOTE]
> 在將方法聲明`virtual`為 和`internal`（`Overloads``Overridable``Friend`在 Visual Basic 中）時，本節會警告安全問題。 此警告僅適用于 .NET 框架版本 1.0 和 1.1，它不適用於更高版本。  
  
 在 .NET Framework 版本 1.0 和 1.1 中，在確認代碼對其他程式集無法接通，必須瞭解類型系統可訪問性的細微差別。 聲明**為虛擬**和**內部**（在 Visual Basic 中**重載可重寫好友**）的方法可以重寫父類的 vable 條目，並且只能在同一程式集中使用，因為它是內部的。 但是，重寫的可訪問性由**虛擬**關鍵字決定，只要該代碼有權訪問類本身，就可以從另一個程式集重寫此功能。 如果重寫的可能性出現問題，請使用聲明性安全性來修復它，或者如果不**嚴格要求虛擬關鍵字**，則將其刪除。  
  
 請注意，即使語言編譯器會以編譯錯誤防止這些覆寫，程式碼撰寫還是可能以其他編譯器覆寫。  
  
## <a name="see-also"></a>另請參閱

- [安全程式碼撰寫方針](../../standard/security/secure-coding-guidelines.md)
