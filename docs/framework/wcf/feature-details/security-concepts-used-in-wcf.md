---
title: "用於 WCF 的安全性概念"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 142de63c3d61ae2ff7f89b1d602f2a48c739f53a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="security-concepts-used-in-wcf"></a>用於 WCF 的安全性概念
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 安全性是根據已經在使用中並且部署於各種安全性基礎結構的概念建置。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援其中某些基礎結構，例如 Secure Sockets Layer (SSL) over HTTP (HTTPS)。 但是，藉由在使用 SOAP 編碼之訊息上實作更新的互通安全性標準 (例如 WS-Security)，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不僅是只能支援現有的安全性基礎結構。 不論是使用現有的機制或新的互通標準，兩者都是依據相同的安全性概念。 因此，若要實作應用程式的最佳安全性模型，最重要的是了解現有基礎結構與較新標準所依據的概念。  
  
## <a name="introduction-to-security-for-wcf-web-services"></a>WCF Web 服務安全性簡介  
 在 WCF 安全性指導方針即這裡下載 Microsoft Patterns and Practices 群組所撰寫的深入的技術白皮書： [WCF 安全性指南 》](http://go.microsoft.com/fwlink/?LinkId=210210)。 本白皮書描述基本安全性概念，因為這些概念與 Web 服務、主要 WCF 安全性概念、內部網路應用程式案例，以及網際網路應用程式案例有關。  
  
## <a name="industry-wide-security-specifications"></a>業界安全性規格  
  
### <a name="public-key-infrastructure"></a>公開金鑰基礎結構  
 公開金鑰基礎結構 (PKI) 是結合了數位憑證、憑證授權單位，與其他註冊授權單位，並以公開金鑰密碼編譯法來驗證參與電子異動之每一方的系統。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Server 2008 R2 憑證服務](http://go.microsoft.com/fwlink/?LinkId=210211)。  
  
### <a name="kerberos-protocol"></a>Kerberos 通訊協定  
 *Kerberos 通訊協定*是規格，來建立安全性機制來驗證使用者的 Windows 網域上。 它允許使用者在網域中使用其他實體建立安全內容。 Windows 2000 及以後版本平台根據預設會使用 Kerberos 通訊協定。 當建立將與內部網路用戶端進行互動的服務時，了解系統的機制會有所幫助。 此外，因為*Web 服務安全性 Kerberos 繫結*已經廣泛發行，您可以使用 Kerberos 通訊協定與網際網路用戶端通訊 （也就是 Kerberos 通訊協定具有互通性）。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何在 Windows 中實作 Kerberos 通訊協定時，請參閱[Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)。  
  
### <a name="x509-certificates"></a>X.509 憑證  
 X.509 憑證是在安全性應用程式中使用的主要認證形式。 如需有關 X.509 憑證，請參閱[X.509 公用金鑰憑證](http://go.microsoft.com/fwlink/?LinkId=210213)。 X.509 憑證儲存在憑證存放區中。 執行 Windows 的電腦上有多種憑證存放區，每個存放區都有不同的用途。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]不同的存放區，請參閱[憑證存放區](http://go.microsoft.com/fwlink/?LinkID=87787)。  
  
## <a name="web-services-security-specifications"></a>Web 服務安全性規格  
 系統定義的繫結支援許多常用的 Web 服務安全性規格。 如需完整清單，系統提供繫結和 web 服務規格的支援，請參閱：[通訊協定支援的 Web 服務之互通性繫結](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## <a name="access-control-mechanisms"></a>存取控制機制  
 WCF 提供數種方法來控制服務或作業的存取權。 包括  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  ASP.NET 成員資格提供者  
  
3.  ASP.NET 角色提供者  
  
4.  授權管理員  
  
5.  識別模型  
  
 如需有關這些主題，請參閱[存取控制機制](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## <a name="see-also"></a>請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric 的安全性模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
