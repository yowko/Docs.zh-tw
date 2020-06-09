---
title: 用於 WCF 的安全性概念
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: f852ba4e1100103289bc5fd879b19ebd40443b8d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595176"
---
# <a name="security-concepts-used-in-wcf"></a><span data-ttu-id="0c887-102">用於 WCF 的安全性概念</span><span class="sxs-lookup"><span data-stu-id="0c887-102">Security Concepts Used in WCF</span></span>
<span data-ttu-id="0c887-103">Windows Communication Foundation （WCF）安全性是根據已在使用中且已部署在各種安全性基礎結構中的概念所建立。</span><span class="sxs-lookup"><span data-stu-id="0c887-103">Windows Communication Foundation (WCF) security is built upon concepts already in use and deployed in various security infrastructures.</span></span>  
  
 <span data-ttu-id="0c887-104">WCF 支援其中一些基礎結構，例如安全通訊端層（SSL） over HTTP （HTTPS）。</span><span class="sxs-lookup"><span data-stu-id="0c887-104">WCF supports some of those infrastructures, such as Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="0c887-105">不過，WCF 不支援現有的安全性基礎結構，而是透過 SOAP 編碼的訊息來執行較新的互通安全性標準（例如 WS-MANAGEMENT）。</span><span class="sxs-lookup"><span data-stu-id="0c887-105">However, WCF goes beyond supporting existing security infrastructures by implementing newer interoperable security standards (such as WS-Security) over SOAP-encoded messages.</span></span> <span data-ttu-id="0c887-106">不論是使用現有的機制或新的互通標準，兩者都是依據相同的安全性概念。</span><span class="sxs-lookup"><span data-stu-id="0c887-106">Whether you are using existing mechanisms or new interoperable standards, the security concepts behind both are the same.</span></span> <span data-ttu-id="0c887-107">因此，若要實作應用程式的最佳安全性模型，最重要的是了解現有基礎結構與較新標準所依據的概念。</span><span class="sxs-lookup"><span data-stu-id="0c887-107">Understanding the concepts behind existing infrastructures and the newer standards is central to implementing the best security model for an application.</span></span>  
  
## <a name="introduction-to-security-for-wcf-web-services"></a><span data-ttu-id="0c887-108">WCF Web 服務安全性簡介</span><span class="sxs-lookup"><span data-stu-id="0c887-108">Introduction to Security for WCF Web Services</span></span>  

<span data-ttu-id="0c887-109">Microsoft 模式和實務小組撰寫了稱為「 [WCF 安全性指南](https://archive.codeplex.com/?p=wcfsecurityguide)」的深度技術白皮書。</span><span class="sxs-lookup"><span data-stu-id="0c887-109">The Microsoft Patterns and Practices group wrote an in-depth white paper called [WCF Security Guide](https://archive.codeplex.com/?p=wcfsecurityguide).</span></span> <span data-ttu-id="0c887-110">本白皮書說明與 web 服務、主要 WCF 安全性概念、內部網路應用程式案例，以及網際網路應用程式案例相關的基本安全性概念。</span><span class="sxs-lookup"><span data-stu-id="0c887-110">This white paper describes the fundamental security concepts as they relate to web services, key WCF security concepts, intranet application scenarios, and internet application scenarios.</span></span>  
  
## <a name="industry-wide-security-specifications"></a><span data-ttu-id="0c887-111">業界安全性規格</span><span class="sxs-lookup"><span data-stu-id="0c887-111">Industry-Wide Security Specifications</span></span>  
  
### <a name="public-key-infrastructure"></a><span data-ttu-id="0c887-112">公開金鑰基礎結構</span><span class="sxs-lookup"><span data-stu-id="0c887-112">Public Key Infrastructure</span></span>  

<span data-ttu-id="0c887-113">公開金鑰基礎結構（PKI）是一種數位憑證、憑證授權單位單位及其他註冊機關的系統，可透過使用公開金鑰加密來驗證和驗證涉及電子交易的每一方。</span><span class="sxs-lookup"><span data-stu-id="0c887-113">Public Key Infrastructure (PKI) is a system of digital certificates, certification authorities, and other registration authorities that verify and authenticate each party involved in an electronic transaction through the use of public-key cryptography.</span></span>
  
### <a name="kerberos-protocol"></a><span data-ttu-id="0c887-114">Kerberos 通訊協定</span><span class="sxs-lookup"><span data-stu-id="0c887-114">Kerberos Protocol</span></span>  
 <span data-ttu-id="0c887-115">*Kerberos 通訊協定*是用來建立安全性機制的規格，可驗證 Windows 網域上的使用者。</span><span class="sxs-lookup"><span data-stu-id="0c887-115">The *Kerberos protocol* is a specification for creating a security mechanism that authenticates users on a Windows domain.</span></span> <span data-ttu-id="0c887-116">它允許使用者在網域中使用其他實體建立安全內容。</span><span class="sxs-lookup"><span data-stu-id="0c887-116">It allows a user to establish a secure context with other entities within a domain.</span></span> <span data-ttu-id="0c887-117">Windows 2000 及以後版本平台根據預設會使用 Kerberos 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0c887-117">Windows 2000 and later platforms use the Kerberos protocol by default.</span></span> <span data-ttu-id="0c887-118">當建立將與內部網路用戶端進行互動的服務時，了解系統的機制會有所幫助。</span><span class="sxs-lookup"><span data-stu-id="0c887-118">Understanding the mechanisms of the system is useful when creating a service that will interact with intranet clients.</span></span> <span data-ttu-id="0c887-119">此外，由於 Web 服務安全性的*kerberos*系結已廣泛發佈，因此您可以使用 kerberos 通訊協定與網際網路用戶端進行通訊（也就是 kerberos 通訊協定可互通）。</span><span class="sxs-lookup"><span data-stu-id="0c887-119">In addition, since the *Web Services Security Kerberos Binding* is widely published, you can use the Kerberos protocol to communicate with Internet clients (that is, the Kerberos protocol is interoperable).</span></span> <span data-ttu-id="0c887-120">如需有關如何在 Windows 中執行 Kerberos 通訊協定的詳細資訊，請參閱[Microsoft kerberos](/windows/win32/secauthn/microsoft-kerberos)。</span><span class="sxs-lookup"><span data-stu-id="0c887-120">For more information about how the Kerberos protocol is implemented in Windows, see  [Microsoft Kerberos](/windows/win32/secauthn/microsoft-kerberos).</span></span>  
  
### <a name="x509-certificates"></a><span data-ttu-id="0c887-121">X.509 憑證</span><span class="sxs-lookup"><span data-stu-id="0c887-121">X.509 Certificates</span></span>  
 <span data-ttu-id="0c887-122">X.509 憑證是在安全性應用程式中使用的主要認證形式。</span><span class="sxs-lookup"><span data-stu-id="0c887-122">X.509 certificates are a primary credential form used in security applications.</span></span> <span data-ttu-id="0c887-123">如需 x.509 憑證的詳細資訊，請參閱[X.509 公開金鑰憑證](/windows/win32/seccertenroll/about-x-509-public-key-certificates)。</span><span class="sxs-lookup"><span data-stu-id="0c887-123">For more information on X.509 certificates see [X.509 Public Key Certificates](/windows/win32/seccertenroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="0c887-124">X.509 憑證儲存在憑證存放區中。</span><span class="sxs-lookup"><span data-stu-id="0c887-124">X.509 certificates are stored within a certificate store.</span></span> <span data-ttu-id="0c887-125">執行 Windows 的電腦上有多種憑證存放區，每個存放區都有不同的用途。</span><span class="sxs-lookup"><span data-stu-id="0c887-125">A computer running Windows has several kinds of certificate stores, each with a different purpose.</span></span> <span data-ttu-id="0c887-126">如需不同存放區的詳細資訊，請參閱[憑證存放區](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="0c887-126">For more information about the different stores, see [Certificate Stores](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span></span>  
  
## <a name="web-services-security-specifications"></a><span data-ttu-id="0c887-127">Web 服務安全性規格</span><span class="sxs-lookup"><span data-stu-id="0c887-127">Web Services Security Specifications</span></span>  
 <span data-ttu-id="0c887-128">系統定義的繫結支援許多常用的 Web 服務安全性規格。</span><span class="sxs-lookup"><span data-stu-id="0c887-128">The system-defined bindings support many commonly used web services security specifications.</span></span> <span data-ttu-id="0c887-129">如需系統提供之系結和其支援的 web 服務規格的完整清單，請參閱：[由系統提供的互通性系結所支援的 Web 服務通訊協定](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0c887-129">For a complete list of system-provided bindings and the web services specifications they support see: [Web Services Protocols Supported by System-Provided Interoperability Bindings](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span></span>  
  
## <a name="access-control-mechanisms"></a><span data-ttu-id="0c887-130">存取控制機制</span><span class="sxs-lookup"><span data-stu-id="0c887-130">Access Control Mechanisms</span></span>  
 <span data-ttu-id="0c887-131">WCF 提供數種方法來控制服務或作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="0c887-131">WCF provides a number of ways to control access to a service or operation.</span></span> <span data-ttu-id="0c887-132">包括</span><span class="sxs-lookup"><span data-stu-id="0c887-132">Among them are</span></span>  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. <span data-ttu-id="0c887-133">ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="0c887-133">ASP.NET Membership Provider</span></span>  
  
3. <span data-ttu-id="0c887-134">ASP.NET 角色提供者</span><span class="sxs-lookup"><span data-stu-id="0c887-134">ASP.NET Role Provider</span></span>  
  
4. <span data-ttu-id="0c887-135">授權管理員</span><span class="sxs-lookup"><span data-stu-id="0c887-135">Authorization Manager</span></span>  
  
5. <span data-ttu-id="0c887-136">識別模型</span><span class="sxs-lookup"><span data-stu-id="0c887-136">Identity Model</span></span>  
  
 <span data-ttu-id="0c887-137">如需有關這些主題的詳細資訊，請參閱[存取控制機制](access-control-mechanisms.md)</span><span class="sxs-lookup"><span data-stu-id="0c887-137">For more information on these topics see, [Access Control Mechanisms](access-control-mechanisms.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c887-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c887-138">See also</span></span>

- [<span data-ttu-id="0c887-139">安全性總覽</span><span class="sxs-lookup"><span data-stu-id="0c887-139">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="0c887-140">[Windows Server AppFabric 的資訊安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0c887-140">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
