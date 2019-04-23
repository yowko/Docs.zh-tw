---
title: HOW TO：使用 PrincipalPermissionAttribute 類別來限制存取
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: ae2aa4c5629096ee7d888e7c4e334c3b6696db3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323313"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>HOW TO：使用 PrincipalPermissionAttribute 類別來限制存取
控制 Windows 網域電腦上資源的存取，是基本的安全性工作。 例如，只有特定使用者能夠檢視機密資料 (如薪資資料)。 本主題說明如何透過將使用者歸屬到預先定義的群組，以限制方法的存取。 如需實用範例，請參閱 <<c0> [ 授權存取服務作業](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)。  
  
 這項工作包含兩個不同的程序。 第一個程序是建立群組並填入使用者。 第二個程序是套用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別以指定群組。  
  
### <a name="to-create-a-windows-group"></a>建立 Windows 群組  
  
1. 開啟**電腦管理**主控台。  
  
2. 在左窗格中，按一下**本機使用者和群組**。  
  
3. 以滑鼠右鍵按一下**群組**，然後按一下**新增群組**。  
  
4. 在 **群組名稱**方塊中，輸入新群組的名稱。  
  
5. 在 **描述**方塊中，輸入新群組的描述。  
  
6. 按一下 [**新增**] 按鈕，將新成員新增至群組。  
  
7. 如果您將自己加入群組中，而且想要測試以下程式碼，則必須先登出電腦然後再登入，才能包含在該群組中。  
  
### <a name="to-demand-user-membership"></a>要求使用者成員資格  
  
1. 開啟 Windows Communication Foundation (WCF) 程式碼檔案，其中包含實作的服務合約程式碼。 如需有關如何實作合約的詳細資訊，請參閱 < [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)。  
  
2. 將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性 (Attribute) 套用至每一個必須限於特定群組的方法。 將 <xref:System.Security.Permissions.SecurityAttribute.Action%2A> 屬性設為 <xref:System.Security.Permissions.SecurityAction.Demand>，並將 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> 屬性設為群組名稱。 例如:   
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  如果您將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 屬性套用至合約，則會擲回 <xref:System.Security.SecurityException>。 您只能在方法層級套用此屬性。  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>使用憑證控制方法的存取  
 如果用戶端認證類型為憑證，您也可以使用 `PrincipalPermissionAttribute` 類別控制方法的存取。 若要執行這項操作，您必須擁有憑證的主體和指紋。  
  
 若要檢查其屬性的憑證，請參閱[How to:使用 MMC 嵌入式管理單元檢視憑證](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。 若要尋找憑證指紋值，請參閱[How to:擷取憑證的指紋](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。  
  
#### <a name="to-control-access-using-a-certificate"></a>使用憑證控制存取  
  
1. 將 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 類別套用至您要限制存取的方法。  
  
2. 將屬性 (Attribute) 的動作設為 <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>。  
  
3. 將 `Name` 屬性設為字串，包含主體名稱和憑證的指紋。 使用分號和空格分隔這兩個值，如以下範例所示：  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. 將 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 屬性設為 <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>，如以下組態範例所示：  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     將這個值設為 `UseAspNetRoles`，表示 `Name` 的 `PrincipalPermissionAttribute` 屬性將用來執行字串比較。 做為用戶端認證使用憑證時，預設 WCF 串連憑證一般名稱，並使用分號來建立用戶端的主要身分識別的唯一值的指紋。 將服務上的 `UseAspNetRoles` 設為 `PrincipalPermissionMode` 之後，這個主要身分識別值會與 `Name` 屬性值比較，以判斷使用者的存取權限。  
  
     或者，當建立自我裝載服務時，依照以下程式碼所示，設定程式碼中的 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> 屬性：  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [授權存取服務作業](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [安全性概觀](../../../docs/framework/wcf/feature-details/security-overview.md)
- [履行服務合約](../../../docs/framework/wcf/implementing-service-contracts.md)
