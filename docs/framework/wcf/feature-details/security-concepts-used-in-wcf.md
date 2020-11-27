---
title: 用於 WCF 的安全性概念
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 2c7bc01ba45c02be4a1d40c2600fde62e94afe32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251382"
---
# <a name="security-concepts-used-in-wcf"></a>用於 WCF 的安全性概念

Windows Communication Foundation (WCF) 安全性是以已在使用中且部署于各種安全性基礎結構的概念為基礎。  
  
 WCF 支援某些基礎結構，例如安全通訊端層 (SSL) 透過 HTTP (HTTPS) 。 不過，WCF 藉由執行較新的互通安全性標準 (（例如透過 SOAP 編碼的訊息的 WS-Security) ），超越支援現有的安全性基礎結構。 不論是使用現有的機制或新的互通標準，兩者都是依據相同的安全性概念。 因此，若要實作應用程式的最佳安全性模型，最重要的是了解現有基礎結構與較新標準所依據的概念。  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web 服務安全性簡介  

Microsoft 模式和實務小組撰寫了稱為「 [WCF 安全性指南](https://archive.codeplex.com/?p=wcfsecurityguide)」的深入技術白皮書。 本白皮書將說明與 web 服務、關鍵 WCF 安全性概念、內部網路應用程式案例和網際網路應用程式案例相關的基本安全性概念。  
  
## <a name="industry-wide-security-specifications"></a>業界安全性規格  
  
### <a name="public-key-infrastructure"></a>公開金鑰基礎結構  

公開金鑰基礎結構 (PKI) 是數位憑證、憑證授權單位單位和其他註冊授權單位的系統，可透過公開金鑰加密的使用來驗證和驗證每一方的電子交易相關各方。
  
### <a name="kerberos-protocol"></a>Kerberos 通訊協定  

 *Kerberos 通訊協定* 是一種規格，可建立在 Windows 網域上驗證使用者的安全性機制。 它允許使用者在網域中使用其他實體建立安全內容。 Windows 2000 及以後版本平台根據預設會使用 Kerberos 通訊協定。 當建立將與內部網路用戶端進行互動的服務時，了解系統的機制會有所幫助。 此外，因為 Web 服務安全性的 *kerberos* 系結已廣泛發佈，所以您可以使用 kerberos 通訊協定與網際網路用戶端通訊， (也就是 kerberos 通訊協定可互通) 。 如需有關如何在 Windows 中執行 Kerberos 通訊協定的詳細資訊，請參閱  [Microsoft kerberos](/windows/win32/secauthn/microsoft-kerberos)。  
  
### <a name="x509-certificates"></a>X.509 憑證  

 X.509 憑證是在安全性應用程式中使用的主要認證形式。 如需 x.509 憑證的詳細資訊，請參閱 [X.509 公開金鑰憑證](/windows/win32/seccertenroll/about-x-509-public-key-certificates)。 X.509 憑證儲存在憑證存放區中。 執行 Windows 的電腦上有多種憑證存放區，每個存放區都有不同的用途。 如需不同存放區的詳細資訊，請參閱 [憑證存放區](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))。  
  
## <a name="web-services-security-specifications"></a>Web 服務安全性規格  

 系統定義的繫結支援許多常用的 Web 服務安全性規格。 如需系統提供之系結的完整清單，以及其支援的 web 服務規格，請參閱： [System-Provided 互通性系結所支援的 Web 服務通訊協定](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>存取控制機制  

 WCF 提供數種方法來控制服務或作業的存取權。 包括  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. ASP.NET 成員資格提供者  
  
3. ASP.NET 角色提供者  
  
4. 授權管理員  
  
5. 識別模型  
  
 如需這些主題的詳細資訊，請參閱 [存取控制機制](access-control-mechanisms.md)  
  
## <a name="see-also"></a>另請參閱

- [安全性概觀](security-overview.md)
- [Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))
