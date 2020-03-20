---
title: 存取控制機制
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: b423dac4d8324069eb1825666419b23b5afdca63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185497"
---
# <a name="access-control-mechanisms"></a>存取控制機制
您可以使用 Windows 通信基礎 （WCF） 以多種方式控制訪問。 本主題將扼要討論各種機制，並提供每一種機制的建議使用時機，本主題目的在於協助您選擇使用正確的機制。 下面將依複雜性的順序列出存取技術。 最簡單的是 <xref:System.Security.Permissions.PrincipalPermissionAttribute>，最複雜的則是「身分識別模型」。  
  
 除了這些機制之外，在[委派和冒號](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)中還解釋了使用 WCF 進行類比和委派。  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 是用來限制對於服務方法的存取。 當該屬性應用於方法時，它可用於請求特定調用方在 Windows 組或ASP.NET角色中的標識或成員資格。 如果是使用 X.509 憑證進行驗證，用戶端便會獲得由主體名稱加憑證指紋所組成的主要身分識別。  
  
 請用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 控制服務執行所在電腦上資源的存取，如果服務的使用者永遠屬於服務執行所在之相同 Windows 網域，也用此種做法。 您可以輕易建立具有指定之存取層級 (例如無、唯讀或讀取和寫入) 的 Windows 群組。  
  
 有關使用 屬性的詳細資訊，請參閱[如何：使用主體許可權屬性類限制訪問](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)。 有關標識的詳細資訊，請參閱[服務標識和身份驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## <a name="aspnet-membership-provider"></a>ASP.NET 成員資格提供者  
 ASP.NET的一個功能是成員資格提供程式。 儘管從技術角度來說，成員資格提供者並不屬於存取控制機制，但其可透過限制能夠存取服務端點的一組可能識別來控制對於服務的存取。 成員資格功能包括可以填入 (Populate) 使用者名稱/密碼組合的資料庫，而該名稱/密碼組合可讓網站的使用者配合該網站來建立帳戶。 要訪問使用成員資格提供程式的服務，使用者必須使用其使用者名和密碼登錄。  
  
> [!NOTE]
> 必須先使用ASP.NET功能填充資料庫，然後 WCF 服務才能將其用於授權目的。  
  
 如果您已經從現有ASP.NET網站中已經擁有成員資格資料庫，並且希望使相同的使用者能夠使用具有相同使用者名和密碼的服務，也可以使用成員資格功能。  
  
 有關在 WCF 服務中使用成員資格功能的詳細資訊，請參閱[：使用ASP.NET成員資格提供程式](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)。  
  
## <a name="aspnet-role-provider"></a>ASP.NET 角色提供者  
 ASP.NET的另一個功能是使用角色管理授權的能力。 ASP.NET角色提供程式使開發人員能夠為使用者創建角色，並將每個使用者分配給角色或角色。 與成員資格提供程式一樣，角色和分配存儲在資料庫中，並且可以使用ASP.NET角色提供程式的特定實現提供的工具進行填充。 與成員資格功能一樣，WCF 開發人員可以使用資料庫中的資訊按角色授權服務使用者。 例如，他們可以結合使用角色提供者與前述的 `PrincipalPermissionAttribute` 存取控制機制。  
  
 如果您擁有現有的ASP.NET角色提供程式資料庫，並且希望在 WCF 服務中使用相同的規則和使用者分配集，也可以使用ASP.NET角色提供程式。  
  
 有關使用角色提供程式功能的詳細資訊，請參閱[如何：將ASP.NET角色提供程式與服務一起使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)。  
  
## <a name="authorization-manager"></a>授權管理員  
 另一個功能將授權管理員 （AzMan） 與ASP.NET角色提供程式合併以授權用戶端。 當ASP.NET託管 Web 服務時，AzMan 可以集成到應用程式中，以便通過 AzMan 完成對服務的授權。 ASP.NET角色管理器提供一個 API，使您能夠管理應用程式角色、從角色中添加和刪除使用者以及檢查角色成員身份，但它不允許您查詢使用者是否有權執行命名的任務或操作。 AzMan 可讓您定義個別的作業，並將它們結合於工作中。 使用 AZMan 時，除了角色檢查以外，您也可以檢查使用者是否能夠執行某項工作。 角色指派和工作授權可以設定在應用程式外部，或是以程式設計方式執行於應用程式內部。 AzMan 管理 Microsoft 管理主控台 (MMC) 嵌入式管理單元可讓系統管理員能夠變更角色可在執行階段執行的工作，以及管理每位使用者的角色成員資格。  
  
 如果您已經有權訪問現有的 AzMan 安裝，並且希望使用 AzMan/角色提供程式組合的功能授權服務使用者，也可以使用 AzMan 和 ASP.NET角色提供程式。  
  
 有關 AzMan 和ASP.NET角色提供程式的詳細資訊，請參閱[如何使用授權管理員 （AzMan） ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10))。 有關使用 AzMan 和 WCF 服務的角色提供程式的詳細資訊，請參閱[如何：將ASP.NET授權管理員角色提供程式與服務一起使用](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)。  
  
## <a name="identity-model"></a>識別模型  
 身分識別模型是一組 API，這組 API 可讓您管理宣告和原則來授權用戶端。 使用身分識別模型時，您可以檢查呼叫者向服務驗證本身時所使用認證中所包含的每一個宣告、比較宣告與服務的原則集，並根據比較結果來授與或拒絕存取權。  
  
 如果您需要精密控制能力，以及在授與存取權之前設定特定準則的能力，請使用身分識別模型。 例如，當使用 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 時，準則只是已通過驗證且屬於特定角色之使用者的身分識別。 相較之下，若是使用身分識別模型，您就可以建立原則，表示使用者必須超過 18 歲並擁有有效的駕照，才允許該使用者檢視某份文件。  
  
 有一個可以充分發揮身分識別模型宣告架構存取控制的範例，就是在發行權杖情節中使用同盟認證的情況下。 有關聯合和頒發的權杖的詳細資訊，請參閱[聯合和已頒發的權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
 有關標識模型的詳細資訊，請參閱[使用標識模型管理聲明和授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [如何：利用 PrincipalPermissionAttribute 類別限制存取](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [HOW TO：使用 ASP.NET 角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [如何：使用 ASP.NET 授權管理員角色提供者搭配服務](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [委派和模擬](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
