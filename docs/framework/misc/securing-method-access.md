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
# <a name="securing-method-access"></a><span data-ttu-id="74349-102">設定方法存取的安全性</span><span class="sxs-lookup"><span data-stu-id="74349-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="74349-103">有些方法可能不適合讓未受信任的任意程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="74349-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="74349-104">這類方法會造成一些風險：方法可能會提供一些受限制的資訊；它可能會認定傳遞給它的任何資訊；它可能不會對參數執行錯誤檢查；它可能會因錯誤的參數發生問題或執行有害的動作。</span><span class="sxs-lookup"><span data-stu-id="74349-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="74349-105">您應該留意這些情況，並採取動作來協助保護方法。</span><span class="sxs-lookup"><span data-stu-id="74349-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="74349-106">在某些情況下，您可能需要限制不提供公用用途但仍必須是公用的方法。</span><span class="sxs-lookup"><span data-stu-id="74349-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="74349-107">例如，您可能會需要有跨您自己的 Dll 呼叫的介面，因此它必須是公用的，但為了防止客戶使用它，或惡意程式碼利用進入點進入您的元件，所以您不想將它公開。</span><span class="sxs-lookup"><span data-stu-id="74349-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="74349-108">另一個限制不提供公用用途 (但必須是公用) 方法的常見原因，是為了避免記錄和支援可能非常內部的介面。</span><span class="sxs-lookup"><span data-stu-id="74349-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="74349-109">Managed 程式碼提供數種方式以限制方法存取：</span><span class="sxs-lookup"><span data-stu-id="74349-109">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="74349-110">限制類別、 組件、 或衍生類別的存取範圍，如果其可以信任。</span><span class="sxs-lookup"><span data-stu-id="74349-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="74349-111">這是最簡單限制方法存取權的方式。</span><span class="sxs-lookup"><span data-stu-id="74349-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="74349-112">請注意，一般而言，衍生類別可能比它們衍生自的類別還不可靠，雖然在某些情況下它們共用父類別的識別。</span><span class="sxs-lookup"><span data-stu-id="74349-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="74349-113">特別是，不要推斷來自**受保護**的關鍵字的信任，這不一定在安全上下文中使用。</span><span class="sxs-lookup"><span data-stu-id="74349-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="74349-114">將方法訪問限制為指定標識的調用方，實質上是您選擇的任何特定[證據](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29)（強式名稱、發行者、區域等）。</span><span class="sxs-lookup"><span data-stu-id="74349-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="74349-115">限制具有您選取權限之呼叫端的方法存取權。</span><span class="sxs-lookup"><span data-stu-id="74349-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="74349-116">同樣地，宣告式安全性可讓您控制類別的繼承。</span><span class="sxs-lookup"><span data-stu-id="74349-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="74349-117">您可以使用**繼承需求**執行以下操作：</span><span class="sxs-lookup"><span data-stu-id="74349-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="74349-118">需要衍生類別以具有指定身分識別或權限。</span><span class="sxs-lookup"><span data-stu-id="74349-118">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="74349-119">需要覆寫指定方法的衍生類別以具有指定身分識別或權限。</span><span class="sxs-lookup"><span data-stu-id="74349-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="74349-120">下列範例示範如何以要求呼叫端使用特定強勢名稱，來協助保護限制存取的公用類別。</span><span class="sxs-lookup"><span data-stu-id="74349-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="74349-121">此示例使用<xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute>具有強式名稱**的 Demand。**</span><span class="sxs-lookup"><span data-stu-id="74349-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="74349-122">有關如何使用強式名稱對程式集進行簽名的基於任務的資訊，請參閱[創建和使用強式名稱程式集](../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="74349-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="74349-123">將類別和成員排除在未受信任程式碼的使用之外</span><span class="sxs-lookup"><span data-stu-id="74349-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="74349-124">使用這一節中所示的宣告，來防止部分信任程式碼使用特定類別和方法，以及屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="74349-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="74349-125">您可以藉由將這些宣告套用至類別，來為所有方法、 屬性和事件套用保護，不過請注意存取欄位不會受宣告式安全性影響。</span><span class="sxs-lookup"><span data-stu-id="74349-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="74349-126">也請注意，連結要求協助防範立即呼叫端，且可能還是會受到引誘攻擊。</span><span class="sxs-lookup"><span data-stu-id="74349-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74349-127">在 .NET 框架 4 中引入了一種新的透明度模型。</span><span class="sxs-lookup"><span data-stu-id="74349-127">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="74349-128">[安全透明代碼，2 級](security-transparent-code-level-2.md)模型使用<xref:System.Security.SecurityCriticalAttribute>屬性標識安全代碼。</span><span class="sxs-lookup"><span data-stu-id="74349-128">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="74349-129">安全性關鍵的程式碼需要呼叫端和繼承者兩者都完全受信任。</span><span class="sxs-lookup"><span data-stu-id="74349-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="74349-130">從舊版 .NET Framework 程式碼存取安全性規則的組件可以呼叫層級 2 組件。</span><span class="sxs-lookup"><span data-stu-id="74349-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="74349-131">在此情況下，安全性關鍵屬性會被視為完全信任的連結要求。</span><span class="sxs-lookup"><span data-stu-id="74349-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="74349-132">在強命名程式集中[，LinkDemand](link-demands.md)應用於其中所有可公開訪問的方法、屬性和事件，以將其使用限制為完全受信任的調用方。</span><span class="sxs-lookup"><span data-stu-id="74349-132">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="74349-133">若要停用此功能，您必須套用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="74349-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="74349-134">因此，只有不帶正負號的組件或具有此屬性的組件需要明確地標示類別，以排除不受信任的呼叫端您可以使用這些宣告以標記非為不受信任的呼叫端之類型的子集。</span><span class="sxs-lookup"><span data-stu-id="74349-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="74349-135">下列範例示範如何防止不受信任的程式碼使用類別和成員。</span><span class="sxs-lookup"><span data-stu-id="74349-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="74349-136">針對公用未密封的類別：</span><span class="sxs-lookup"><span data-stu-id="74349-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="74349-137">針對公用密封的類別：</span><span class="sxs-lookup"><span data-stu-id="74349-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="74349-138">針對公用抽象類別：</span><span class="sxs-lookup"><span data-stu-id="74349-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="74349-139">針對公用虛擬函式：</span><span class="sxs-lookup"><span data-stu-id="74349-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="74349-140">針對公用抽象函式：</span><span class="sxs-lookup"><span data-stu-id="74349-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="74349-141">針對基底類別並不要求完全信任的公用覆寫函式：</span><span class="sxs-lookup"><span data-stu-id="74349-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="74349-142">針對基底類別要求完全信任的公用覆寫函式：</span><span class="sxs-lookup"><span data-stu-id="74349-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="74349-143">針對公用介面：</span><span class="sxs-lookup"><span data-stu-id="74349-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="74349-144">Virtual Internal 覆寫或 Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="74349-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74349-145">在將方法聲明`virtual`為 和`internal`（`Overloads``Overridable``Friend`在 Visual Basic 中）時，本節會警告安全問題。</span><span class="sxs-lookup"><span data-stu-id="74349-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="74349-146">此警告僅適用于 .NET 框架版本 1.0 和 1.1，它不適用於更高版本。</span><span class="sxs-lookup"><span data-stu-id="74349-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="74349-147">在 .NET Framework 版本 1.0 和 1.1 中，在確認代碼對其他程式集無法接通，必須瞭解類型系統可訪問性的細微差別。</span><span class="sxs-lookup"><span data-stu-id="74349-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="74349-148">聲明**為虛擬**和**內部**（在 Visual Basic 中**重載可重寫好友**）的方法可以重寫父類的 vable 條目，並且只能在同一程式集中使用，因為它是內部的。</span><span class="sxs-lookup"><span data-stu-id="74349-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="74349-149">但是，重寫的可訪問性由**虛擬**關鍵字決定，只要該代碼有權訪問類本身，就可以從另一個程式集重寫此功能。</span><span class="sxs-lookup"><span data-stu-id="74349-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="74349-150">如果重寫的可能性出現問題，請使用聲明性安全性來修復它，或者如果不**嚴格要求虛擬關鍵字**，則將其刪除。</span><span class="sxs-lookup"><span data-stu-id="74349-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="74349-151">請注意，即使語言編譯器會以編譯錯誤防止這些覆寫，程式碼撰寫還是可能以其他編譯器覆寫。</span><span class="sxs-lookup"><span data-stu-id="74349-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74349-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74349-152">See also</span></span>

- [<span data-ttu-id="74349-153">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="74349-153">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
