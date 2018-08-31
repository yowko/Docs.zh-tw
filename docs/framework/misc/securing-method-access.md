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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 314ceb86219ce143e84a00392727d610c0779e48
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258065"
---
# <a name="securing-method-access"></a><span data-ttu-id="8ce72-102">設定方法存取的安全性</span><span class="sxs-lookup"><span data-stu-id="8ce72-102">Securing Method Access</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="8ce72-103">有些方法可能不適合讓未受信任的任意程式碼呼叫。</span><span class="sxs-lookup"><span data-stu-id="8ce72-103">Some methods might not be suitable to allow arbitrary untrusted code to call.</span></span> <span data-ttu-id="8ce72-104">這類方法會造成一些風險：方法可能會提供一些受限制的資訊；它可能會認定傳遞給它的任何資訊；它可能不會對參數執行錯誤檢查；它可能會因錯誤的參數發生問題或執行有害的動作。</span><span class="sxs-lookup"><span data-stu-id="8ce72-104">Such methods pose several risks: The method might provide some restricted information; it might believe any information passed to it; it might not do error checking on the parameters; or with the wrong parameters, it might malfunction or do something harmful.</span></span> <span data-ttu-id="8ce72-105">您應該留意這些情況，並採取動作來協助保護方法。</span><span class="sxs-lookup"><span data-stu-id="8ce72-105">You should be aware of these cases and take action to help protect the method.</span></span>  
  
 <span data-ttu-id="8ce72-106">在某些情況下，您可能需要限制不提供公用用途但仍必須是公用的方法。</span><span class="sxs-lookup"><span data-stu-id="8ce72-106">In some cases, you might need to restrict methods that are not intended for public use but still must be public.</span></span> <span data-ttu-id="8ce72-107">例如，您可能會需要有跨您自己的 Dll 呼叫的介面，因此它必須是公用的，但為了防止客戶使用它，或惡意程式碼利用進入點進入您的元件，所以您不想將它公開。</span><span class="sxs-lookup"><span data-stu-id="8ce72-107">For example, you might have an interface that needs to be called across your own DLLs and hence must be public, but you do not want to expose it publicly to prevent customers from using it or to prevent malicious code from exploiting the entry point into your component.</span></span> <span data-ttu-id="8ce72-108">另一個限制不提供公用用途 (但必須是公用) 方法的常見原因，是為了避免記錄和支援可能非常內部的介面。</span><span class="sxs-lookup"><span data-stu-id="8ce72-108">Another common reason to restrict a method not intended for public use (but that must be public) is to avoid having to document and support what might be a very internal interface.</span></span>  
  
 <span data-ttu-id="8ce72-109">Managed 程式碼提供數種方式以限制方法存取：</span><span class="sxs-lookup"><span data-stu-id="8ce72-109">Managed code offers several ways to restrict method access:</span></span>  
  
-   <span data-ttu-id="8ce72-110">限制類別、 組件、 或衍生類別的存取範圍，如果其可以信任。</span><span class="sxs-lookup"><span data-stu-id="8ce72-110">Limit the scope of accessibility to the class, assembly, or derived classes, if they can be trusted.</span></span> <span data-ttu-id="8ce72-111">這是最簡單限制方法存取權的方式。</span><span class="sxs-lookup"><span data-stu-id="8ce72-111">This is the simplest way to limit method access.</span></span> <span data-ttu-id="8ce72-112">請注意，一般而言，衍生類別可能比它們衍生自的類別還不可靠，雖然在某些情況下它們共用父類別的識別。</span><span class="sxs-lookup"><span data-stu-id="8ce72-112">Note that, in general, derived classes can be less trustworthy than the class they derive from, though in some cases they share the parent class's identity.</span></span> <span data-ttu-id="8ce72-113">特別的是，不會推斷關鍵字的信任關係**保護**，這不一定會在安全性內容。</span><span class="sxs-lookup"><span data-stu-id="8ce72-113">In particular, do not infer trust from the keyword **protected**, which is not necessarily used in the security context.</span></span>  
  
-   <span data-ttu-id="8ce72-114">限制方法存取，以指定的身分識別-基本上，任何特定的呼叫端[辨識項](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da)選擇 （強式名稱、 發行者、 區域等等）。</span><span class="sxs-lookup"><span data-stu-id="8ce72-114">Limit the method access to callers of a specified identity--essentially, any particular [evidence](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da) (strong name, publisher, zone, and so on) you choose.</span></span>  
  
-   <span data-ttu-id="8ce72-115">限制具有您選取權限之呼叫端的方法存取權。</span><span class="sxs-lookup"><span data-stu-id="8ce72-115">Limit the method access to callers having whatever permissions you select.</span></span>  
  
 <span data-ttu-id="8ce72-116">同樣地，宣告式安全性可讓您控制類別的繼承。</span><span class="sxs-lookup"><span data-stu-id="8ce72-116">Similarly, declarative security allows you to control inheritance of classes.</span></span> <span data-ttu-id="8ce72-117">您可以使用**InheritanceDemand**執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8ce72-117">You can use **InheritanceDemand** to do the following:</span></span>  
  
-   <span data-ttu-id="8ce72-118">需要衍生類別以具有指定身分識別或權限。</span><span class="sxs-lookup"><span data-stu-id="8ce72-118">Require derived classes to have a specified identity or permission.</span></span>  
  
-   <span data-ttu-id="8ce72-119">需要覆寫指定方法的衍生類別以具有指定身分識別或權限。</span><span class="sxs-lookup"><span data-stu-id="8ce72-119">Require derived classes that override specific methods to have a specified identity or permission.</span></span>  
  
 <span data-ttu-id="8ce72-120">下列範例示範如何以要求呼叫端使用特定強勢名稱，來協助保護限制存取的公用類別。</span><span class="sxs-lookup"><span data-stu-id="8ce72-120">The following example shows how to help protect a public class for limited access by requiring that callers be signed with a particular strong name.</span></span> <span data-ttu-id="8ce72-121">這個範例會使用<xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute>具有**隨選**強式名稱。</span><span class="sxs-lookup"><span data-stu-id="8ce72-121">This example uses the <xref:System.Security.Permissions.StrongNameIdentityPermissionAttribute> with a **Demand** for the strong name.</span></span> <span data-ttu-id="8ce72-122">如需如何簽署以強式名稱組件的工作型資訊，請參閱[建立和使用強式名稱組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="8ce72-122">For task-based information on how to sign an assembly with a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
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
  
## <a name="excluding-classes-and-members-from-use-by-untrusted-code"></a><span data-ttu-id="8ce72-123">將類別和成員排除在未受信任程式碼的使用之外</span><span class="sxs-lookup"><span data-stu-id="8ce72-123">Excluding Classes and Members from Use by Untrusted Code</span></span>  
 <span data-ttu-id="8ce72-124">使用這一節中所示的宣告，來防止部分信任程式碼使用特定類別和方法，以及屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="8ce72-124">Use the declarations shown in this section to prevent specific classes and methods, as well as properties and events, from being used by partially trusted code.</span></span> <span data-ttu-id="8ce72-125">您可以藉由將這些宣告套用至類別，來為所有方法、 屬性和事件套用保護，不過請注意存取欄位不會受宣告式安全性影響。</span><span class="sxs-lookup"><span data-stu-id="8ce72-125">By applying these declarations to a class, you apply the protection to all its methods, properties, and events; however, note that field access is not affected by declarative security.</span></span> <span data-ttu-id="8ce72-126">也請注意，連結要求協助防範立即呼叫端，且可能還是會受到引誘攻擊。</span><span class="sxs-lookup"><span data-stu-id="8ce72-126">Note also that link demands help protect against only the immediate callers and might still be subject to luring attacks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce72-127">新的透明度模型已導入[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="8ce72-127">A new transparency model has been introduced in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="8ce72-128">[安全性透明程式碼，層級 2](../../../docs/framework/misc/security-transparent-code-level-2.md)模型識別安全程式碼<xref:System.Security.SecurityCriticalAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="8ce72-128">The [Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) model identifies secure code with the <xref:System.Security.SecurityCriticalAttribute> attribute.</span></span> <span data-ttu-id="8ce72-129">安全性關鍵的程式碼需要呼叫端和繼承者兩者都完全受信任。</span><span class="sxs-lookup"><span data-stu-id="8ce72-129">Security-critical code requires both callers and inheritors to be fully trusted.</span></span> <span data-ttu-id="8ce72-130">從舊版 .NET Framework 程式碼存取安全性規則的組件可以呼叫層級 2 組件。</span><span class="sxs-lookup"><span data-stu-id="8ce72-130">Assemblies that are running under the code access security rules from earlier .NET Framework versions can call level 2 assemblies.</span></span> <span data-ttu-id="8ce72-131">在此情況下，安全性關鍵屬性會被視為完全信任的連結要求。</span><span class="sxs-lookup"><span data-stu-id="8ce72-131">In this case, the security-critical attributes will be treated as link demands for full trust.</span></span>  
  
 <span data-ttu-id="8ce72-132">強式名稱組件中[LinkDemand](../../../docs/framework/misc/link-demands.md)套用至所有可公開存取的方法、 屬性和事件中，以限制它使用完全信任呼叫端。</span><span class="sxs-lookup"><span data-stu-id="8ce72-132">In strong-named assemblies, a [LinkDemand](../../../docs/framework/misc/link-demands.md) is applied to all publicly accessible methods, properties, and events therein to restrict their use to fully trusted callers.</span></span> <span data-ttu-id="8ce72-133">若要停用此功能，您必須套用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="8ce72-133">To disable this feature, you must apply the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="8ce72-134">因此，只有不帶正負號的組件或具有此屬性的組件需要明確地標示類別，以排除不受信任的呼叫端您可以使用這些宣告以標記非為不受信任的呼叫端之類型的子集。</span><span class="sxs-lookup"><span data-stu-id="8ce72-134">Thus, explicitly marking classes to exclude untrusted callers is necessary only for unsigned assemblies or assemblies with this attribute; you can use these declarations to mark a subset of types therein that are not intended for untrusted callers.</span></span>  
  
 <span data-ttu-id="8ce72-135">下列範例示範如何防止不受信任的程式碼使用類別和成員。</span><span class="sxs-lookup"><span data-stu-id="8ce72-135">The following examples show how to prevent classes and members from being used by untrusted code.</span></span>  
  
 <span data-ttu-id="8ce72-136">針對公用未密封的類別：</span><span class="sxs-lookup"><span data-stu-id="8ce72-136">For public nonsealed classes:</span></span>  
  
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
  
 <span data-ttu-id="8ce72-137">針對公用密封的類別：</span><span class="sxs-lookup"><span data-stu-id="8ce72-137">For public sealed classes:</span></span>  
  
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
  
 <span data-ttu-id="8ce72-138">針對公用抽象類別：</span><span class="sxs-lookup"><span data-stu-id="8ce72-138">For public abstract classes:</span></span>  
  
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
  
 <span data-ttu-id="8ce72-139">針對公用虛擬函式：</span><span class="sxs-lookup"><span data-stu-id="8ce72-139">For public virtual functions:</span></span>  
  
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
  
 <span data-ttu-id="8ce72-140">針對公用抽象函式：</span><span class="sxs-lookup"><span data-stu-id="8ce72-140">For public abstract functions:</span></span>  
  
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
  
 <span data-ttu-id="8ce72-141">針對基底類別並不要求完全信任的公用覆寫函式：</span><span class="sxs-lookup"><span data-stu-id="8ce72-141">For public override functions where the base class does not demand full trust:</span></span>  
  
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
  
 <span data-ttu-id="8ce72-142">針對基底類別要求完全信任的公用覆寫函式：</span><span class="sxs-lookup"><span data-stu-id="8ce72-142">For public override functions where the base class demands full trust:</span></span>  
  
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
  
 <span data-ttu-id="8ce72-143">針對公用介面：</span><span class="sxs-lookup"><span data-stu-id="8ce72-143">For public interfaces:</span></span>  
  
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
  
## <a name="virtual-internal-overrides-or-overloads-overridable-friend"></a><span data-ttu-id="8ce72-144">Virtual Internal 覆寫或 Overloads Overridable Friend</span><span class="sxs-lookup"><span data-stu-id="8ce72-144">Virtual Internal Overrides or Overloads Overridable Friend</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce72-145">本節會警告關於安全性問題，宣告兩者為方法時`virtual`並`internal`(`Overloads``Overridable``Friend` Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="8ce72-145">This section warns about a security issue when declaring a method as both `virtual` and `internal` (`Overloads``Overridable``Friend` in Visual Basic).</span></span> <span data-ttu-id="8ce72-146">這個警告只適用於.NET framework 1.0 和 1.1 版，它不會套用到更新版本。</span><span class="sxs-lookup"><span data-stu-id="8ce72-146">This warning applies only to the .NET Framework versions 1.0 and 1.1, it does not apply to later versions.</span></span>  
  
 <span data-ttu-id="8ce72-147">在.NET framework 1.0 和 1.1 版中，您必須留意類型系統存取範圍的細微差別時確認您的程式碼無法使用其他組件。</span><span class="sxs-lookup"><span data-stu-id="8ce72-147">In the .NET Framework versions 1.0 and 1.1, you must be aware of a nuance of the type system accessibility when confirming that your code is unavailable to other assemblies.</span></span> <span data-ttu-id="8ce72-148">宣告的方法**虛擬**並**內部**(**Overloads Overridable Friend** Visual Basic 中) 可以覆寫父類別 vtable 項目，而且可以只從使用相同的組件中因為它是內部。</span><span class="sxs-lookup"><span data-stu-id="8ce72-148">A method that is declared **virtual** and **internal** (**Overloads Overridable Friend** in Visual Basic) can override the parent class's vtable entry and can be used only from within the same assembly because it is internal.</span></span> <span data-ttu-id="8ce72-149">不過，覆寫的存取範圍取決於**虛擬**關鍵字，且可能會覆寫從其他組件，只要該程式碼可存取此類別本身。</span><span class="sxs-lookup"><span data-stu-id="8ce72-149">However, the accessibility for overriding is determined by the **virtual** keyword, and this can be overridden from another assembly as long as that code has access to the class itself.</span></span> <span data-ttu-id="8ce72-150">如果覆寫可能會發生問題，使用宣告式安全性來解決問題，或移除**虛擬**關鍵字，如果不是絕對必要。</span><span class="sxs-lookup"><span data-stu-id="8ce72-150">If the possibility of an override presents a problem, use declarative security to fix it, or remove the **virtual** keyword if it is not strictly required.</span></span>  
  
 <span data-ttu-id="8ce72-151">請注意，即使語言編譯器會以編譯錯誤防止這些覆寫，程式碼撰寫還是可能以其他編譯器覆寫。</span><span class="sxs-lookup"><span data-stu-id="8ce72-151">Note that even if a language compiler prevents these overrides with a compilation error, it is possible for code written with other compilers to override.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce72-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ce72-152">See Also</span></span>  
 [<span data-ttu-id="8ce72-153">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="8ce72-153">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
