---
title: 模擬和還原
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bc5b4a9bef51ac1591bdeb21651cee624d552b2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137443"
---
# <a name="impersonating-and-reverting"></a><span data-ttu-id="6277b-102">模擬和還原</span><span class="sxs-lookup"><span data-stu-id="6277b-102">Impersonating and Reverting</span></span>
<span data-ttu-id="6277b-103">有時候您可能需要取得 Windows 帳戶權杖，才能模擬 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="6277b-103">Sometimes you might need to obtain a Windows account token to impersonate a Windows account.</span></span> <span data-ttu-id="6277b-104">例如，ASP.NET 型應用程式可能必須在不同的時間代表數個使用者。</span><span class="sxs-lookup"><span data-stu-id="6277b-104">For example, your ASP.NET-based application might have to act on behalf of several users at different times.</span></span> <span data-ttu-id="6277b-105">您的應用程式可能會接受來自網際網路資訊服務 (IIS) 代表系統管理員的權杖、模擬該使用者、執行作業，然後還原成之前的身分識別。</span><span class="sxs-lookup"><span data-stu-id="6277b-105">Your application might accept a token that represents an administrator from Internet Information Services (IIS), impersonate that user, perform an operation, and revert to the previous identity.</span></span> <span data-ttu-id="6277b-106">接下來，它可能會接受來自 IIS 代表具有較少權限的使用者的權杖、執行某項作業，然後再次還原。</span><span class="sxs-lookup"><span data-stu-id="6277b-106">Next, it might accept a token from IIS that represents a user with fewer rights, perform some operation, and revert again.</span></span>  
  
 <span data-ttu-id="6277b-107">當您的應用程式必須模擬尚未由 IIS 附加至目前執行緒的 Windows 帳戶時，您必須擷取該帳戶的權杖並使用它來啟動帳戶。</span><span class="sxs-lookup"><span data-stu-id="6277b-107">In situations where your application must impersonate a Windows account that has not been attached to the current thread by IIS, you must retrieve that account's token and use it to activate the account.</span></span> <span data-ttu-id="6277b-108">您可以執行下列工作來達成這點：</span><span class="sxs-lookup"><span data-stu-id="6277b-108">You can do this by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="6277b-109">藉由呼叫未受管理的 **LogonUser** 方法，擷取特定使用者的帳戶權杖。</span><span class="sxs-lookup"><span data-stu-id="6277b-109">Retrieve an account token for a particular user by making a call to the unmanaged **LogonUser** method.</span></span> <span data-ttu-id="6277b-110">這個方法不在 .NET Framework 基底類別庫中，而是位於未受管理的 **advapi32.dll**。</span><span class="sxs-lookup"><span data-stu-id="6277b-110">This method is not in the .NET Framework base class library, but is located in the unmanaged **advapi32.dll**.</span></span> <span data-ttu-id="6277b-111">存取 Unmanaged 程式碼中的方法是進階的操作，已超出本文的討論範圍。</span><span class="sxs-lookup"><span data-stu-id="6277b-111">Accessing methods in unmanaged code is an advanced operation and is beyond the scope of this discussion.</span></span> <span data-ttu-id="6277b-112">如需詳細資訊，請參閱[與 Unmanaged 程式碼互通](../../../docs/framework/interop/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6277b-112">For more information, see [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="6277b-113">如需 **LogonUser** 方法和 **advapi32.dll** 的詳細資訊，請參閱 Platform SDK 文件。</span><span class="sxs-lookup"><span data-stu-id="6277b-113">For more information about the **LogonUser** method and **advapi32.dll**, see the Platform SDK documentation.</span></span>  
  
2.  <span data-ttu-id="6277b-114">建立 **WindowsIdentity** 類別的新執行個體，並傳遞權杖。</span><span class="sxs-lookup"><span data-stu-id="6277b-114">Create a new instance of the **WindowsIdentity** class, passing the token.</span></span> <span data-ttu-id="6277b-115">下列程式碼會示範此呼叫，其中 `hToken` 代表 Windows 權杖。</span><span class="sxs-lookup"><span data-stu-id="6277b-115">The following code demonstrates this call, where `hToken` represents a Windows token.</span></span>  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  <span data-ttu-id="6277b-116">藉由建立的新執行個體開始模擬<xref:System.Security.Principal.WindowsImpersonationContext>類別，並初始化與<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType>初始化的類別，如下列程式碼所示的方法。</span><span class="sxs-lookup"><span data-stu-id="6277b-116">Begin impersonation by creating a new instance of the <xref:System.Security.Principal.WindowsImpersonationContext> class and initializing it with the <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> method of the initialized class, as shown in the following code.</span></span>  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  <span data-ttu-id="6277b-117">當您不再需要模擬時，呼叫<xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType>方法來將模擬還原，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6277b-117">When you no longer need to impersonate, call the <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> method to revert the impersonation, as shown in the following code.</span></span>  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 <span data-ttu-id="6277b-118">如果信任的程式碼具有已經附加<xref:System.Security.Principal.WindowsPrincipal>物件的執行緒，您可以呼叫執行個體方法**Impersonate**，這不會取得帳戶權杖。</span><span class="sxs-lookup"><span data-stu-id="6277b-118">If trusted code has already attached a <xref:System.Security.Principal.WindowsPrincipal> object to the thread, you can call the instance method **Impersonate**, which does not take an account token.</span></span> <span data-ttu-id="6277b-119">請注意，這只適用於執行緒上的 **WindowsPrincipal** 物件代表非處理序目前執行所使用之使用者身分的使用者。</span><span class="sxs-lookup"><span data-stu-id="6277b-119">Note that this is only useful when the **WindowsPrincipal** object on the thread represents a user other than the one under which the process is currently executing.</span></span> <span data-ttu-id="6277b-120">比方說，您可能會在使用 ASP.NET 並開啟 Windows 驗證、關閉模擬時遇到這種情況。</span><span class="sxs-lookup"><span data-stu-id="6277b-120">For example, you might encounter this situation using ASP.NET with Windows authentication turned on and impersonation turned off.</span></span> <span data-ttu-id="6277b-121">在此情況下，處理序會以網際網路資訊服務 (IIS) 中設定的帳戶身分執行，同時主體代表正在存取網頁的 Windows 使用者。</span><span class="sxs-lookup"><span data-stu-id="6277b-121">In this case, the process is running under an account configured in Internet Information Services (IIS) while the current principal represents the Windows user that is accessing the page.</span></span>  
  
 <span data-ttu-id="6277b-122">請注意，都**Impersonate**也不**復原**變更**主體**物件 (<xref:System.Security.Principal.IPrincipal>) 與目前呼叫內容相關聯。</span><span class="sxs-lookup"><span data-stu-id="6277b-122">Note that neither **Impersonate** nor **Undo** changes the **Principal** object (<xref:System.Security.Principal.IPrincipal>)  associated with the current call context.</span></span> <span data-ttu-id="6277b-123">相反地，模擬和還原會變更與目前作業系統處理序相關聯的權杖。</span><span class="sxs-lookup"><span data-stu-id="6277b-123">Rather, impersonation and reverting change the token associated with the current operating system process..</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6277b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6277b-124">See also</span></span>

- <xref:System.Security.Principal.WindowsIdentity>  
- <xref:System.Security.Principal.WindowsImpersonationContext>  
- [<span data-ttu-id="6277b-125">Principal 和 Identity 物件</span><span class="sxs-lookup"><span data-stu-id="6277b-125">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)  
- [<span data-ttu-id="6277b-126">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="6277b-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
