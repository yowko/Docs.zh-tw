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
ms.openlocfilehash: 0f490fc09ada9ee80cb6cee12e9e9061e820026e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="security-concepts-used-in-wcf"></a><span data-ttu-id="cb48a-102">用於 WCF 的安全性概念</span><span class="sxs-lookup"><span data-stu-id="cb48a-102">Security Concepts Used in WCF</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="cb48a-103"> 安全性是根據已經在使用中並且部署於各種安全性基礎結構的概念建置。</span><span class="sxs-lookup"><span data-stu-id="cb48a-103"> security is built upon concepts already in use and deployed in various security infrastructures.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="cb48a-104"> 支援其中某些基礎結構，例如 Secure Sockets Layer (SSL) over HTTP (HTTPS)。</span><span class="sxs-lookup"><span data-stu-id="cb48a-104"> supports some of those infrastructures, such as Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="cb48a-105">但是，藉由在使用 SOAP 編碼之訊息上實作更新的互通安全性標準 (例如 WS-Security)，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 不僅是只能支援現有的安全性基礎結構。</span><span class="sxs-lookup"><span data-stu-id="cb48a-105">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] goes beyond supporting existing security infrastructures by implementing newer interoperable security standards (such as WS-Security) over SOAP-encoded messages.</span></span> <span data-ttu-id="cb48a-106">不論是使用現有的機制或新的互通標準，兩者都是依據相同的安全性概念。</span><span class="sxs-lookup"><span data-stu-id="cb48a-106">Whether you are using existing mechanisms or new interoperable standards, the security concepts behind both are the same.</span></span> <span data-ttu-id="cb48a-107">因此，若要實作應用程式的最佳安全性模型，最重要的是了解現有基礎結構與較新標準所依據的概念。</span><span class="sxs-lookup"><span data-stu-id="cb48a-107">Understanding the concepts behind existing infrastructures and the newer standards is central to implementing the best security model for an application.</span></span>  
  
## <a name="introduction-to-security-for-wcf-web-services"></a><span data-ttu-id="cb48a-108">WCF Web 服務安全性簡介</span><span class="sxs-lookup"><span data-stu-id="cb48a-108">Introduction to Security for WCF Web Services</span></span>  
 <span data-ttu-id="cb48a-109">在 WCF 安全性指導方針即這裡下載 Microsoft Patterns and Practices 群組所撰寫的深入的技術白皮書： [WCF 安全性指南 》](http://go.microsoft.com/fwlink/?LinkId=210210)。</span><span class="sxs-lookup"><span data-stu-id="cb48a-109">The Microsoft Patterns and Practices group wrote an in-depth whitepaper on WCF security guidance which is available for download here: [WCF Security Guide](http://go.microsoft.com/fwlink/?LinkId=210210).</span></span> <span data-ttu-id="cb48a-110">本白皮書描述基本安全性概念，因為這些概念與 Web 服務、主要 WCF 安全性概念、內部網路應用程式案例，以及網際網路應用程式案例有關。</span><span class="sxs-lookup"><span data-stu-id="cb48a-110">This whitepaper describes the fundamental security concepts as they relate to web services, key WCF security concepts, intranet application scenarios, and internet application scenarios.</span></span>  
  
## <a name="industry-wide-security-specifications"></a><span data-ttu-id="cb48a-111">業界安全性規格</span><span class="sxs-lookup"><span data-stu-id="cb48a-111">Industry-Wide Security Specifications</span></span>  
  
### <a name="public-key-infrastructure"></a><span data-ttu-id="cb48a-112">公開金鑰基礎結構</span><span class="sxs-lookup"><span data-stu-id="cb48a-112">Public Key Infrastructure</span></span>  
 <span data-ttu-id="cb48a-113">公開金鑰基礎結構 (PKI) 是結合了數位憑證、憑證授權單位，與其他註冊授權單位，並以公開金鑰密碼編譯法來驗證參與電子異動之每一方的系統。</span><span class="sxs-lookup"><span data-stu-id="cb48a-113">Public Key Infrastructure (PKI) is a system of digital certificates, certification authorities, and other registration authorities that verify and authenticate each party involved in an electronic transaction through the use of public key cryptography.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="cb48a-114">[Windows Server 2008 R2 憑證服務](http://go.microsoft.com/fwlink/?LinkId=210211)。</span><span class="sxs-lookup"><span data-stu-id="cb48a-114"> [Windows Server 2008 R2 Certificate Services](http://go.microsoft.com/fwlink/?LinkId=210211).</span></span>  
  
### <a name="kerberos-protocol"></a><span data-ttu-id="cb48a-115">Kerberos 通訊協定</span><span class="sxs-lookup"><span data-stu-id="cb48a-115">Kerberos Protocol</span></span>  
 <span data-ttu-id="cb48a-116">*Kerberos 通訊協定*是規格，來建立安全性機制來驗證使用者的 Windows 網域上。</span><span class="sxs-lookup"><span data-stu-id="cb48a-116">The *Kerberos protocol* is a specification for creating a security mechanism that authenticates users on a Windows domain.</span></span> <span data-ttu-id="cb48a-117">它允許使用者在網域中使用其他實體建立安全內容。</span><span class="sxs-lookup"><span data-stu-id="cb48a-117">It allows a user to establish a secure context with other entities within a domain.</span></span> <span data-ttu-id="cb48a-118">Windows 2000 及以後版本平台根據預設會使用 Kerberos 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cb48a-118">Windows 2000 and later platforms use the Kerberos protocol by default.</span></span> <span data-ttu-id="cb48a-119">當建立將與內部網路用戶端進行互動的服務時，了解系統的機制會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="cb48a-119">Understanding the mechanisms of the system is useful when creating a service that will interact with intranet clients.</span></span> <span data-ttu-id="cb48a-120">此外，因為*Web 服務安全性 Kerberos 繫結*已經廣泛發行，您可以使用 Kerberos 通訊協定與網際網路用戶端通訊 （也就是 Kerberos 通訊協定具有互通性）。</span><span class="sxs-lookup"><span data-stu-id="cb48a-120">In addition, since the *Web Services Security Kerberos Binding* is widely published, you can use the Kerberos protocol to communicate with Internet clients (that is, the Kerberos protocol is interoperable).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="cb48a-121">如何在 Windows 中實作 Kerberos 通訊協定時，請參閱[Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)。</span><span class="sxs-lookup"><span data-stu-id="cb48a-121"> how the Kerberos protocol is implemented in Windows, see  [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).</span></span>  
  
### <a name="x509-certificates"></a><span data-ttu-id="cb48a-122">X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="cb48a-122">X.509 Certificates</span></span>  
 <span data-ttu-id="cb48a-123">X.509 憑證是在安全性應用程式中使用的主要認證形式。</span><span class="sxs-lookup"><span data-stu-id="cb48a-123">X.509 certificates are a primary credential form used in security applications.</span></span> <span data-ttu-id="cb48a-124">如需有關 X.509 憑證，請參閱[X.509 公用金鑰憑證](http://go.microsoft.com/fwlink/?LinkId=210213)。</span><span class="sxs-lookup"><span data-stu-id="cb48a-124">For more information on X.509 certificates see [X.509 Public Key Certificates](http://go.microsoft.com/fwlink/?LinkId=210213).</span></span> <span data-ttu-id="cb48a-125">X.509 憑證儲存在憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="cb48a-125">X.509 certificates are stored within a certificate store.</span></span> <span data-ttu-id="cb48a-126">執行 Windows 的電腦上有多種憑證存放區，每個存放區都有不同的用途。</span><span class="sxs-lookup"><span data-stu-id="cb48a-126">A computer running Windows has several kinds of certificate stores, each with a different purpose.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="cb48a-127">不同的存放區，請參閱[憑證存放區](http://go.microsoft.com/fwlink/?LinkID=87787)。</span><span class="sxs-lookup"><span data-stu-id="cb48a-127"> the different stores, see [Certificate Stores](http://go.microsoft.com/fwlink/?LinkID=87787).</span></span>  
  
## <a name="web-services-security-specifications"></a><span data-ttu-id="cb48a-128">Web 服務安全性規格</span><span class="sxs-lookup"><span data-stu-id="cb48a-128">Web Services Security Specifications</span></span>  
 <span data-ttu-id="cb48a-129">系統定義的繫結支援許多常用的 Web 服務安全性規格。</span><span class="sxs-lookup"><span data-stu-id="cb48a-129">The system-defined bindings support many commonly used web services security specifications.</span></span> <span data-ttu-id="cb48a-130">如需完整清單，系統提供繫結和 web 服務規格的支援，請參閱：[通訊協定支援的 Web 服務之互通性繫結](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="cb48a-130">For a complete list of system-provided bindings and the web services specifications they support see: [Web Services Protocols Supported by System-Provided Interoperability Bindings](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span></span>  
  
## <a name="access-control-mechanisms"></a><span data-ttu-id="cb48a-131">存取控制機制</span><span class="sxs-lookup"><span data-stu-id="cb48a-131">Access Control Mechanisms</span></span>  
 <span data-ttu-id="cb48a-132">WCF 提供數種方法來控制服務或作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="cb48a-132">WCF provides a number of ways to control access to a service or operation.</span></span> <span data-ttu-id="cb48a-133">包括</span><span class="sxs-lookup"><span data-stu-id="cb48a-133">Among them are</span></span>  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  <span data-ttu-id="cb48a-134">ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="cb48a-134">ASP.NET Membership Provider</span></span>  
  
3.  <span data-ttu-id="cb48a-135">ASP.NET 角色提供者</span><span class="sxs-lookup"><span data-stu-id="cb48a-135">ASP.NET Role Provider</span></span>  
  
4.  <span data-ttu-id="cb48a-136">授權管理員</span><span class="sxs-lookup"><span data-stu-id="cb48a-136">Authorization Manager</span></span>  
  
5.  <span data-ttu-id="cb48a-137">識別模型</span><span class="sxs-lookup"><span data-stu-id="cb48a-137">Identity Model</span></span>  
  
 <span data-ttu-id="cb48a-138">如需有關這些主題，請參閱[存取控制機制](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)</span><span class="sxs-lookup"><span data-stu-id="cb48a-138">For more information on these topics see, [Access Control Mechanisms](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb48a-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb48a-139">See Also</span></span>  
 [<span data-ttu-id="cb48a-140">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="cb48a-140">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="cb48a-141">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="cb48a-141">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
