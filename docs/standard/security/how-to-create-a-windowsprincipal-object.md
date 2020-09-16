---
title: 作法：建立 WindowsPrincipal 物件
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: 6cf7153250d2574783515ea53cf99709499d36f9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556202"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="f5a67-102">作法：建立 WindowsPrincipal 物件</span><span class="sxs-lookup"><span data-stu-id="f5a67-102">How to: Create a WindowsPrincipal Object</span></span>

> [!NOTE]
> <span data-ttu-id="f5a67-103">本文適用于 Windows。</span><span class="sxs-lookup"><span data-stu-id="f5a67-103">This article applies to Windows.</span></span>
>
> <span data-ttu-id="f5a67-104">如需 ASP.NET Core 的詳細資訊，請參閱 [ASP.NET Core 安全性](/aspnet/core/security/)。</span><span class="sxs-lookup"><span data-stu-id="f5a67-104">For information about ASP.NET Core, see [ASP.NET Core Security](/aspnet/core/security/).</span></span>

<span data-ttu-id="f5a67-105">有兩種方式來建立 <xref:System.Security.Principal.WindowsPrincipal> 物件，視程式碼是否必須重複執行以角色為基礎的驗證，還是它只必須執行一次而定。</span><span class="sxs-lookup"><span data-stu-id="f5a67-105">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
<span data-ttu-id="f5a67-106">如果程式碼必須重複執行以角色為基礎的驗證，下列程序的第一個會產生較少負荷。</span><span class="sxs-lookup"><span data-stu-id="f5a67-106">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="f5a67-107">程式碼只需要進行一次以角色為基礎的驗證時，您可以使用下列程序的第二個來建立 <xref:System.Security.Principal.WindowsPrincipal> 物件。</span><span class="sxs-lookup"><span data-stu-id="f5a67-107">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="f5a67-108">建立 WindowsPrincipal 物件以進行重複驗證</span><span class="sxs-lookup"><span data-stu-id="f5a67-108">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1. <span data-ttu-id="f5a67-109">對由靜態 <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> 屬性傳回的 <xref:System.AppDomain> 物件呼叫 <xref:System.AppDomain.SetPrincipalPolicy%2A> 方法，並傳遞 <xref:System.Security.Principal.PrincipalPolicy> 列舉值給方法，指出新的原則應該是什麼。</span><span class="sxs-lookup"><span data-stu-id="f5a67-109">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="f5a67-110">支援的值為 <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>、<xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> 和 <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>。</span><span class="sxs-lookup"><span data-stu-id="f5a67-110">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="f5a67-111">下列程式碼可示範這項方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="f5a67-111">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. <span data-ttu-id="f5a67-112">設定原則後，請使用靜態 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性來擷取封裝目前 Windows 使用者的主體。</span><span class="sxs-lookup"><span data-stu-id="f5a67-112">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="f5a67-113">由於屬性傳回型別是 <xref:System.Security.Principal.IPrincipal>，您必須將結果轉換為 <xref:System.Security.Principal.WindowsPrincipal> 類型。</span><span class="sxs-lookup"><span data-stu-id="f5a67-113">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="f5a67-114">下列程式碼會將新的 <xref:System.Security.Principal.WindowsPrincipal> 物件初始化為與目前執行緒相關聯之主體的值。</span><span class="sxs-lookup"><span data-stu-id="f5a67-114">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. <span data-ttu-id="f5a67-115">建立主體物件之後，您可以數種方法的其中一種來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f5a67-115">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="f5a67-116">建立 WindowsPrincipal 物件以進行單一驗證</span><span class="sxs-lookup"><span data-stu-id="f5a67-116">To create a WindowsPrincipal object for a single validation</span></span>  
  
1. <span data-ttu-id="f5a67-117">藉由呼叫靜態 <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> 方法初始化新的 <xref:System.Security.Principal.WindowsIdentity> 物件，此方法會查詢目前的 Windows 帳戶，將該帳戶的相關資訊放入新建立的身分識別物件。</span><span class="sxs-lookup"><span data-stu-id="f5a67-117">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="f5a67-118">下列程式碼會建立新的 <xref:System.Security.Principal.WindowsIdentity> 物件，並將其初始化為目前已驗證的使用者。</span><span class="sxs-lookup"><span data-stu-id="f5a67-118">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. <span data-ttu-id="f5a67-119">建立新的 <xref:System.Security.Principal.WindowsPrincipal> 物件，並傳遞在上一個步驟中建立之 <xref:System.Security.Principal.WindowsIdentity> 物件的值給它。</span><span class="sxs-lookup"><span data-stu-id="f5a67-119">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. <span data-ttu-id="f5a67-120">建立主體物件之後，您可以數種方法的其中一種來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f5a67-120">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a67-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5a67-121">See also</span></span>

- [<span data-ttu-id="f5a67-122">Principal 和 Identity 物件</span><span class="sxs-lookup"><span data-stu-id="f5a67-122">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
- [<span data-ttu-id="f5a67-123">ASP.NET Core 安全性</span><span class="sxs-lookup"><span data-stu-id="f5a67-123">ASP.NET Core Security</span></span>](/aspnet/core/security/)
