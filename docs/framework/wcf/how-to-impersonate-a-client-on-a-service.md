---
title: "HOW TO：在服務上模擬用戶端"
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
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c868e2b31fa15d0f0c9228828beba03666d5591
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>HOW TO：在服務上模擬用戶端
模擬 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務上的用戶端使服務可以代表用戶端執行動作。 關於存取控制清單 (ACL) 檢查的動作，例如存取機器上的目錄和檔案或存取 SQL Server 資料庫，請根據用戶端使用者帳戶檢查 ACL。 本主題說明在 Windows 網域中啟用用戶端以設定用戶端模擬等級所需的基本步驟。 如需此文件的實用範例，請參閱 [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md)。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]用戶端模擬，請參閱[委派和模擬](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)。  
  
> [!NOTE]
>  用戶端和服務在相同電腦上執行，且用戶端在系統帳戶下執行時 (也就是 `Local System` 或 `Network Service`)，以可設定狀態的安全性內容權杖建立安全的工作階段時無法模擬用戶端。 WinForms 或主控台應用程式通常在目前登入的帳戶下執行，因此根據預設值可以模擬該帳戶。 但當用戶端是 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 頁面，而且該頁面是裝載於 [!INCLUDE[iis601](../../../includes/iis601-md.md)] 或 IIS 7.0中時，根據預設，用戶端不會以 `Network Service` 帳戶執行。 所有支援安全工作階段的系統提供繫結預設為使用沒有狀態的安全性內容權杖。 不過，如果用戶端是 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 頁面，而且已使用含有可設定狀態之安全性內容權杖的安全工作階段，就無法模擬該用戶端。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]在安全工作階段中使用具狀態之安全性內容權杖，請參閱[How to： 建立安全工作階段的安全性內容權杖](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>若要從服務上的快取 Windows 權杖啟用用戶端模擬  
  
1.  建立服務。 如需此基本程序的教學課程，請參閱 [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md)。  
  
2.  使用運用 Windows 驗證並建立工作階段的繫結，例如 <xref:System.ServiceModel.NetTcpBinding> 或 <xref:System.ServiceModel.WSHttpBinding>。  
  
3.  建立服務的介面實作時，將 <xref:System.ServiceModel.OperationBehaviorAttribute> 類別套用至需要用戶端模擬的方法。 將 <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 屬性設定為 <xref:System.ServiceModel.ImpersonationOption.Required>。  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>若要設定用戶端上的允許模擬等級  
  
1.  使用 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立服務用戶端程式碼。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][使用 WCF 用戶端存取服務](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)。  
  
2.  建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端後，將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 類別的 <xref:System.ServiceModel.Security.WindowsClientCredential> 屬性設定成為其中一個 <xref:System.Security.Principal.TokenImpersonationLevel> 列舉值。  
  
    > [!NOTE]
    >  若要使用 <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>，必須使用交涉的 Kerberos 驗證 (有時稱為 *multi-leg* 或 *multi-step* Kerberos)。 如需如何實作此的說明，請參閱[安全性的最佳做法](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)。  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [模擬用戶端](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [委派和模擬](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
