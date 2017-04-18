---
title: "用於 WCF 的安全性概念 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: 15
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 15
---
# 用於 WCF 的安全性概念
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 安全性是根據已經在使用中並且部署於各種安全性基礎結構的概念建置。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援其中某些基礎結構，例如 Secure Sockets Layer \(SSL\) over HTTP \(HTTPS\)。但是，藉由在使用 SOAP 編碼之訊息上實作更新的互通安全性標準 \(例如 WS\-Security\)，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不僅是只能支援現有的安全性基礎結構。不論是使用現有的機制或新的互通標準，兩者都是依據相同的安全性概念。因此，若要實作應用程式的最佳安全性模型，最重要的是了解現有基礎結構與較新標準所依據的概念。  
  
## WCF Web 服務安全性簡介  
 Microsoft 典範與實例群組針對 WCF 安全性指引所撰寫的深入白皮書可於下列位址下載：[WCF 安全性指南](http://go.microsoft.com/fwlink/?LinkId=210210)。本白皮書描述基本安全性概念，因為這些概念與 Web 服務、主要 WCF 安全性概念、內部網路應用程式案例，以及網際網路應用程式案例有關。  
  
## 業界安全性規格  
  
### 公開金鑰基礎結構  
 公開金鑰基礎結構 \(PKI\) 是結合數位憑證、憑證授權單位及其他註冊授權單位，使用公開金鑰加密確認並驗證參與電子交易之每一方的系統。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Server 2008 R2 憑證服務](http://go.microsoft.com/fwlink/?LinkId=210211)。  
  
### Kerberos 通訊協定  
 「*Kerberos 通訊協定*」\(Kerberos Protocol\) 是建立安全性機制以便在 Windows 網域驗證使用者的規格。它允許使用者在網域中使用其他實體建立安全內容。Windows 2000 及以後版本平台根據預設會使用 Kerberos 通訊協定。當建立將與內部網路用戶端進行互動的服務時，了解系統的機制會有所幫助。此外，因為「*Web 服務安全性 Kerberos 繫結*」\(Web Services Security Kerberos Binding\) 已經廣泛發行，所以您可以使用 Kerberos 通訊協定與網際網路用戶端進行通訊 \(也就是 Kerberos 通訊協定具有互通性\)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何在 Windows 中實作 Kerberos 通訊協定的詳細資訊，請參閱 [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)。  
  
### X.509 憑證  
 X.509 憑證是在安全性應用程式中使用的主要認證形式。如需 X.509 憑證的詳細資訊，請參閱 [X.509 公用金鑰憑證](http://go.microsoft.com/fwlink/?LinkId=210213)。X.509 憑證儲存在憑證存放區中。執行 Windows 的電腦上有幾種存放區，每個存放區都有不同的用途。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]不同存放區的詳細資訊，請參閱[憑證存放區](http://go.microsoft.com/fwlink/?LinkID=87787)。  
  
## Web 服務安全性規格  
 系統定義的繫結支援許多常用的 Web 服務安全性規格。如需系統提供之繫結的完整清單，及其所支援的 Web 服務規格，請參閱：[系統提供的互通性繫結所支援的 Web 服務通訊協定](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
  
## 存取控制機制  
 WCF 提供數種方法來控制服務或作業的存取權。包括  
  
1.  <xref:System.Security.Permissions.PrinciplePermissionAttribute>  
  
2.  ASP.NET 成員資格提供者  
  
3.  ASP.NET 角色提供者  
  
4.  授權管理員  
  
5.  識別模型  
  
 如需這些主題的詳細資訊，請參閱[存取控制機制](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
  
## 請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Windows Server AppFabric 的資訊安全模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)