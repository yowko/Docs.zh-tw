---
title: "程式碼存取安全性的基本概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08ce62f54e70fe1650914060ade0f52357f8a736
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="code-access-security-basics"></a><span data-ttu-id="5c96c-102">程式碼存取安全性的基本概念</span><span class="sxs-lookup"><span data-stu-id="5c96c-102">Code Access Security Basics</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="5c96c-103">以 Common Language Runtime 為目標的每個應用程式 (亦即，每個 Managed 應用程式)，都必須與執行階段的安全性系統互動。</span><span class="sxs-lookup"><span data-stu-id="5c96c-103">Every application that targets the common language runtime (that is, every managed application) must interact with the runtime's security system.</span></span> <span data-ttu-id="5c96c-104">當 Managed 應用程式載入時，其主機會自動授與其權限集合。</span><span class="sxs-lookup"><span data-stu-id="5c96c-104">When a managed application is loaded, its host automatically grants it a set of permissions.</span></span> <span data-ttu-id="5c96c-105">這些權限是由主機的本機安全性設定，或是由應用程式所在的沙箱決定。</span><span class="sxs-lookup"><span data-stu-id="5c96c-105">These permissions are determined by the host's local security settings or by the sandbox the application is in.</span></span> <span data-ttu-id="5c96c-106">根據這些權限，應用程式會正確執行，或是產生安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c96c-106">Depending on these permissions, the application either runs properly or generates a security exception.</span></span>  
  
 <span data-ttu-id="5c96c-107">桌面應用程式的預設主機可允許程式碼在完全信任中執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-107">The default host for desktop applications allows code to run in full trust.</span></span> <span data-ttu-id="5c96c-108">因此，如果您的應用程式是以桌面為目標，則有不受限制的權限集合。</span><span class="sxs-lookup"><span data-stu-id="5c96c-108">Therefore, if your application targets the desktop, it has an unrestricted permission set.</span></span> <span data-ttu-id="5c96c-109">其他主機或沙箱則為應用程式提供有限的權限集合。</span><span class="sxs-lookup"><span data-stu-id="5c96c-109">Other hosts or sandboxes provide a limited permission set for applications.</span></span> <span data-ttu-id="5c96c-110">由於權限集合可以在主機之間變更，因此，您必須將應用程式設計為只使用目標主機允許的權限。</span><span class="sxs-lookup"><span data-stu-id="5c96c-110">Because the permission set can change from host to host, you must design your application to use only the permissions that your target host allows.</span></span>  
  
 <span data-ttu-id="5c96c-111">您必須熟悉下列程式碼存取安全性概念，才能撰寫以 Common Language Runtime 為目標的有效應用程式：</span><span class="sxs-lookup"><span data-stu-id="5c96c-111">You must be familiar with the following code access security concepts in order to write effective applications that target the common language runtime:</span></span>  
  
-   <span data-ttu-id="5c96c-112">**類型安全程式碼**： 類型安全程式碼是只以妥善定義、 可允許的方式來存取類型的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c96c-112">**Type-safe code**: Type-safe code is code that accesses types only in well-defined, allowable ways.</span></span> <span data-ttu-id="5c96c-113">例如，如果有一個有效的物件參考，類型安全程式碼就可以在對應至實際欄位成員的固定位移上存取記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c96c-113">For example, given a valid object reference, type-safe code can access memory at fixed offsets that correspond to actual field members.</span></span> <span data-ttu-id="5c96c-114">如果程式碼存取的記憶體，是在屬於該物件公開欄位之記憶體範圍外的任意位移，則不是類型安全程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c96c-114">If the code accesses memory at arbitrary offsets outside the range of memory that belongs to that object's publicly exposed fields, it is not type-safe.</span></span> <span data-ttu-id="5c96c-115">若要讓程式碼受益於程式碼存取安全性，您必須使用會產生可驗證類型安全程式碼的編譯器。</span><span class="sxs-lookup"><span data-stu-id="5c96c-115">To enable code to benefit from code access security, you must use a compiler that generates verifiably type-safe code.</span></span> <span data-ttu-id="5c96c-116">如需詳細資訊，請參閱[撰寫可驗證的類型安全程式碼](#typesafe_code)本主題稍後的章節。</span><span class="sxs-lookup"><span data-stu-id="5c96c-116">For more information, see the [Writing Verifiably Type-Safe Code](#typesafe_code) section later in this topic.</span></span>  
  
-   <span data-ttu-id="5c96c-117">**命令式和宣告式語法**: common language runtime 為目標的程式碼可以與安全性系統互動所要求的權限要求 (demand) 呼叫端擁有指定的權限，以及覆寫特定安全性設定 （有足夠的權限）。</span><span class="sxs-lookup"><span data-stu-id="5c96c-117">**Imperative and declarative syntax**: Code that targets the common language runtime can interact with the security system by requesting permissions, demanding that callers have specified permissions, and overriding certain security settings (given enough privileges).</span></span> <span data-ttu-id="5c96c-118">您可以使用兩種形式的語法，以程式設計方式來與 .NET Framework 安全性系統互動：宣告式語法和命令式語法。</span><span class="sxs-lookup"><span data-stu-id="5c96c-118">You use two forms of syntax to programmatically interact with the .NET Framework security system: declarative syntax and imperative syntax.</span></span> <span data-ttu-id="5c96c-119">宣告式呼叫是使用屬性來執行，命令式呼叫是使用程式碼中新的類別執行個體來執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-119">Declarative calls are performed using attributes; imperative calls are performed using new instances of classes within your code.</span></span> <span data-ttu-id="5c96c-120">有些呼叫只能以命令方式執行，有些呼叫只能以宣告方式執行，而有些呼叫能以其中任一方式執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-120">Some calls can be performed only imperatively, others can be performed only declaratively, and some calls can be performed in either manner.</span></span>  
  
-   <span data-ttu-id="5c96c-121">**安全類別庫**： 安全類別庫會使用安全性要求，以確定程式庫的呼叫端擁有存取程式庫公開之資源的權限。</span><span class="sxs-lookup"><span data-stu-id="5c96c-121">**Secure class libraries**: A secure class library uses security demands to ensure that the library's callers have permission to access the resources that the library exposes.</span></span> <span data-ttu-id="5c96c-122">例如，安全類別庫可能有一個用來建立檔案的方法，要求 (demand) 其呼叫端要有權限才能建立檔案。</span><span class="sxs-lookup"><span data-stu-id="5c96c-122">For example, a secure class library might have a method for creating files that would demand that its callers have permissions to create files.</span></span> <span data-ttu-id="5c96c-123">.NET Framework 由安全類別庫組成。</span><span class="sxs-lookup"><span data-stu-id="5c96c-123">The .NET Framework consists of secure class libraries.</span></span> <span data-ttu-id="5c96c-124">您應該要知道需要哪些權限，才能存取您的程式碼所使用的任何類別庫。</span><span class="sxs-lookup"><span data-stu-id="5c96c-124">You should be aware of the permissions required to access any library that your code uses.</span></span> <span data-ttu-id="5c96c-125">如需詳細資訊，請參閱[使用安全類別庫](#secure_library)本主題稍後的章節。</span><span class="sxs-lookup"><span data-stu-id="5c96c-125">For more information, see the [Using Secure Class Libraries](#secure_library) section later in this topic.</span></span>  
  
-   <span data-ttu-id="5c96c-126">**透明程式碼**： 開頭為[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，除了識別特定權限，您也必須決定程式碼是否應執行安全性透明的形式。</span><span class="sxs-lookup"><span data-stu-id="5c96c-126">**Transparent code**: Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], in addition to identifying specific permissions, you must also determine whether your code should run as security-transparent.</span></span> <span data-ttu-id="5c96c-127">安全性透明程式碼無法呼叫被識別為安全性關鍵的類型或成員。</span><span class="sxs-lookup"><span data-stu-id="5c96c-127">Security-transparent code cannot call types or members that are identified as security-critical.</span></span> <span data-ttu-id="5c96c-128">這個規則適用於完全信任的應用程式，也適用於部分信任的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c96c-128">This rule applies to full-trust applications as well as partially trusted applications.</span></span> <span data-ttu-id="5c96c-129">如需詳細資訊，請參閱[安全性透明程式碼](../../../docs/framework/misc/security-transparent-code.md)。</span><span class="sxs-lookup"><span data-stu-id="5c96c-129">For more information, see [Security-Transparent Code](../../../docs/framework/misc/security-transparent-code.md).</span></span>  
  
<a name="typesafe_code"></a>   
## <a name="writing-verifiably-type-safe-code"></a><span data-ttu-id="5c96c-130">撰寫可驗證的類型安全程式碼</span><span class="sxs-lookup"><span data-stu-id="5c96c-130">Writing Verifiably Type-Safe Code</span></span>  
 <span data-ttu-id="5c96c-131">Just-In-Time (JIT) 編譯會執行驗證程序來檢查程式碼，並嘗試判斷程式碼是否為類型安全。</span><span class="sxs-lookup"><span data-stu-id="5c96c-131">Just-in-time (JIT) compilation performs a verification process that examines code and tries to determine whether the code is type-safe.</span></span> <span data-ttu-id="5c96c-132">必須是類型安全驗證期間證明的程式碼會呼叫*可驗證的類型安全程式碼*。</span><span class="sxs-lookup"><span data-stu-id="5c96c-132">Code that is proven during verification to be type-safe is called *verifiably type-safe code*.</span></span> <span data-ttu-id="5c96c-133">因為驗證程序或編譯器的限制，程式碼可能是類型安全，但不一定是可驗證的類型安全。</span><span class="sxs-lookup"><span data-stu-id="5c96c-133">Code can be type-safe, yet might not be verifiably type-safe because of the limitations of the verification process or of the compiler.</span></span> <span data-ttu-id="5c96c-134">並非所有語言都是類型安全，而某些語言編譯器，例如 Microsoft Visual C++，就無法產生可驗證的類型安全 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c96c-134">Not all languages are type-safe, and some language compilers, such as Microsoft Visual C++, cannot generate verifiably type-safe managed code.</span></span> <span data-ttu-id="5c96c-135">若要判斷您使用的語言編譯器是否會產生可驗證的類型安全程式碼，請參閱編譯器的文件。</span><span class="sxs-lookup"><span data-stu-id="5c96c-135">To determine whether the language compiler you use generates verifiably type-safe code, consult the compiler's documentation.</span></span> <span data-ttu-id="5c96c-136">如果您使用的語言編譯器，只有在您避免某些語言建構時，才會產生可驗證的類型安全程式碼，您可能想要使用[PEVerify 工具](../../../docs/framework/tools/peverify-exe-peverify-tool.md)來判斷您的程式碼是否可驗證的類型安全。</span><span class="sxs-lookup"><span data-stu-id="5c96c-136">If you use a language compiler that generates verifiably type-safe code only when you avoid certain language constructs, you might want to use the [PEVerify tool](../../../docs/framework/tools/peverify-exe-peverify-tool.md) to determine whether your code is verifiably type-safe.</span></span>  
  
 <span data-ttu-id="5c96c-137">非可驗證的類型安全程式碼，可以在安全性原則允許程式碼略過驗證時，嘗試執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-137">Code that is not verifiably type-safe can attempt to execute if security policy allows the code to bypass verification.</span></span> <span data-ttu-id="5c96c-138">不過，因為在執行階段用來隔離組件的機制中，類型安全是不可或缺的一部分，所以如果程式碼違反類型安全的規則，就無法可靠地強制執行安全性。</span><span class="sxs-lookup"><span data-stu-id="5c96c-138">However, because type safety is an essential part of the runtime's mechanism for isolating assemblies, security cannot be reliably enforced if code violates the rules of type safety.</span></span> <span data-ttu-id="5c96c-139">根據預設，非類型安全的程式碼必須源自本機電腦，才能執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-139">By default, code that is not type-safe is allowed to run only if it originates from the local computer.</span></span> <span data-ttu-id="5c96c-140">因此，行動程式碼應該是類型安全程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c96c-140">Therefore, mobile code should be type-safe.</span></span>  
  
<a name="secure_library"></a>   
## <a name="using-secure-class-libraries"></a><span data-ttu-id="5c96c-141">使用安全類別庫</span><span class="sxs-lookup"><span data-stu-id="5c96c-141">Using Secure Class Libraries</span></span>  
 <span data-ttu-id="5c96c-142">如果您的程式碼要求並且被授與類別庫所需的權限，就可以存取類別庫，而類別庫所公開的資源會被保護，以防未經授權的存取。</span><span class="sxs-lookup"><span data-stu-id="5c96c-142">If your code requests and is granted the permissions required by the class library, it will be allowed to access the library and the resources that the library exposes will be protected from unauthorized access.</span></span> <span data-ttu-id="5c96c-143">如果您的程式碼沒有適當的權限，將無法存取類別庫，而惡意程式碼將無法使用您的程式碼來間接存取受保護的資源。</span><span class="sxs-lookup"><span data-stu-id="5c96c-143">If your code does not have the appropriate permissions, it will not be allowed to access the class library, and malicious code will not be able to use your code to indirectly access protected resources.</span></span> <span data-ttu-id="5c96c-144">呼叫您的程式碼的其他程式碼，也必須要有類別庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="5c96c-144">Other code that calls your code must also have permission to access the library.</span></span> <span data-ttu-id="5c96c-145">如果沒有，您的程式碼也會被限制執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-145">If it does not, your code will be restricted from running as well.</span></span>  
  
 <span data-ttu-id="5c96c-146">程式碼存取安全性並不會消除撰寫程式碼時發生人為錯誤的可能性。</span><span class="sxs-lookup"><span data-stu-id="5c96c-146">Code access security does not eliminate the possibility of human error in writing code.</span></span> <span data-ttu-id="5c96c-147">不過，如果您的應用程式使用安全類別庫來存取受保護的資源，應用程式程式碼的安全性風險就會減少，因為類別庫會仔細檢查潛在的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="5c96c-147">However, if your application uses secure class libraries to access protected resources, the security risk for application code is decreased, because class libraries are closely scrutinized for potential security problems.</span></span>  
  
## <a name="declarative-security"></a><span data-ttu-id="5c96c-148">宣告式安全性</span><span class="sxs-lookup"><span data-stu-id="5c96c-148">Declarative Security</span></span>  
 <span data-ttu-id="5c96c-149">宣告式安全性語法會使用[屬性](../../../docs/standard/attributes/index.md)到將安全性資訊放[中繼資料](../../../docs/standard/metadata-and-self-describing-components.md)您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c96c-149">Declarative security syntax uses [attributes](../../../docs/standard/attributes/index.md) to place security information into the [metadata](../../../docs/standard/metadata-and-self-describing-components.md) of your code.</span></span> <span data-ttu-id="5c96c-150">屬性可以放在組件、類別或成員層級，以指出您想要使用的要求 (request)、要求 (demand) 或覆寫類型。</span><span class="sxs-lookup"><span data-stu-id="5c96c-150">Attributes can be placed at the assembly, class, or member level, to indicate the type of request, demand, or override you want to use.</span></span> <span data-ttu-id="5c96c-151">以 Common Language Runtime 為目標的應用程式中會使用要求 (request) 來通知執行階段安全性系統有關應用程式需要或不想要之權限的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c96c-151">Requests are used in applications that target the common language runtime to inform the runtime security system about the permissions that your application needs or does not want.</span></span> <span data-ttu-id="5c96c-152">程式庫中會使用要求 (demand) 和覆寫，以協助保護資源，不讓呼叫端存取，或是覆寫預設安全性行為。</span><span class="sxs-lookup"><span data-stu-id="5c96c-152">Demands and overrides are used in libraries to help protect resources from callers or to override default security behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c96c-153">在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]中，.NET Framework 安全性模型和術語已有重大變更。</span><span class="sxs-lookup"><span data-stu-id="5c96c-153">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="5c96c-154">如需有關這些變更的詳細資訊，請參閱[安全性變更](../../../docs/framework/security/security-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="5c96c-154">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="5c96c-155">若要使用宣告式安全性呼叫，您必須初始化權限物件的狀態資料，使其表示您需要的特定權限形式。</span><span class="sxs-lookup"><span data-stu-id="5c96c-155">In order to use declarative security calls, you must initialize the state data of the permission object so that it represents the particular form of permission you need.</span></span> <span data-ttu-id="5c96c-156">每個內建權限都有一個被傳遞 <xref:System.Security.Permissions.SecurityAction> 列舉的屬性，以描述您想要執行之安全性作業的類型。</span><span class="sxs-lookup"><span data-stu-id="5c96c-156">Every built-in permission has an attribute that is passed a <xref:System.Security.Permissions.SecurityAction> enumeration to describe the type of security operation you want to perform.</span></span> <span data-ttu-id="5c96c-157">不過，權限也會接受其本身專用的參數。</span><span class="sxs-lookup"><span data-stu-id="5c96c-157">However, permissions also accept their own parameters that are exclusive to them.</span></span>  
  
 <span data-ttu-id="5c96c-158">下列程式碼片段顯示的宣告式語法，可用來要求 (request) 您的程式碼呼叫端必須擁有名為 `MyPermission` 的自訂權限。</span><span class="sxs-lookup"><span data-stu-id="5c96c-158">The following code fragment shows declarative syntax for requesting that your code's callers have a custom permission called `MyPermission`.</span></span> <span data-ttu-id="5c96c-159">此權限是假設的自訂權限，並不存在於 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="5c96c-159">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="5c96c-160">在此範例中，宣告式呼叫是直接放在類別定義前面，指定此權限會套用到類別層級。</span><span class="sxs-lookup"><span data-stu-id="5c96c-160">In this example, the declarative call is placed directly before the class definition, specifying that this permission be applied to the class level.</span></span> <span data-ttu-id="5c96c-161">屬性會被傳遞**SecurityAction.Demand**結構，以指定呼叫端必須具備此權限才能執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-161">The attribute is passed a **SecurityAction.Demand** structure to specify that callers must have this permission in order to run.</span></span>  
  
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
  
## <a name="imperative-security"></a><span data-ttu-id="5c96c-162">命令式安全性</span><span class="sxs-lookup"><span data-stu-id="5c96c-162">Imperative Security</span></span>  
 <span data-ttu-id="5c96c-163">命令式安全性語法會藉由建立您想要叫用之權限物件的新執行個體來發出安全性呼叫。</span><span class="sxs-lookup"><span data-stu-id="5c96c-163">Imperative security syntax issues a security call by creating a new instance of the permission object you want to invoke.</span></span> <span data-ttu-id="5c96c-164">您可以使用命令式語法來執行要求 (demand) 和覆寫，但不能執行要求 (request)。</span><span class="sxs-lookup"><span data-stu-id="5c96c-164">You can use imperative syntax to perform demands and overrides, but not requests.</span></span>  
  
 <span data-ttu-id="5c96c-165">在進行安全性呼叫之前，您必須先初始化權限物件的狀態資料，使其表示您需要的特定權限形式。</span><span class="sxs-lookup"><span data-stu-id="5c96c-165">Before you make the security call, you must initialize the state data of the permission object so that it represents the particular form of the permission you need.</span></span> <span data-ttu-id="5c96c-166">例如，當建立<xref:System.Security.Permissions.FileIOPermission>物件，您可以使用建構函式來初始化**FileIOPermission**物件，使其表示無限制的存取所有檔案或無法存取檔案。</span><span class="sxs-lookup"><span data-stu-id="5c96c-166">For example, when creating a <xref:System.Security.Permissions.FileIOPermission> object, you can use the constructor to initialize the **FileIOPermission** object so that it represents either unrestricted access to all files or no access to files.</span></span> <span data-ttu-id="5c96c-167">或者，您可以使用不同**FileIOPermission**物件，傳遞參數來指出您想要的存取類型的物件，代表 （亦即，讀取、 附加或寫入），以及您想要的該物件保護哪些檔案。</span><span class="sxs-lookup"><span data-stu-id="5c96c-167">Or, you can use a different **FileIOPermission** object, passing parameters that indicate the type of access you want the object to represent (that is, read, append, or write) and what files you want the object to protect.</span></span>  
  
 <span data-ttu-id="5c96c-168">命令式安全性語法除了可以用來叫用單一安全性物件，還可以用來初始化權限集合中的權限群組。</span><span class="sxs-lookup"><span data-stu-id="5c96c-168">In addition to using imperative security syntax to invoke a single security object, you can use it to initialize a group of permissions in a permission set.</span></span> <span data-ttu-id="5c96c-169">例如，這項技術是唯一能可靠地執行[assert](../../../docs/framework/misc/using-the-assert-method.md)呼叫一個方法中的多個權限。</span><span class="sxs-lookup"><span data-stu-id="5c96c-169">For example, this technique is the only way to reliably perform [assert](../../../docs/framework/misc/using-the-assert-method.md) calls on multiple permissions in one method.</span></span> <span data-ttu-id="5c96c-170">使用 <xref:System.Security.PermissionSet> 和 <xref:System.Security.NamedPermissionSet> 類別來建立權限群組，然後呼叫適當的方法來叫用所需的安全性呼叫。</span><span class="sxs-lookup"><span data-stu-id="5c96c-170">Use the <xref:System.Security.PermissionSet> and <xref:System.Security.NamedPermissionSet> classes to create a group of permissions and then call the appropriate method to invoke the desired security call.</span></span>  
  
 <span data-ttu-id="5c96c-171">您可以使用命令式語法來執行要求 (demand) 和覆寫，但不能執行要求 (request)。</span><span class="sxs-lookup"><span data-stu-id="5c96c-171">You can use imperative syntax to perform demands and overrides, but not requests.</span></span> <span data-ttu-id="5c96c-172">如果只有在執行階段才會知道初始化權限狀態所需的資訊，您可以使用命令式語法來執行要求 (demand) 和覆寫，而不要使用宣告式語法。</span><span class="sxs-lookup"><span data-stu-id="5c96c-172">You might use imperative syntax for demands and overrides instead of declarative syntax when information that you need in order to initialize the permission state becomes known only at run time.</span></span> <span data-ttu-id="5c96c-173">例如，如果您想要確定呼叫端擁有讀取特定檔案的權限，但是在執行階段之前，都不知道該檔案的名稱，請使用命令式要求 (demand)。</span><span class="sxs-lookup"><span data-stu-id="5c96c-173">For example, if you want to ensure that callers have permission to read a certain file, but you do not know the name of that file until run time, use an imperative demand.</span></span> <span data-ttu-id="5c96c-174">當您需要在執行階段判斷某條件是否成立，以及根據測試結果，是否產生安全性要求 (demand) 時，您可能也會選擇使用命令式檢查，而不是宣告式檢查，</span><span class="sxs-lookup"><span data-stu-id="5c96c-174">You might also choose to use imperative checks instead of declarative checks when you need to determine at run time whether a condition holds and, based on the result of the test, make a security demand (or not).</span></span>  
  
 <span data-ttu-id="5c96c-175">下列程式碼片段所顯示的命令式語法，可用來要求 (request) 您的程式碼呼叫端必須擁有名為 `MyPermission` 的自訂權限。</span><span class="sxs-lookup"><span data-stu-id="5c96c-175">The following code fragment shows imperative syntax for requesting that your code's callers have a custom permission called `MyPermission`.</span></span> <span data-ttu-id="5c96c-176">此權限是假設的自訂權限，並不存在於 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="5c96c-176">This permission is a hypothetical custom permission and does not exist in the .NET Framework.</span></span> <span data-ttu-id="5c96c-177">`MyMethod` 中建立了一個新的 `MyPermision` 執行個體，只保護具有安全性呼叫的這個方法。</span><span class="sxs-lookup"><span data-stu-id="5c96c-177">A new instance of `MyPermision` is created in `MyMethod`, guarding only this method with the security call.</span></span>  
  
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
  
## <a name="using-managed-wrapper-classes"></a><span data-ttu-id="5c96c-178">使用 Managed 包裝函式類別</span><span class="sxs-lookup"><span data-stu-id="5c96c-178">Using Managed Wrapper Classes</span></span>  
 <span data-ttu-id="5c96c-179">大部分應用程式和元件 (安全程式庫除外) 都不應該直接呼叫 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c96c-179">Most applications and components (except secure libraries) should not directly call unmanaged code.</span></span> <span data-ttu-id="5c96c-180">這有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="5c96c-180">There are several reasons for this.</span></span> <span data-ttu-id="5c96c-181">如果程式碼直接呼叫 Unmanaged 程式碼，可能在許多情況下都不允許它執行，因為程式碼必須被授與高度信任，才能呼叫原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="5c96c-181">If code calls unmanaged code directly, it will not be allowed to run in many circumstances because code must be granted a high level of trust to call native code.</span></span> <span data-ttu-id="5c96c-182">如果將原則修改為可允許這類應用程式執行，可能會大幅降低系統的安全性，而讓應用程式能夠自由執行幾乎任何作業。</span><span class="sxs-lookup"><span data-stu-id="5c96c-182">If policy is modified to allow such an application to run, it can significantly weaken the security of the system, leaving the application free to perform almost any operation.</span></span>  
  
 <span data-ttu-id="5c96c-183">此外，有權存取 Unmanaged 程式碼的程式碼可能可以藉由呼叫 Unmanaged API，來執行幾乎任何作業。</span><span class="sxs-lookup"><span data-stu-id="5c96c-183">Additionally, code that has permission to access unmanaged code can probably perform almost any operation by calling into an unmanaged API.</span></span> <span data-ttu-id="5c96c-184">有權呼叫 unmanaged 程式碼的程式碼不需要的例如<xref:System.Security.Permissions.FileIOPermission>來存取檔案，它可以直接呼叫 unmanaged (Win32) 檔案 API，略過的 managed 的檔案 API 需要**FileIOPermission**。</span><span class="sxs-lookup"><span data-stu-id="5c96c-184">For example, code that has permission to call unmanaged code does not need <xref:System.Security.Permissions.FileIOPermission> to access a file; it can just call an unmanaged (Win32) file API directly, bypassing the managed file API that requires **FileIOPermission**.</span></span> <span data-ttu-id="5c96c-185">如果 Managed 程式碼有權呼叫 Unmanaged 程式碼，並且真的直接呼叫 Unmanaged 程式碼，安全性系統將無法可靠地強制執行安全性限制，因為執行階段無法對 Unmanaged 程式碼強制執行這類限制。</span><span class="sxs-lookup"><span data-stu-id="5c96c-185">If managed code has permission to call into unmanaged code and does call directly into unmanaged code, the security system will be unable to reliably enforce security restrictions, since the runtime cannot enforce such restrictions on unmanaged code.</span></span>  
  
 <span data-ttu-id="5c96c-186">如果您想要讓應用程式執行需要存取 Unmanaged 程式碼的作業，其應透過包裝所需功能的受信任 Managed 類別 (如果這種類別存在的話) 來執行。</span><span class="sxs-lookup"><span data-stu-id="5c96c-186">If you want your application to perform an operation that requires accessing unmanaged code, it should do so through a trusted managed class that wraps the required functionality (if such a class exists).</span></span> <span data-ttu-id="5c96c-187">如果安全類別庫中已經有包裝函式類別存在，請不要建立您自己的包裝函式類別。</span><span class="sxs-lookup"><span data-stu-id="5c96c-187">Do not create a wrapper class yourself if one already exists in a secure class library.</span></span> <span data-ttu-id="5c96c-188">包裝函式類別 (必須被授與高度信任，才能呼叫 Unmanaged 程式碼) 負責要求 (demand) 其呼叫端擁有適當的權限。</span><span class="sxs-lookup"><span data-stu-id="5c96c-188">The wrapper class, which must be granted a high degree of trust to be allowed to make the call into unmanaged code, is responsible for demanding that its callers have the appropriate permissions.</span></span> <span data-ttu-id="5c96c-189">如果您使用包裝函式類別，您的程式碼只需要要求 (request) 以及被授與包裝函式類別所要求 (demand) 的權限。</span><span class="sxs-lookup"><span data-stu-id="5c96c-189">If you use the wrapper class, your code only needs to request and be granted the permissions that the wrapper class demands.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c96c-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c96c-190">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.NamedPermissionSet>  
 <xref:System.Security.Permissions.SecurityAction>  
 [<span data-ttu-id="5c96c-191">Assert</span><span class="sxs-lookup"><span data-stu-id="5c96c-191">Assert</span></span>](../../../docs/framework/misc/using-the-assert-method.md)  
 [<span data-ttu-id="5c96c-192">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="5c96c-192">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)  
 [<span data-ttu-id="5c96c-193">程式碼存取安全性的基本概念</span><span class="sxs-lookup"><span data-stu-id="5c96c-193">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 [<span data-ttu-id="5c96c-194">屬性</span><span class="sxs-lookup"><span data-stu-id="5c96c-194">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="5c96c-195">中繼資料和自我描述元件</span><span class="sxs-lookup"><span data-stu-id="5c96c-195">Metadata and Self-Describing Components</span></span>](../../../docs/standard/metadata-and-self-describing-components.md)
