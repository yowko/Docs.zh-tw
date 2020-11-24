---
title: 重要的安全性概念
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET]
- security [.NET], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
ms.openlocfilehash: 73e4d0474810d097c5eee8b99ae30b6096ee1695
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687543"
---
# <a name="key-security-concepts"></a><span data-ttu-id="d0aa1-102">重要的安全性概念</span><span class="sxs-lookup"><span data-stu-id="d0aa1-102">Key Security Concepts</span></span>

> [!NOTE]
> <span data-ttu-id="d0aa1-103">本文適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="d0aa1-104">如需 ASP.NET Core 的詳細資訊，請參閱 [ASP.NET Core 安全性的總覽](/aspnet/core/security/)。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-104">For information about ASP.NET Core, see [Overview of ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="d0aa1-105">.NET 提供以角色為基礎的安全性，以協助解決行動程式碼的安全性疑慮，並提供支援，讓元件能夠判斷哪些使用者已獲授權。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-105">.NET offers role-based security to help address security concerns about mobile code and to provide support that enables components to determine what users are authorized to do.</span></span>  
  
## <a name="type-safety-and-security"></a><span data-ttu-id="d0aa1-106">類型安全和安全性</span><span class="sxs-lookup"><span data-stu-id="d0aa1-106">Type safety and security</span></span>  

<span data-ttu-id="d0aa1-107">類型安全程式碼只會存取經授權存取的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-107">Type-safe code accesses only the memory locations it is authorized to access.</span></span> <span data-ttu-id="d0aa1-108"> (在此討論中，型別安全特別指的是記憶體型別安全，而且不應該與較廣泛的型別安全性混淆。 ) 例如，型別安全程式碼無法從其他物件的私用欄位中讀取值。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-108">(For this discussion, type safety specifically refers to memory type safety and should not be confused with type safety in a broader respect.) For example, type-safe code cannot read values from another object's private fields.</span></span> <span data-ttu-id="d0aa1-109">它只會以妥善定義、可允許的方式來存取類型。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-109">It accesses types only in well-defined, allowable ways.</span></span>  
  
<span data-ttu-id="d0aa1-110">在 Just-In-Time (JIT) 編譯期間，選擇性的驗證程序會檢查中繼資料，以及要以 JIT 編譯成原生機器程式碼之方法的 Microsoft Intermediate Language (MSIL)，以驗證其類型安全。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-110">During just-in-time (JIT) compilation, an optional verification process examines the metadata and Microsoft intermediate language (MSIL) of a method to be JIT-compiled into native machine code to verify that they are type safe.</span></span> <span data-ttu-id="d0aa1-111">如果程式碼具有略過驗證的權限，則會略過此程序。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-111">This process is skipped if the code has permission to bypass verification.</span></span> <span data-ttu-id="d0aa1-112">如需有關驗證的詳細資訊，請參閱 [Managed 執行程序](../managed-execution-process.md)。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-112">For more information about verification, see [Managed Execution Process](../managed-execution-process.md).</span></span>  
  
<span data-ttu-id="d0aa1-113">雖然沒有強制要驗證類型安全才能執行 Managed 程式碼，但是在組件隔離和強制執行安全性的作業中，類型安全扮演相當重要的角色。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-113">Although verification of type safety is not mandatory to run managed code, type safety plays a crucial role in assembly isolation and security enforcement.</span></span> <span data-ttu-id="d0aa1-114">當程式碼類型安全時，Common Language Runtime 可以將組件彼此完全隔離。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-114">When code is type safe, the common language runtime can completely isolate assemblies from each other.</span></span> <span data-ttu-id="d0aa1-115">此隔離有助於確保組件無法對彼此產生不利的影響，而且也會增加應用程式的可靠性。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-115">This isolation helps ensure that assemblies cannot adversely affect each other and it increases application reliability.</span></span> <span data-ttu-id="d0aa1-116">類型安全元件即使受信任的層級不同，還是可以在相同的處理序中安全地執行。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-116">Type-safe components can execute safely in the same process even if they are trusted at different levels.</span></span> <span data-ttu-id="d0aa1-117">當程式碼不是類型安全時，可能會發生不必要的副作用。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-117">When code is not type safe, unwanted side effects can occur.</span></span> <span data-ttu-id="d0aa1-118">例如，執行階段無法防止 Managed 程式碼呼叫機器碼 (Unmanaged) 及執行惡意的作業。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-118">For example, the runtime cannot prevent managed code from calling into native (unmanaged) code and performing malicious operations.</span></span> <span data-ttu-id="d0aa1-119">當程式碼為類型安全時，執行階段的安全性強制機制可確保它不會存取原生程式碼，除非它有這樣的權限。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-119">When code is type safe, the runtime's security enforcement mechanism ensures that it does not access native code unless it has permission to do so.</span></span> <span data-ttu-id="d0aa1-120">所有不是類型安全的程式碼，都必須被授與具有通過之列舉成員 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> 的 <xref:System.Security.Permissions.SecurityPermission>，才能執行。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-120">All code that is not type safe must have been granted <xref:System.Security.Permissions.SecurityPermission> with the passed enum member <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> to run.</span></span>  
  
<span data-ttu-id="d0aa1-121">如需詳細資訊，請參閱 [Code Access Security Basics](../../framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-121">For more information, see [Code Access Security Basics](../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="principal"></a><span data-ttu-id="d0aa1-122">主體</span><span class="sxs-lookup"><span data-stu-id="d0aa1-122">Principal</span></span>  

<span data-ttu-id="d0aa1-123">主體代表使用者的身分識別與角色，並且會代表使用者採取行動。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-123">A principal represents the identity and role of a user and acts on the user's behalf.</span></span> <span data-ttu-id="d0aa1-124">.NET 中以角色為基礎的安全性支援三種主體：</span><span class="sxs-lookup"><span data-stu-id="d0aa1-124">Role-based security in .NET supports three kinds of principals:</span></span>  
  
- <span data-ttu-id="d0aa1-125">泛型主體代表獨立於 Windows 使用者和角色而存在的使用者和角色。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-125">Generic principals represent users and roles that exist independent of Windows users and roles.</span></span>  
  
- <span data-ttu-id="d0aa1-126">Windows 主體代表 Windows 使用者及其角色 (或其 Windows 群組)。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-126">Windows principals represent Windows users and their roles (or their Windows groups).</span></span> <span data-ttu-id="d0aa1-127">Windows 主體可以模擬另一位使用者，這表示該主體可以代表使用者存取資源，同時呈現屬於該使用者身分識別。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-127">A Windows principal can impersonate another user, which means that the principal can access a resource on a user's behalf while presenting the identity that belongs to that user.</span></span>  
  
- <span data-ttu-id="d0aa1-128">自訂主體可以由應用程式以該特定應用程式所需的任何方式來定義。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-128">Custom principals can be defined by an application in any way that is needed for that particular application.</span></span> <span data-ttu-id="d0aa1-129">其可擴充主體身分識別和角色的基本概念。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-129">They can extend the basic notion of the principal's identity and roles.</span></span>  
  
<span data-ttu-id="d0aa1-130">如需詳細資訊，請參閱[主體和身分識別物件](principal-and-identity-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-130">For more information, see [Principal and Identity Objects](principal-and-identity-objects.md).</span></span>  
  
## <a name="authentication"></a><span data-ttu-id="d0aa1-131">驗證</span><span class="sxs-lookup"><span data-stu-id="d0aa1-131">Authentication</span></span>  

<span data-ttu-id="d0aa1-132">驗證是探索並確認主體身分識別的程序，它會檢查使用者的認證，並針對某授權單位來驗證那些認證。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-132">Authentication is the process of discovering and verifying the identity of a principal by examining the user's credentials and validating those credentials against some authority.</span></span> <span data-ttu-id="d0aa1-133">在驗證期間取得的資訊可直接供是由您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-133">The information obtained during authentication is directly usable by your code.</span></span> <span data-ttu-id="d0aa1-134">您也可以使用 .NET 以角色為基礎的安全性來驗證目前使用者，並判斷是否允許該主體存取您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-134">You can also use .NET role-based security to authenticate the current user and to determine whether to allow that principal to access your code.</span></span> <span data-ttu-id="d0aa1-135">請參閱 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> 方法的多載，以取得如何針對特定角色來驗證主體的範例。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-135">See the overloads of the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> method for examples of how to authenticate the principal for specific roles.</span></span> <span data-ttu-id="d0aa1-136">例如，您可以使用 <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> 多載來判斷目前使用者是否為系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-136">For example, you can use the <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> overload to determine if the current user is a member of the Administrators group.</span></span>  
  
<span data-ttu-id="d0aa1-137">現今使用各種不同的驗證機制，其中有許多可搭配 .NET 以角色為基礎的安全性使用。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-137">A variety of authentication mechanisms are used today, many of which can be used with .NET role-based security.</span></span> <span data-ttu-id="d0aa1-138">部分最常用的機制有基本、摘要式、Passport、作業系統 (例如 NTLM 或 Kerberos) 或應用程式定義的機制。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-138">Some of the most commonly used mechanisms are basic, digest, Passport, operating system (such as NTLM or Kerberos), or application-defined mechanisms.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d0aa1-139">範例</span><span class="sxs-lookup"><span data-stu-id="d0aa1-139">Example</span></span>  

<span data-ttu-id="d0aa1-140">下列範例需要由作用中的主體做為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-140">The following example requires that the active principal be an administrator.</span></span> <span data-ttu-id="d0aa1-141">`name` 參數為 `null`，可讓做為系統管理員的任何使用者傳遞要求。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-141">The `name` parameter is `null`, which allows any user who is an administrator to pass the demand.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0aa1-142">在 Windows Vista 中，使用者帳戶控制 (UAC) 會判斷使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-142">In Windows Vista, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="d0aa1-143">如果您是內建 Administrators 群組的成員，系統會將兩個執行階段存取語彙基元 (Token) 指派給您：標準使用者存取語彙基元及管理員存取語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-143">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="d0aa1-144">根據預設，您會屬於標準使用者角色。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-144">By default, you are in the standard user role.</span></span> <span data-ttu-id="d0aa1-145">若要執行需要您是系統管理員的程式碼，您必須先將權限從標準使用者提高為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-145">To execute the code that requires you to be an administrator, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="d0aa1-146">您可以在啟動應用程式時，以滑鼠右鍵按一下應用程式圖示，並指出您想要以系統管理員身分執行，藉此提高為系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-146">You can do this when you start an application by right-clicking the application icon and indicating that you want to run as an administrator.</span></span>  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 <span data-ttu-id="d0aa1-147">下列範例示範如何判斷主體的身分識別，以及可供主體使用的角色。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-147">The following example demonstrates how to determine the identity of the principal and the roles available to the principal.</span></span> <span data-ttu-id="d0aa1-148">此範例的應用程式可能是要確認目前的使用者是您允許使用您的應用程式的角色。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-148">An application of this example might be to confirm that the current user is in a role you allow for using your application.</span></span>  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a><span data-ttu-id="d0aa1-149">授權</span><span class="sxs-lookup"><span data-stu-id="d0aa1-149">Authorization</span></span>  

<span data-ttu-id="d0aa1-150">授權是決定是否允許主體執行所要求動作的程序。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-150">Authorization is the process of determining whether a principal is allowed to perform a requested action.</span></span> <span data-ttu-id="d0aa1-151">授權會在驗證之後進行，它會使用主體的身分識別和角色相關資訊來判斷主體可以存取哪些資源。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-151">Authorization occurs after authentication and uses information about the principal's identity and roles to determine what resources the principal can access.</span></span> <span data-ttu-id="d0aa1-152">您可以使用 .NET 以角色為基礎的安全性來執行授權。</span><span class="sxs-lookup"><span data-stu-id="d0aa1-152">You can use .NET role-based security to implement authorization.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0aa1-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0aa1-153">See also</span></span>

- [<span data-ttu-id="d0aa1-154">ASP.NET Core 安全性</span><span class="sxs-lookup"><span data-stu-id="d0aa1-154">ASP.NET Core Security</span></span>](/aspnet/core/security/)
