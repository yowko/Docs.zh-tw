---
title: 存取控制機制
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 9ebd1489c35bb3b023ed73cd86fac1b6a352012b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882177"
---
# <a name="access-control-mechanisms"></a>存取控制機制
您可以控制數種方式與 Windows Communication Foundation (WCF) 的存取。 本主題將扼要討論各種機制，並提供每一種機制的建議使用時機，本主題目的在於協助您選擇使用正確的機制。 下面將依複雜性的順序列出存取技術。 最簡單的是 <xref:System.Security.Permissions.PrincipalPermissionAttribute>，最複雜的則是「身分識別模型」。  
  
 除了這些機制中，模擬與委派搭配 WCF 述[委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)。  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 是用來限制對於服務方法的存取。 當屬性套用至方法時，它可用來要求特定呼叫者身分識別或 Windows 群組或 ASP.NET 角色的成員資格。 如果是使用 X.509 憑證進行驗證，用戶端便會獲得由主體名稱加憑證指紋所組成的主要身分識別。  
  
 請用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 控制服務執行所在電腦上資源的存取，如果服務的使用者永遠屬於服務執行所在之相同 Windows 網域，也用此種做法。 您可以輕易建立具有指定之存取層級 (例如無、唯讀或讀取和寫入) 的 Windows 群組。  
  
 如需使用屬性的詳細資訊，請參閱[How to:以 PrincipalPermissionAttribute 類別限制存取](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)。 如需身分識別的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## <a name="aspnet-membership-provider"></a>ASP.NET 成員資格提供者  
 ASP.NET 的功能是成員資格提供者。 儘管從技術角度來說，成員資格提供者並不屬於存取控制機制，但其可透過限制能夠存取服務端點的一組可能識別來控制對於服務的存取。 成員資格功能包括可以填入 (Populate) 使用者名稱/密碼組合的資料庫，而該名稱/密碼組合可讓網站的使用者配合該網站來建立帳戶。 為了存取使用成員資格提供者的服務，使用者必須以自己的使用者名稱和密碼登入。  
  
> [!NOTE]
>  您必須先填入之前的 WCF 服務可以將它用於授權用途，使用 ASP.NET 功能的資料庫。  
  
 如果您已經從現有的 ASP.NET 網站上取得的成員資格資料庫，而且您想要讓相同的使用者使用您的服務，授與相同的使用者名稱和密碼，您也可以使用成員資格功能。  
  
 如需使用 WCF 服務中的成員資格功能的詳細資訊，請參閱[How to:使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)。  
  
## <a name="aspnet-role-provider"></a>ASP.NET 角色提供者  
 ASP.NET 的另一個功能是能夠使用角色管理授權。 ASP.NET 角色提供者可讓開發人員建立使用者角色，並將每個使用者指派給角色或角色。 如同成員資格提供者的角色和指派會儲存在資料庫中，並可以使用 ASP.NET 角色提供者的特定實作所提供的工具中填入。 做為成員資格功能，使用 WCF 開發人員可以使用資訊在資料庫中來授權服務使用者角色。 例如，他們可以結合使用角色提供者與前述的 `PrincipalPermissionAttribute` 存取控制機制。  
  
 如果您有現有的 ASP.NET 角色提供者資料庫，而且想要在您的 WCF 服務使用相同的規則和使用者的指派，您也可以使用 ASP.NET 角色提供者。  
  
 如需使用角色提供者功能的詳細資訊，請參閱[How to:使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。  
  
## <a name="authorization-manager"></a>授權管理員  
 另一項功能會結合授權管理員 (AzMan) 與 ASP.NET 角色提供者來授權用戶端。 當 ASP.NET 裝載的 Web 服務時，AzMan 可以整合到應用程式，以便授權給服務透過 AzMan 完成。 ASP.NET 角色管理員提供的 API 可讓您管理應用程式角色新增和移除角色的使用者，以及檢查角色成員資格，但它不允許您查詢使用者是否被授權來執行具名的工作或作業。 AzMan 可讓您定義個別的作業，並將它們結合於工作中。 使用 AZMan 時，除了角色檢查以外，您也可以檢查使用者是否能夠執行某項工作。 角色指派和工作授權可以設定在應用程式外部，或是以程式設計方式執行於應用程式內部。 AzMan 管理 Microsoft 管理主控台 (MMC) 嵌入式管理單元可讓系統管理員能夠變更角色可在執行階段執行的工作，以及管理每位使用者的角色成員資格。  
  
 如果您已經可以存取現有的 AzMan 安裝，而且想要授權服務使用者使用 AzMan/角色提供者組合的功能，您可以也使用 AzMan 和 ASP.NET 角色提供者。  
  
 如需 AzMan 和 ASP.NET 角色提供者的詳細資訊，請參閱[How To:使用 ASP.NET 2.0 使用授權管理員 (AzMan)](https://go.microsoft.com/fwlink/?LinkId=88951)。 如需 WCF 服務使用 AzMan 和角色提供者的詳細資訊，請參閱[How to:使用 ASP.NET 授權管理員角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)。  
  
## <a name="identity-model"></a>識別模型  
 身分識別模型是一組 API，這組 API 可讓您管理宣告和原則來授權用戶端。 使用身分識別模型時，您可以檢查呼叫者向服務驗證本身時所使用認證中所包含的每一個宣告、比較宣告與服務的原則集，並根據比較結果來授與或拒絕存取權。  
  
 如果您需要精密控制能力，以及在授與存取權之前設定特定準則的能力，請使用身分識別模型。 例如，當使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 時，準則只是已通過驗證且屬於特定角色之使用者的身分識別。 相較之下，若是使用身分識別模型，您就可以建立原則，表示使用者必須超過 18 歲並擁有有效的駕照，才允許該使用者檢視某份文件。  
  
 有一個可以充分發揮身分識別模型宣告架構存取控制的範例，就是在發行權杖情節中使用同盟認證的情況下。 如需有關同盟與發行的權杖的詳細資訊，請參閱[聯合與發行權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
 如需身分識別模型的詳細資訊，請參閱[管理宣告與授權身分識別模型](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [如何：以 PrincipalPermissionAttribute 類別限制存取](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [如何：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [如何：使用 ASP.NET 授權管理員角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
