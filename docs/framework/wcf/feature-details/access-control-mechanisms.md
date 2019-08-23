---
title: 存取控制機制
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 14f348300d8ab9276a86b4cf8d91823d39b9aba3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964991"
---
# <a name="access-control-mechanisms"></a>存取控制機制
您可以使用 Windows Communication Foundation (WCF) 以數種方式來控制存取。 本主題將扼要討論各種機制，並提供每一種機制的建議使用時機，本主題目的在於協助您選擇使用正確的機制。 下面將依複雜性的順序列出存取技術。 最簡單的是 <xref:System.Security.Permissions.PrincipalPermissionAttribute>，最複雜的則是「身分識別模型」。  
  
 除了這些機制以外, 使用 WCF 的模擬和委派也會在[委派和](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)模擬中說明。  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 是用來限制對於服務方法的存取。 當屬性套用至方法時, 可以用來要求特定呼叫者的身分識別, 或 Windows 群組或 ASP.NET 角色中的成員資格。 如果是使用 X.509 憑證進行驗證，用戶端便會獲得由主體名稱加憑證指紋所組成的主要身分識別。  
  
 請用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 控制服務執行所在電腦上資源的存取，如果服務的使用者永遠屬於服務執行所在之相同 Windows 網域，也用此種做法。 您可以輕易建立具有指定之存取層級 (例如無、唯讀或讀取和寫入) 的 Windows 群組。  
  
 如需使用屬性的詳細資訊, 請[參閱如何:使用 PrincipalPermissionAttribute 類別](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)來限制存取。 如需有關身分識別的詳細資訊, 請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## <a name="aspnet-membership-provider"></a>ASP.NET 成員資格提供者  
 ASP.NET 的一項功能是成員資格提供者。 儘管從技術角度來說，成員資格提供者並不屬於存取控制機制，但其可透過限制能夠存取服務端點的一組可能識別來控制對於服務的存取。 成員資格功能包括可以填入 (Populate) 使用者名稱/密碼組合的資料庫，而該名稱/密碼組合可讓網站的使用者配合該網站來建立帳戶。 為了存取使用成員資格提供者的服務，使用者必須以自己的使用者名稱和密碼登入。  
  
> [!NOTE]
> 您必須先使用 ASP.NET 功能填入資料庫, WCF 服務才能將它用於授權用途。  
  
 如果您已經有現有 ASP.NET 網站的成員資格資料庫, 而且您想要讓相同的使用者使用您的服務, 並以相同的使用者名稱和密碼進行授權, 您也可以使用成員資格功能。  
  
 如需在 WCF 服務中使用成員資格功能的詳細資訊, [請參閱如何:使用 ASP.NET 成員資格提供](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)者。  
  
## <a name="aspnet-role-provider"></a>ASP.NET 角色提供者  
 ASP.NET 的另一項功能是使用角色管理授權的能力。 ASP.NET 角色提供者可讓開發人員為使用者建立角色, 並將每個使用者指派給角色或角色。 和成員資格提供者一樣, 角色和指派會儲存在資料庫中, 而且可以使用 ASP.NET 角色提供者的特定執行所提供的工具填入。 如同成員資格功能, WCF 開發人員可以使用資料庫中的資訊, 依據角色來授權服務使用者。 例如，他們可以結合使用角色提供者與前述的 `PrincipalPermissionAttribute` 存取控制機制。  
  
 如果您有現有的 ASP.NET 角色提供者資料庫, 而且想要在您的 WCF 服務中使用同一組規則和使用者指派, 您也可以使用 ASP.NET 角色提供者。  
  
 如需有關使用角色提供者功能的詳細資訊[, 請參閱如何:搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)使用 ASP.NET 角色提供者。  
  
## <a name="authorization-manager"></a>授權管理員  
 另一個功能是將授權管理員 (AzMan) 與 ASP.NET 角色提供者結合, 以授權用戶端。 當 ASP.NET 裝載 Web 服務時, AzMan 可以整合到應用程式中, 以便透過 AzMan 來進行服務的授權。 ASP.NET 角色管理員所提供的 API 可讓您管理應用程式角色、從角色新增和移除使用者, 以及檢查角色成員資格, 但不允許您查詢使用者是否已獲授權執行已命名的工作或操作。 AzMan 可讓您定義個別的作業，並將它們結合於工作中。 使用 AZMan 時，除了角色檢查以外，您也可以檢查使用者是否能夠執行某項工作。 角色指派和工作授權可以設定在應用程式外部，或是以程式設計方式執行於應用程式內部。 AzMan 管理 Microsoft 管理主控台 (MMC) 嵌入式管理單元可讓系統管理員能夠變更角色可在執行階段執行的工作，以及管理每位使用者的角色成員資格。  
  
 如果您已經擁有現有 AzMan 安裝的存取權, 而且想要使用 AzMan/角色提供者組合的功能來授權服務使用者, 您也可以使用 AzMan 和 ASP.NET 角色提供者。  
  
 如需 AzMan 和 ASP.NET 角色提供者的詳細資訊, [請參閱如何:搭配 ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=88951)使用授權管理員 (AzMan)。 如需使用 AzMan 和 WCF 服務之角色提供者的詳細資訊, [請參閱如何:搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)使用 ASP.NET 許可證管理員角色提供者。  
  
## <a name="identity-model"></a>識別模型  
 身分識別模型是一組 API，這組 API 可讓您管理宣告和原則來授權用戶端。 使用身分識別模型時，您可以檢查呼叫者向服務驗證本身時所使用認證中所包含的每一個宣告、比較宣告與服務的原則集，並根據比較結果來授與或拒絕存取權。  
  
 如果您需要精密控制能力，以及在授與存取權之前設定特定準則的能力，請使用身分識別模型。 例如，當使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 時，準則只是已通過驗證且屬於特定角色之使用者的身分識別。 相較之下，若是使用身分識別模型，您就可以建立原則，表示使用者必須超過 18 歲並擁有有效的駕照，才允許該使用者檢視某份文件。  
  
 有一個可以充分發揮身分識別模型宣告架構存取控制的範例，就是在發行權杖情節中使用同盟認證的情況下。 如需同盟和已發行權杖的詳細資訊, 請參閱[同盟和發行的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
 如需有關身分識別模型的詳細資訊, 請參閱[使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [如何：使用 PrincipalPermissionAttribute 類別來限制存取](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [如何：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [如何：搭配服務使用 ASP.NET 許可證管理員角色提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
