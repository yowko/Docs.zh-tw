---
title: 保護 WCF Data Services 的安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- securing application [WCF Data Services]
- WCF Data Services, security
ms.assetid: 99fc2baa-a040-4549-bc4d-f683d60298af
ms.openlocfilehash: e09007e786772e838a9aaa76eb8ef7a3fe2b7cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174650"
---
# <a name="securing-wcf-data-services"></a>保護 WCF Data Services 的安全
本主題介紹特定于開發、部署和運行 WCF 資料服務和訪問支援開放資料協定 （OData） 的服務的應用程式的安全注意事項。 您還應遵循有關創建安全 .NET 框架應用程式的建議。  
  
在規劃如何保護基於 WCF 資料服務的 OData 服務時，必須同時解決身份驗證、發現和驗證主體身份的過程以及授權，以確定經過身份驗證的委託人是否允許訪問請求的資源。 您也應該考慮是否要使用 SSL 加密訊息。  
  
## <a name="authenticating-client-requests"></a>驗證用戶端要求  
WCF 資料服務不實現自己的任何類型的身份驗證，而是依賴于資料服務主機的身份驗證規定。 這意味著服務假定它收到的任何請求已由網路主機進行身份驗證，並且主機已通過 WCF 資料服務提供的介面正確標識了請求的原則。 這些身份驗證選項和方法在多部分[OData 和身份驗證系列中](https://devblogs.microsoft.com/odata/?s=%22OData+and+authentication%22)進行了詳細說明。  
  
### <a name="authentication-options-for-a-wcf-data-service"></a>用於 WCF Data Service 的驗證選項  
 下表列出了一些驗證機制，可協助您驗證 WCF Data Service 的要求。  
  
|驗證選項|描述|  
|----------------------------|-----------------|  
|匿名驗證|啟用 HTTP 匿名驗證時，任何原則都可以連線至資料服務。 匿名存取不需要認證。 只有在您想要允許任何人存取資料服務時，才使用此選項。|  
|基本和摘要式驗證|驗證需要使用者名稱和密碼所組成的認證。 支援非 Windows 用戶端的驗證。 **安全記事：** 基本驗證憑據（使用者名和密碼）以明明的方式發送，可以截獲。 摘要式驗證會根據所提供的認證傳送雜湊，這讓它比基本驗證更安全。 兩者都很容易受到攔截式攻擊。 使用這些驗證方法時，您應該考慮使用安全通訊端層 (SSL)，加密用戶端與資料服務之間的通訊。 <br /><br /> Microsoft 互聯網資訊服務 （IIS） 為ASP.NET應用程式中的 HTTP 要求提供了基本驗證和摘要身份驗證的實現。 這個 Windows 驗證提供者實作可讓 .NET Framework 用戶端應用程式將要求之 HTTP 標頭中的認證提供給資料服務，以便密切地交涉 Windows 使用者的驗證。 有關詳細資訊，請參閱[摘要身份驗證技術參考](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782794(v=ws.10))。<br /><br /> 當希望資料服務使用基於某些自訂身份驗證服務而不是 Windows 憑據的基本驗證時，必須實現自訂ADP.NET HTTP 模組進行身份驗證。<br /><br /> 有關如何將自訂基本驗證方案與 WCF 資料服務一起使用的示例，請參閱博客文章[OData 和身份驗證 + 第 6 部分 = 自訂基本驗證](https://devblogs.microsoft.com/odata/odata-and-authentication-part-6-custom-basic-authentication/)。|  
|Windows 驗證|Windows 型認證是使用 NTLM 或 Kerberos 交換。 此機制比基本或摘要式驗證更安全，但它需要用戶端是 Windows 架構的應用程式。 IIS 還為ASP.NET應用程式中的 HTTP 要求提供了 Windows 身份驗證的實現。 有關詳細資訊，請參閱[ASP.NET表單身份驗證概述](https://docs.microsoft.com/previous-versions/aspnet/7t6b43z4(v=vs.100))。<br /><br /> 有關如何將 Windows 身份驗證與 WCF 資料服務一起使用的示例，請參閱博客文章[OData 和身份驗證 + 第 2 部分 + Windows 身份驗證](https://devblogs.microsoft.com/odata/odata-and-authentication-part-2-windows-authentication/)。|  
|ASP.NET表單身份驗證|表單驗證可讓您使用自己的程式碼來驗證使用者，然後在 Cookie 或網頁 URL 中維護驗證語彙基元 (Token)。 您可以使用您所建立的登入表單驗證使用者的使用者名稱和密碼。 未經驗證的要求會重新導向至登入頁面，使用者可在此處提供認證和送出表單。 如果應用程式驗證了要求，則系統會發出包含金鑰的票證，用於重新建立後續要求的身分識別。 有關詳細資訊，請參閱[表單身份檢查器提供者](https://docs.microsoft.com/previous-versions/aspnet/9wff0kyh(v=vs.100))。 **安全記事：** 預設情況下，在 ASP.NET Web 應用程式中使用表單身份驗證時，包含表單身份驗證票證的 Cookie 不受保護。 您應該考慮要求 SSL 同時保護驗證票證和初始登入認證。 <br /><br /> 有關如何將表單身份驗證與 WCF 資料服務一起使用的示例，請參閱博客文章[OData 和身份驗證 – 第 7 部分 = 表單身份驗證](https://devblogs.microsoft.com/odata/odata-and-authentication-part-7-forms-authentication/)。|  
|宣告架構驗證|在基於聲明的身份驗證中，資料服務依賴于受信任的"協力廠商"標識提供程式服務來對使用者進行身份驗證。 身分識別提供者會明確地驗證要求資料服務資源之存取權的使用者，並發出授與要求資源之存取權的語彙基元。 接著，系統會向資料服務呈現此權杖，然後根據與發出存取權杖之身分識別服務的信任關係，授與存取權給使用者。<br /><br /> 使用宣告架構驗證提供者的優點是，它們可以跨信任網域，用來驗證各種不同類型的用戶端。 資料服務可以採用此種協力廠商提供者，來卸載維護和驗證使用者的需求。 OAuth 2.0 是 Microsoft Azure AppFabric 存取控制所支援的宣告架構驗證通訊協定，以服務的方式用於聯盟授權。 此通訊協定支援 REST 型服務。 有關如何將 OAuth 2.0 與 WCF 資料服務一起使用的示例，請參閱博客文章[OData 和身份驗證 – 第 8 部分 • OAuth WRAP](https://devblogs.microsoft.com/odata/odata-and-authentication-part-8-oauth-wrap/)。|  
  
<a name="clientAuthentication"></a>
### <a name="authentication-in-the-client-library"></a>用戶端程式庫中的驗證  
 預設情況下，WCF 資料服務用戶端庫在向 OData 服務發出請求時不提供憑據。 當資料服務需要登入認證來驗證使用者時，這些認證可以在從 <xref:System.Net.NetworkCredential> 之 <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> 屬性存取的 <xref:System.Data.Services.Client.DataServiceContext> 中提供，如以下範例所示：  
  
```csharp  
// Set the client authentication credentials.  
context.Credentials =  
    new NetworkCredential(userName, password, domain);  
```  
  
```vb  
' Set the client authentication credentials.  
context.Credentials = _  
    New NetworkCredential(userName, password, domain)  
```  
  
 有關詳細資訊，請參閱[：為數據服務請求指定用戶端憑據](specify-client-creds-for-a-data-service-request-wcf.md)。  
  
 當資料服務需要無法使用 <xref:System.Net.NetworkCredential> 物件指定的登入認證 (例如宣告架構語彙基元或 Cookie) 時，您必須在 HTTP 要求中手動設定標頭，這通常是 `Authorization` 和 `Cookie` 標頭。 有關此類身份驗證方案的詳細資訊，請參閱博客文章[OData 和身份驗證 – 第 3 部分 – 用戶端掛鉤](https://devblogs.microsoft.com/odata/odata-and-authentication-part-3-clientside-hooks/)。 有關如何在請求消息中設置 HTTP 標頭的示例，請參閱[如何：在用戶端請求中設置標頭](how-to-set-headers-in-the-client-request-wcf-data-services.md)。  
  
## <a name="impersonation"></a>模擬  
 一般而言，資料服務會使用裝載資料服務之背景工作處理序的認證來存取所需的資源，例如伺服器或資料庫上的檔案。 使用類比時，ASP.NET應用程式可以使用發出請求的使用者的 Windows 標識（使用者帳戶）執行。 模擬常用於依賴 IIS 驗證使用者，而且此原則的認證用來存取必要資源的應用程式。 有關詳細資訊，請參閱[ASP.NET類比](https://docs.microsoft.com/previous-versions/aspnet/xh507fc5(v=vs.100))。  
  
## <a name="configuring-data-service-authorization"></a>設定資料服務授權  
 授權是將應用程式資源的存取權授與根據先前成功驗證所識別的原則或過程。 一般的作法是，您應該只授與足夠的權限給資料服務的使用者來執行用戶端應用程式所需的作業。  
  
### <a name="restrict-access-to-data-service-resources"></a>限制資料服務資源的存取  
 預設情況下，WCF 資料服務使您能夠向能夠訪問資料服務的任何使用者授予針對資料服務資源（實體集和服務操作）的通用讀取和寫入存取權限。 定義讀取和寫入權限的規則可以針對資料服務所公開的每個實體，以及公開到任何服務作業的每個實體個別定義。 建議您同時將讀取和寫入權限僅限為用戶端應用程式所需的資源。 有關詳細資訊，請參閱[最低資源訪問要求](configuring-the-data-service-wcf-data-services.md#accessRequirements)。  
  
### <a name="implement-role-based-interceptors"></a>實作以角色為基礎的攔截器  
 攔截器可讓您在資料服務實際運作之前，攔截對資料服務資源的要求。 有關詳細資訊，請參閱[攔截器](interceptors-wcf-data-services.md)。 攔截器可讓您根據提出要求的已驗證使用者進行授權決策。 有關如何根據經過身份驗證的使用者標識限制對資料服務資源的訪問的示例，請參閱[如何：攔截資料服務消息](how-to-intercept-data-service-messages-wcf-data-services.md)。  
  
### <a name="restrict-access-to-the-persisted-data-store-and-local-resources"></a>限制已保存之資料存放區和本機資源的存取  
 用來存取已保存之存放區的帳戶應該僅被授與資料庫或檔案系統中的足夠權限來支援資料服務的需求。 使用匿名驗證時，這是用來執行裝載應用程式的帳戶。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](how-to-develop-a-wcf-data-service-running-on-iis.md)。 使用模擬時，必須將這些資源的存取權授與已驗證的使用者，通常是做為 Windows 群組的一部分。  
  
## <a name="other-security-considerations"></a>其他安全性考量  
  
### <a name="secure-the-data-in-the-payload"></a>保護裝載中資料的安全  
OData 基於 HTTP 協定。 在 HTTP 訊息中，根據資料服務實作的驗證，標頭可能包含寶貴的使用者認證。 訊息主體可能也包含必須受到保護的寶貴客戶資料。 在這兩種情況下，建議您使用 SSL 透過網路傳輸保護這項資訊。  
  
### <a name="ignored-message-headers-and-cookies"></a>已忽略的訊息標頭和 Cookie  
 資料服務會忽略，而且絕不會設定宣告內容類型與資源位置以外之標頭的 HTTP 要求標頭。  
  
 Cookie 可用作身份驗證方案的一部分，例如與ASP.NET表單身份驗證一起使用。 但是，WCF 資料服務會忽略在傳入請求上設置的任何 HTTP Cookie。 資料服務的主機可能會處理 Cookie，但 WCF 資料服務運行時從不分析或返回 Cookie。 WCF 資料服務用戶端庫也不會處理回應中發送的 Cookie。  
  
### <a name="custom-hosting-requirements"></a>自訂裝載需求  
 預設情況下，WCF 資料服務創建為 IIS 中託管ASP.NET應用程式。 這可讓資料服務運用此平台的安全行為。 您可以定義由自訂主機託管的 WCF 資料服務。 有關詳細資訊，請參閱[託管資料服務](hosting-the-data-service-wcf-data-services.md)。 裝載資料服務的元件和平台必須確定下列安全性行為，以防止資料服務的攻擊：  
  
- 限制所有可能作業之資料服務要求中接受的 URI 長度。  
  
- 限制傳入與傳出之 HTTP 訊息的大小。  
  
- 限制在任何指定時間的未完成要求總數。  
  
- 限制 HTTP 標頭的大小及其值，並提供 WCF 資料服務對標頭資料的訪問。  
  
- 偵測並還擊已知的攻擊，如 TCP SYN 和訊息重新執行攻擊。  
  
### <a name="values-are-not-further-encoded"></a>值不會進一步編碼  
 發送到資料服務的屬性值不會由 WCF 資料服務運行時進一步編碼。 例如，當實體的字串屬性包含 HTML 格式的內容時，資料服務不會以 HTML 編碼標記。 資料服務也不會進一步編碼回應中的屬性值。 用戶端程式庫也不會執行任何額外的編碼。  
  
### <a name="considerations-for-client-applications"></a>用戶端應用程式的考量  
 以下安全注意事項適用于使用 WCF 資料服務用戶端存取 OData 服務的應用程式：  
  
- 用戶端程式庫假設用來存取資料服務的通訊協定會提供適當的安全性層級。  
  
- 用戶端程式庫會針對基礎平台提供之傳輸堆疊的逾時和剖析選項，使用所有預設值。  
  
- 用戶端程式庫不會從應用程式組態檔讀取任何設定。  
  
- 用戶端程式庫不會實作任何跨網域存取機制。 但是，它會依賴基礎 HTTP 堆疊所提供的機制。  
  
- 用戶端程式庫沒有使用者介面項目，因此，絕不會嘗試顯示或呈現它所接收或傳送的資料。  
  
- 建議用戶端應用程式一律驗證使用者輸入，以及接受自不受信任之服務的資料。  
  
## <a name="see-also"></a>另請參閱

- [定義 WCF 資料服務](defining-wcf-data-services.md)
- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
