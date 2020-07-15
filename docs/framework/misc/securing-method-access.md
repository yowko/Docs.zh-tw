---
title: 設定方法存取的安全性
description: 瞭解如何對不是供公用使用但仍需要公開的方法，讓方法存取安全。
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
ms.openlocfilehash: a7ef419cf3959cf7a3ffde874353dacd3815c81a
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309387"
---
# <a name="securing-method-access"></a><span data-ttu-id="07431-103">設定方法存取的安全性</span><span class="sxs-lookup"><span data-stu-id="07431-103">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="07431-104">有些方法可能不適合讓未受信任的任意程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="07431-104">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="07431-105">這類方法會造成一些風險：方法可能會提供一些受限制的資訊；它可能會認定傳遞給它的任何資訊；它可能不會對參數執行錯誤檢查；它可能會因錯誤的參數發生問題或執行有害的動作。</span><span class="sxs-lookup"><span data-stu-id="07431-105">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="07431-106">您應該留意這些情況，並採取動作來協助保護方法。</span><span class="sxs-lookup"><span data-stu-id="07431-106">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="07431-107">在某些情況下，您可能需要限制不提供公用用途但仍必須是公用的方法。</span><span class="sxs-lookup"><span data-stu-id="07431-107">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="07431-108">例如，您可能會需要有跨您自己的 Dll 呼叫的介面，因此它必須是公用的，但為了防止客戶使用它，或惡意程式碼利用進入點進入您的元件，所以您不想將它公開。</span><span class="sxs-lookup"><span data-stu-id="07431-108">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="07431-109">另一個常見的原因是限制不適合公開使用的方法（但必須是公用的），以避免必須記載並支援可能是內部介面的方式。</span><span class="sxs-lookup"><span data-stu-id="07431-109">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be an internal interface.</span></span>  
  
 <span data-ttu-id="07431-110">Managed 程式碼提供數種方式以限制方法存取：</span><span class="sxs-lookup"><span data-stu-id="07431-110">Managed code offers several ways to restrict method access:</span></span>  
  
- <span data-ttu-id="07431-111">限制類別、 組件、 或衍生類別的存取範圍，如果其可以信任。</span><span class="sxs-lookup"><span data-stu-id="07431-111">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="07431-112">這是最簡單限制方法存取權的方式。</span><span class="sxs-lookup"><span data-stu-id="07431-112">This is the simplest way to limit method access.</span></span> <span data-ttu-id="07431-113">一般來說，衍生類別可能會比它們衍生自的類別更值得信任，不過在某些情況下，它們會共用父類別的身分識別。</span><span class="sxs-lookup"><span data-stu-id="07431-113">In general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="07431-114">特別的是，請勿從關鍵字推斷信任 `protected` ，這不一定會用於安全性內容中。</span><span class="sxs-lookup"><span data-stu-id="07431-114">In particular, do not infer trust from the keyword `protected`, which is not necessarily used in the security context.</span></span>  
  
- <span data-ttu-id="07431-115">限制方法存取指定身分識別的呼叫者，基本上是您選擇的任何[特定辨識](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29)項（強式名稱、發行者、區域等等）。</span><span class="sxs-lookup"><span data-stu-id="07431-115">Limit the method access to callers of a specified identity--essentially, any particular [evidence](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7y5x1hcd%28v=vs.100%29) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
- <span data-ttu-id="07431-116">限制具有您選取權限之呼叫端的方法存取權。</span><span class="sxs-lookup"><span data-stu-id="07431-116">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="07431-117">同樣地，宣告式安全性可讓您控制類別的繼承。</span><span class="sxs-lookup"><span data-stu-id="07431-117">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="07431-118">您可以使用**InheritanceDemand**來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="07431-118">You can use **InheritanceDemand** to do the following:</span></span>  
  
- <span data-ttu-id="07431-119">需要衍生類別以具有指定身分識別或權限。</span><span class="sxs-lookup"><span data-stu-id="07431-119">Require derived classes to have a specified identity or permission.</span></span>  
  
- <span data-ttu-id="07431-120">需要覆寫指定方法的衍生類別以具有指定身分識別或權限。</span><span class="sxs-lookup"><span data-stu-id="07431-120">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="07431-121">下列範例示範如何以要求呼叫端使用特定強勢名稱，來協助保護限制存取的公用類別。</span><span class="sxs-lookup"><span data-stu-id="07431-121">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="07431-122">這個範例會使用 <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> 具有強式名稱**要求**的。</span><span class="sxs-lookup"><span data-stu-id="07431-122">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="07431-123">如需如何使用強式名稱簽署元件的工作型資訊，請參閱[建立和使用強式名稱的元件](../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="07431-123">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../standard/assembly/create-use-strong-named.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="07431-124">將類別和成員排除在未受信任程式碼的使用之外</span><span class="sxs-lookup"><span data-stu-id="07431-124">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="07431-125">使用這一節中所示的宣告，來防止部分信任程式碼使用特定類別和方法，以及屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="07431-125">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="07431-126">藉由將這些宣告套用至類別，您可以將保護套用至其所有方法、屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="07431-126">By applying these declarations to a class, you apply the protection to all its methods, properties, and events.</span></span> <span data-ttu-id="07431-127">不過，欄位存取不會受到宣告式安全性的影響。</span><span class="sxs-lookup"><span data-stu-id="07431-127">However, field access is not affected by declarative security.</span></span> <span data-ttu-id="07431-128">也請注意，連結要求協助防範立即呼叫端，且可能還是會受到引誘攻擊。</span><span class="sxs-lookup"><span data-stu-id="07431-128">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07431-129">.NET Framework 4 中引進了新的透明度模型。</span><span class="sxs-lookup"><span data-stu-id="07431-129">A new transparency model has been introduced in the .NET Framework 4.</span></span> <span data-ttu-id="07431-130">[安全性透明的程式碼層級 2](security-transparent-code-level-2.md)模型會以屬性識別安全程式碼 <xref:System.Security.SecurityCriticalAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="07431-130">The [Security-Transparent Code, Level 2](security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="07431-131">安全性關鍵的程式碼需要呼叫端和繼承者兩者都完全受信任。</span><span class="sxs-lookup"><span data-stu-id="07431-131">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="07431-132">從舊版 .NET Framework 程式碼存取安全性規則的組件可以呼叫層級 2 組件。</span><span class="sxs-lookup"><span data-stu-id="07431-132">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="07431-133">在此情況下，安全性關鍵屬性會被視為完全信任的連結要求。</span><span class="sxs-lookup"><span data-stu-id="07431-133">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="07431-134">在強式名稱的元件中，會將[LinkDemand](link-demands.md)套用至所有可公開存取的方法、屬性和事件，以限制其使用完全信任的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="07431-134">In strong-named assemblies, a [LinkDemand](link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="07431-135">若要停用此功能，您必須套用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="07431-135">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="07431-136">因此，只有不帶正負號的組件或具有此屬性的組件需要明確地標示類別，以排除不受信任的呼叫端您可以使用這些宣告以標記非為不受信任的呼叫端之類型的子集。</span><span class="sxs-lookup"><span data-stu-id="07431-136">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="07431-137">下列範例示範如何防止不受信任的程式碼使用類別和成員。</span><span class="sxs-lookup"><span data-stu-id="07431-137">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="07431-138">針對公用未密封的類別：</span><span class="sxs-lookup"><span data-stu-id="07431-138">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="07431-139">針對公用密封的類別：</span><span class="sxs-lookup"><span data-stu-id="07431-139">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="07431-140">針對公用抽象類別：</span><span class="sxs-lookup"><span data-stu-id="07431-140">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="07431-141">針對公用虛擬函式：</span><span class="sxs-lookup"><span data-stu-id="07431-141">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="07431-142">針對公用抽象函式：</span><span class="sxs-lookup"><span data-stu-id="07431-142">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="07431-143">針對基底類別並不要求完全信任的公用覆寫函式：</span><span class="sxs-lookup"><span data-stu-id="07431-143">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="07431-144">針對基底類別要求完全信任的公用覆寫函式：</span><span class="sxs-lookup"><span data-stu-id="07431-144">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="07431-145">針對公用介面：</span><span class="sxs-lookup"><span data-stu-id="07431-145">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="07431-146">Virtual Internal 覆寫或 Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="07431-146">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07431-147">這一節會在將方法同時宣告為和時發出安全性問題 `virtual` `internal` （ `Overloads` `Overridable` `Friend` Visual Basic）。</span><span class="sxs-lookup"><span data-stu-id="07431-147">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads` `Overridable` `Friend` in Visual Basic).</span></span> <span data-ttu-id="07431-148">此警告僅適用于 .NET Framework 版本1.0 和1.1，不適用於較新的版本。</span><span class="sxs-lookup"><span data-stu-id="07431-148">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="07431-149">在 .NET Framework 版本1.0 和1.1 中，當您確認程式碼無法供其他元件使用時，您必須留意類型系統協助工具的細微之處。</span><span class="sxs-lookup"><span data-stu-id="07431-149">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="07431-150">宣告為**虛擬**和**內部**的方法（Visual Basic 中的多載可覆**寫 Friend** ）可以覆寫父類別的 vtable 專案，而且只能從相同的元件內使用，因為它是內部的。</span><span class="sxs-lookup"><span data-stu-id="07431-150">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="07431-151">不過，覆寫的存取範圍是由**virtual**關鍵字決定，而且只要該程式碼可存取類別本身，就可以從另一個元件覆寫。</span><span class="sxs-lookup"><span data-stu-id="07431-151">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="07431-152">如果覆寫的可能性出現問題，請使用宣告式安全性來加以修正，或移除不是絕對必要的**虛擬**關鍵字。</span><span class="sxs-lookup"><span data-stu-id="07431-152">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="07431-153">即使語言編譯器會防止這些覆寫發生編譯錯誤，但使用其他編譯器撰寫的程式碼也可能會覆寫。</span><span class="sxs-lookup"><span data-stu-id="07431-153">Even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07431-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07431-154">See also</span></span>

- [<span data-ttu-id="07431-155">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="07431-155">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
