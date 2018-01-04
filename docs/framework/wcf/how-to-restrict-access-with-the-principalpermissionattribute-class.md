---
title: "HOW TO：使用 PrincipalPermissionAttribute 類別來限制存取"
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
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da91e3456fdca863980c89f45e0cc28db19170be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="ddc51-102">HOW TO：使用 PrincipalPermissionAttribute 類別來限制存取</span><span class="sxs-lookup"><span data-stu-id="ddc51-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>
<span data-ttu-id="ddc51-103">控制 Windows 網域電腦上資源的存取，是基本的安全性工作。</span><span class="sxs-lookup"><span data-stu-id="ddc51-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="ddc51-104">例如，只有特定使用者能夠檢視機密資料 (如薪資資料)。</span><span class="sxs-lookup"><span data-stu-id="ddc51-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="ddc51-105">本主題說明如何透過將使用者歸屬到預先定義的群組，以限制方法的存取。</span><span class="sxs-lookup"><span data-stu-id="ddc51-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="ddc51-106">如需實用範例，請參閱[授權存取服務作業](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc51-106">For a working sample, see [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="ddc51-107">這項工作包含兩個不同的程序。</span><span class="sxs-lookup"><span data-stu-id="ddc51-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="ddc51-108">第一個程序是建立群組並填入使用者。</span><span class="sxs-lookup"><span data-stu-id="ddc51-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="ddc51-109">第二個程序是套用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別以指定群組。</span><span class="sxs-lookup"><span data-stu-id="ddc51-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="ddc51-110">建立 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="ddc51-110">To create a Windows group</span></span>  
  
1.  <span data-ttu-id="ddc51-111">開啟**電腦管理**主控台。</span><span class="sxs-lookup"><span data-stu-id="ddc51-111">Open the **Computer Management** console.</span></span>  
  
2.  <span data-ttu-id="ddc51-112">在左面板中，按一下 **本機使用者和群組**。</span><span class="sxs-lookup"><span data-stu-id="ddc51-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3.  <span data-ttu-id="ddc51-113">以滑鼠右鍵按一下**群組**，然後按一下**新增群組**。</span><span class="sxs-lookup"><span data-stu-id="ddc51-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4.  <span data-ttu-id="ddc51-114">在**群組名稱**方塊中，輸入新群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="ddc51-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5.  <span data-ttu-id="ddc51-115">在**描述**方塊中，輸入新群組的描述。</span><span class="sxs-lookup"><span data-stu-id="ddc51-115">In the **Description** box, type a description of the new group.</span></span>  
  
6.  <span data-ttu-id="ddc51-116">按一下**新增** 按鈕，將新成員加入群組。</span><span class="sxs-lookup"><span data-stu-id="ddc51-116">Click the **Add** button to add new members to the group.</span></span>  
  
7.  <span data-ttu-id="ddc51-117">如果您將自己加入群組中，而且想要測試以下程式碼，則必須先登出電腦然後再登入，才能包含在該群組中。</span><span class="sxs-lookup"><span data-stu-id="ddc51-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="ddc51-118">要求使用者成員資格</span><span class="sxs-lookup"><span data-stu-id="ddc51-118">To demand user membership</span></span>  
  
1.  <span data-ttu-id="ddc51-119">開啟包含所實作之服務合約程式碼的 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="ddc51-119">Open the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] code file that contains the implemented service contract code.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ddc51-120">實作合約，請參閱[實作服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc51-120"> implementing a contract, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="ddc51-121">將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性 (Attribute) 套用至每一個必須限於特定群組的方法。</span><span class="sxs-lookup"><span data-stu-id="ddc51-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="ddc51-122">將 <xref:System.Security.Permissions.SecurityAttribute.Action%2A> 屬性設為 <xref:System.Security.Permissions.SecurityAction.Demand>，並將 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> 屬性設為群組名稱。</span><span class="sxs-lookup"><span data-stu-id="ddc51-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="ddc51-123">例如: </span><span class="sxs-lookup"><span data-stu-id="ddc51-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="ddc51-124">如果您將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性套用至合約，則會擲回 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="ddc51-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="ddc51-125">您只能在方法層級套用此屬性。</span><span class="sxs-lookup"><span data-stu-id="ddc51-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="ddc51-126">使用憑證控制方法的存取</span><span class="sxs-lookup"><span data-stu-id="ddc51-126">Using a Certificate to Control Access to a Method</span></span>  
 <span data-ttu-id="ddc51-127">如果用戶端認證類型為憑證，您也可以使用 `PrincipalPermissionAttribute` 類別控制方法的存取。</span><span class="sxs-lookup"><span data-stu-id="ddc51-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="ddc51-128">若要執行這項操作，您必須擁有憑證的主體和指紋。</span><span class="sxs-lookup"><span data-stu-id="ddc51-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="ddc51-129">若要檢查其屬性的憑證，請參閱[How to： 使用 MMC 嵌入式管理單元檢視憑證](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc51-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="ddc51-130">若要尋找的憑證指紋值，請參閱[How to： 擷取憑證的指紋](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="ddc51-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="ddc51-131">使用憑證控制存取</span><span class="sxs-lookup"><span data-stu-id="ddc51-131">To control access using a certificate</span></span>  
  
1.  <span data-ttu-id="ddc51-132">將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別套用至您要限制存取的方法。</span><span class="sxs-lookup"><span data-stu-id="ddc51-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2.  <span data-ttu-id="ddc51-133">將屬性 (Attribute) 的動作設為 <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ddc51-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3.  <span data-ttu-id="ddc51-134">將 `Name` 屬性設為字串，包含主體名稱和憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="ddc51-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="ddc51-135">使用分號和空格分隔這兩個值，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="ddc51-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  <span data-ttu-id="ddc51-136">將 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 屬性設為 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>，如以下組態範例所示：</span><span class="sxs-lookup"><span data-stu-id="ddc51-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="ddc51-137">將這個值設為 `UseAspNetRoles`，表示 `Name` 的 `PrincipalPermissionAttribute` 屬性將用來執行字串比較。</span><span class="sxs-lookup"><span data-stu-id="ddc51-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="ddc51-138">當憑證用來做為用戶端認證時，根據預設，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 會使用分號串連憑證一般名稱和指紋，以便為用戶端的主要身分識別建立唯一的值。</span><span class="sxs-lookup"><span data-stu-id="ddc51-138">When a certificate is used as a client credential, by default [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="ddc51-139">將服務上的 `UseAspNetRoles` 設為 `PrincipalPermissionMode` 之後，這個主要身分識別值會與 `Name` 屬性值比較，以判斷使用者的存取權限。</span><span class="sxs-lookup"><span data-stu-id="ddc51-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="ddc51-140">或者，當建立自我裝載服務時，依照以下程式碼所示，設定程式碼中的 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 屬性：</span><span class="sxs-lookup"><span data-stu-id="ddc51-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ddc51-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddc51-141">See Also</span></span>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 <xref:System.Security.Permissions.SecurityAction.Demand>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>  
 [<span data-ttu-id="ddc51-142">授權存取服務作業</span><span class="sxs-lookup"><span data-stu-id="ddc51-142">Authorizing Access to Service Operations</span></span>](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="ddc51-143">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="ddc51-143">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="ddc51-144">履行服務合約</span><span class="sxs-lookup"><span data-stu-id="ddc51-144">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
