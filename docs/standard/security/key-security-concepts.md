---
title: "重要的安全性概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8e11e22d98954d9656357e11fbb4ca94ad673659
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="key-security-concepts"></a><span data-ttu-id="7ba35-102">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="7ba35-102">Key Security Concepts</span></span>
<span data-ttu-id="7ba35-103">Microsoft.NET Framework 提供以角色為基礎的安全性，以幫助解除對行動程式碼安全性的相關疑慮，並提供支援，讓元件能夠判斷哪些使用者有權執行。</span><span class="sxs-lookup"><span data-stu-id="7ba35-103">The Microsoft .NET Framework offers role-based security to help address security concerns about mobile code and to provide support that enables components to determine what users are authorized to do.</span></span>  
  
## <a name="type-safety-and-security"></a><span data-ttu-id="7ba35-104">類型安全和安全性</span><span class="sxs-lookup"><span data-stu-id="7ba35-104">Type safety and security</span></span>  
 <span data-ttu-id="7ba35-105">類型安全程式碼只會存取經授權存取的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="7ba35-105">Type-safe code accesses only the memory locations it is authorized to access.</span></span> <span data-ttu-id="7ba35-106">(這裡所討論的類型安全是專指記憶體類型安全，不應與廣義的類型安全混淆。)例如，類型安全程式碼無法從另一個物件的私用欄位讀取值。</span><span class="sxs-lookup"><span data-stu-id="7ba35-106">(For this discussion, type safety specifically refers to memory type safety and should not be confused with type safety in a broader respect.) For example, type-safe code cannot read values from another object's private fields.</span></span> <span data-ttu-id="7ba35-107">它只會以妥善定義、可允許的方式來存取類型。</span><span class="sxs-lookup"><span data-stu-id="7ba35-107">It accesses types only in well-defined, allowable ways.</span></span>  
  
 <span data-ttu-id="7ba35-108">在 Just-In-Time (JIT) 編譯期間，選擇性的驗證程序會檢查中繼資料，以及要以 JIT 編譯成原生機器程式碼之方法的 Microsoft Intermediate Language (MSIL)，以驗證其類型安全。</span><span class="sxs-lookup"><span data-stu-id="7ba35-108">During just-in-time (JIT) compilation, an optional verification process examines the metadata and Microsoft intermediate language (MSIL) of a method to be JIT-compiled into native machine code to verify that they are type safe.</span></span> <span data-ttu-id="7ba35-109">如果程式碼具有略過驗證的權限，則會略過此程序。</span><span class="sxs-lookup"><span data-stu-id="7ba35-109">This process is skipped if the code has permission to bypass verification.</span></span> <span data-ttu-id="7ba35-110">如需有關驗證的詳細資訊，請參閱 [Managed 執行程序](../../../docs/standard/managed-execution-process.md)。</span><span class="sxs-lookup"><span data-stu-id="7ba35-110">For more information about verification, see [Managed Execution Process](../../../docs/standard/managed-execution-process.md).</span></span>  
  
 <span data-ttu-id="7ba35-111">雖然沒有強制要驗證類型安全才能執行 Managed 程式碼，但是在組件隔離和強制執行安全性的作業中，類型安全扮演相當重要的角色。</span><span class="sxs-lookup"><span data-stu-id="7ba35-111">Although verification of type safety is not mandatory to run managed code, type safety plays a crucial role in assembly isolation and security enforcement.</span></span> <span data-ttu-id="7ba35-112">當程式碼類型安全時，Common Language Runtime 可以將組件彼此完全隔離。</span><span class="sxs-lookup"><span data-stu-id="7ba35-112">When code is type safe, the common language runtime can completely isolate assemblies from each other.</span></span> <span data-ttu-id="7ba35-113">此隔離有助於確保組件無法對彼此產生不利的影響，而且也會增加應用程式的可靠性。</span><span class="sxs-lookup"><span data-stu-id="7ba35-113">This isolation helps ensure that assemblies cannot adversely affect each other and it increases application reliability.</span></span> <span data-ttu-id="7ba35-114">類型安全元件即使受信任的層級不同，還是可以在相同的處理序中安全地執行。</span><span class="sxs-lookup"><span data-stu-id="7ba35-114">Type-safe components can execute safely in the same process even if they are trusted at different levels.</span></span> <span data-ttu-id="7ba35-115">當程式碼不是類型安全時，可能會發生不必要的副作用。</span><span class="sxs-lookup"><span data-stu-id="7ba35-115">When code is not type safe, unwanted side effects can occur.</span></span> <span data-ttu-id="7ba35-116">例如，執行階段無法防止 Managed 程式碼呼叫機器碼 (Unmanaged) 及執行惡意的作業。</span><span class="sxs-lookup"><span data-stu-id="7ba35-116">For example, the runtime cannot prevent managed code from calling into native (unmanaged) code and performing malicious operations.</span></span> <span data-ttu-id="7ba35-117">當程式碼為類型安全時，執行階段的安全性強制機制可確保它不會存取原生程式碼，除非它有這樣的權限。</span><span class="sxs-lookup"><span data-stu-id="7ba35-117">When code is type safe, the runtime's security enforcement mechanism ensures that it does not access native code unless it has permission to do so.</span></span> <span data-ttu-id="7ba35-118">所有不是類型安全的程式碼，都必須被授與具有通過之列舉成員 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> 的 <xref:System.Security.Permissions.SecurityPermission>，才能執行。</span><span class="sxs-lookup"><span data-stu-id="7ba35-118">All code that is not type safe must have been granted <xref:System.Security.Permissions.SecurityPermission> with the passed enum member <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> to run.</span></span>  
  
 <span data-ttu-id="7ba35-119">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../docs/framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="7ba35-119">For more information, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="principal"></a><span data-ttu-id="7ba35-120">主體</span><span class="sxs-lookup"><span data-stu-id="7ba35-120">Principal</span></span>  
 <span data-ttu-id="7ba35-121">主體代表使用者的身分識別與角色，並且會代表使用者採取行動。</span><span class="sxs-lookup"><span data-stu-id="7ba35-121">A principal represents the identity and role of a user and acts on the user's behalf.</span></span> <span data-ttu-id="7ba35-122">在 .NET Framework 中，以角色為基礎的安全性可支援三種主體：</span><span class="sxs-lookup"><span data-stu-id="7ba35-122">Role-based security in the .NET Framework supports three kinds of principals:</span></span>  
  
-   <span data-ttu-id="7ba35-123">泛型主體代表獨立於 Windows 使用者和角色而存在的使用者和角色。</span><span class="sxs-lookup"><span data-stu-id="7ba35-123">Generic principals represent users and roles that exist independent of Windows users and roles.</span></span>  
  
-   <span data-ttu-id="7ba35-124">Windows 主體代表 Windows 使用者及其角色 (或其 Windows 群組)。</span><span class="sxs-lookup"><span data-stu-id="7ba35-124">Windows principals represent Windows users and their roles (or their Windows groups).</span></span> <span data-ttu-id="7ba35-125">Windows 主體可以模擬另一位使用者，這表示該主體可以代表使用者存取資源，同時呈現屬於該使用者身分識別。</span><span class="sxs-lookup"><span data-stu-id="7ba35-125">A Windows principal can impersonate another user, which means that the principal can access a resource on a user's behalf while presenting the identity that belongs to that user.</span></span>  
  
-   <span data-ttu-id="7ba35-126">自訂主體可以由應用程式以該特定應用程式所需的任何方式來定義。</span><span class="sxs-lookup"><span data-stu-id="7ba35-126">Custom principals can be defined by an application in any way that is needed for that particular application.</span></span> <span data-ttu-id="7ba35-127">其可擴充主體身分識別和角色的基本概念。</span><span class="sxs-lookup"><span data-stu-id="7ba35-127">They can extend the basic notion of the principal's identity and roles.</span></span>  
  
 <span data-ttu-id="7ba35-128">如需詳細資訊，請參閱[主體和身分識別物件](../../../docs/standard/security/principal-and-identity-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="7ba35-128">For more information, see [Principal and Identity Objects](../../../docs/standard/security/principal-and-identity-objects.md).</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="7ba35-129">驗證</span><span class="sxs-lookup"><span data-stu-id="7ba35-129">Authentication</span></span>  
 <span data-ttu-id="7ba35-130">驗證是探索並確認主體身分識別的程序，它會檢查使用者的認證，並針對某授權單位來驗證那些認證。</span><span class="sxs-lookup"><span data-stu-id="7ba35-130">Authentication is the process of discovering and verifying the identity of a principal by examining the user's credentials and validating those credentials against some authority.</span></span> <span data-ttu-id="7ba35-131">在驗證期間取得的資訊可直接供是由您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="7ba35-131">The information obtained during authentication is directly usable by your code.</span></span> <span data-ttu-id="7ba35-132">您也可以使用 .NET Framework 以角色為基礎的安全性來驗證目前使用者，以及判斷是否允許該主體存取您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ba35-132">You can also use .NET Framework role-based security to authenticate the current user and to determine whether to allow that principal to access your code.</span></span> <span data-ttu-id="7ba35-133">請參閱 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> 方法的多載，以取得如何針對特定角色來驗證主體的範例。</span><span class="sxs-lookup"><span data-stu-id="7ba35-133">See the overloads of the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> method for examples of how to authenticate the principal for specific roles.</span></span> <span data-ttu-id="7ba35-134">例如，您可以使用 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> 多載來判斷目前使用者是否為系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="7ba35-134">For example, you can use the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> overload to determine if the current user is a member of the Administrators group.</span></span>  
  
 <span data-ttu-id="7ba35-135">當今所使用的驗證機制非常多樣化，其中有許多可以搭配 .NET Framework 以角色為基礎的安全性。</span><span class="sxs-lookup"><span data-stu-id="7ba35-135">A variety of authentication mechanisms are used today, many of which can be used with .NET Framework role-based security.</span></span> <span data-ttu-id="7ba35-136">部分最常用的機制有基本、摘要式、Passport、作業系統 (例如 NTLM 或 Kerberos) 或應用程式定義的機制。</span><span class="sxs-lookup"><span data-stu-id="7ba35-136">Some of the most commonly used mechanisms are basic, digest, Passport, operating system (such as NTLM or Kerberos), or application-defined mechanisms.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7ba35-137">範例</span><span class="sxs-lookup"><span data-stu-id="7ba35-137">Example</span></span>  
 <span data-ttu-id="7ba35-138">下列範例需要由作用中的主體做為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="7ba35-138">The following example requires that the active principal be an administrator.</span></span> <span data-ttu-id="7ba35-139">`name` 參數為 `null`，可讓做為系統管理員的任何使用者傳遞要求。</span><span class="sxs-lookup"><span data-stu-id="7ba35-139">The `name` parameter is `null`, which allows any user who is an administrator to pass the demand.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ba35-140">在 Windows Vista 中，使用者帳戶控制 (UAC) 會判斷使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="7ba35-140">In Windows Vista, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="7ba35-141">如果您是內建 Administrators 群組的成員，系統會將兩個執行階段存取語彙基元 (Token) 指派給您：標準使用者存取語彙基元及管理員存取語彙基元。</span><span class="sxs-lookup"><span data-stu-id="7ba35-141">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="7ba35-142">根據預設，您會屬於標準使用者角色。</span><span class="sxs-lookup"><span data-stu-id="7ba35-142">By default, you are in the standard user role.</span></span> <span data-ttu-id="7ba35-143">若要執行需要您是系統管理員的程式碼，您必須先將權限從標準使用者提高為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="7ba35-143">To execute the code that requires you to be an administrator, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="7ba35-144">您可以在啟動應用程式時，以滑鼠右鍵按一下應用程式圖示，並指出您想要以系統管理員身分執行，藉此提高為系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="7ba35-144">You can do this when you start an application by right-clicking the application icon and indicating that you want to run as an administrator.</span></span>  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 <span data-ttu-id="7ba35-145">下列範例示範如何判斷主體的身分識別，以及可供主體使用的角色。</span><span class="sxs-lookup"><span data-stu-id="7ba35-145">The following example demonstrates how to determine the identity of the principal and the roles available to the principal.</span></span> <span data-ttu-id="7ba35-146">此範例的應用程式可能是要確認目前的使用者是您允許使用您的應用程式的角色。</span><span class="sxs-lookup"><span data-stu-id="7ba35-146">An application of this example might be to confirm that the current user is in a role you allow for using your application.</span></span>  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a><span data-ttu-id="7ba35-147">授權</span><span class="sxs-lookup"><span data-stu-id="7ba35-147">Authorization</span></span>  
 <span data-ttu-id="7ba35-148">授權是決定是否允許主體執行所要求動作的程序。</span><span class="sxs-lookup"><span data-stu-id="7ba35-148">Authorization is the process of determining whether a principal is allowed to perform a requested action.</span></span> <span data-ttu-id="7ba35-149">授權會在驗證之後進行，它會使用主體的身分識別和角色相關資訊來判斷主體可以存取哪些資源。</span><span class="sxs-lookup"><span data-stu-id="7ba35-149">Authorization occurs after authentication and uses information about the principal's identity and roles to determine what resources the principal can access.</span></span> <span data-ttu-id="7ba35-150">您可以使用 .NET Framework 以角色為基礎的安全性來實作授權。</span><span class="sxs-lookup"><span data-stu-id="7ba35-150">You can use .NET Framework role-based security to implement authorization.</span></span>
