---
title: 用於 WCF 的安全性概念
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: ce6dc6f5cb8680d6228e21206afdc3aa33085e7d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938115"
---
# <a name="security-concepts-used-in-wcf"></a>用於 WCF 的安全性概念
Windows Communication Foundation （WCF）安全性是根據已在使用中且已部署在各種安全性基礎結構中的概念所建立。  
  
 WCF 支援其中一些基礎結構，例如安全通訊端層（SSL） over HTTP （HTTPS）。 不過，WCF 不支援現有的安全性基礎結構，而是透過 SOAP 編碼的訊息來執行較新的互通安全性標準（例如 WS-MANAGEMENT）。 不論是使用現有的機制或新的互通標準，兩者都是依據相同的安全性概念。 因此，若要實作應用程式的最佳安全性模型，最重要的是了解現有基礎結構與較新標準所依據的概念。  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web 服務安全性簡介  
 Microsoft 模式和實務小組已撰寫有關 WCF 安全性指引的深入白皮書，可從這裡下載： [Wcf 安全性指南](https://go.microsoft.com/fwlink/?LinkId=210210)。 本白皮書說明與 web 服務、主要 WCF 安全性概念、內部網路應用程式案例，以及網際網路應用程式案例相關的基本安全性概念。  
  
## <a name="industry-wide-security-specifications"></a>業界安全性規格  
  
### <a name="public-key-infrastructure"></a>公開金鑰基礎結構  
 公開金鑰基礎結構 (PKI) 是結合了數位憑證、憑證授權單位，與其他註冊授權單位，並以公開金鑰密碼編譯法來驗證參與電子異動之每一方的系統。 如需詳細資訊，請參閱[Windows Server 2008 R2 憑證服務](https://go.microsoft.com/fwlink/?LinkId=210211)。  
  
### <a name="kerberos-protocol"></a>Kerberos 通訊協定  
 *Kerberos 通訊協定*是用來建立安全性機制的規格，可驗證 Windows 網域上的使用者。 它允許使用者在網域中使用其他實體建立安全內容。 Windows 2000 及以後版本平台根據預設會使用 Kerberos 通訊協定。 當建立將與內部網路用戶端進行互動的服務時，了解系統的機制會有所幫助。 此外，由於 Web 服務安全性的*kerberos*系結已廣泛發佈，因此您可以使用 kerberos 通訊協定與網際網路用戶端進行通訊（也就是 kerberos 通訊協定可互通）。 如需有關如何在 Windows 中執行 Kerberos 通訊協定的詳細資訊，請參閱[Microsoft kerberos](https://go.microsoft.com/fwlink/?LinkId=210212)。  
  
### <a name="x509-certificates"></a>X.509 憑證  
 X.509 憑證是在安全性應用程式中使用的主要認證形式。 如需 x.509 憑證的詳細資訊，請參閱[X.509 公開金鑰憑證](https://go.microsoft.com/fwlink/?LinkId=210213)。 X.509 憑證儲存在憑證存放區中。 執行 Windows 的電腦上有多種憑證存放區，每個存放區都有不同的用途。 如需不同存放區的詳細資訊，請參閱[憑證存放區](https://go.microsoft.com/fwlink/?LinkID=87787)。  
  
## <a name="web-services-security-specifications"></a>Web 服務安全性規格  
 系統定義的繫結支援許多常用的 Web 服務安全性規格。 如需系統提供之系結和其支援的 web 服務規格的完整清單，請參閱：[由系統提供的互通性系結所支援的 Web 服務通訊協定](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>存取控制機制  
 WCF 提供數種方法來控制服務或作業的存取權。 包括  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. ASP.NET 成員資格提供者  
  
3. ASP.NET 角色提供者  
  
4. 授權管理員  
  
5. 識別模型  
  
 如需有關這些主題的詳細資訊，請參閱[存取控制機制](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>請參閱

- [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Windows Server App Fabric 的安全性模型](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
