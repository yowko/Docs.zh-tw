---
title: "HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5589ad8e4193416738da98676551bbf82c128a79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="96e98-102">HOW TO：將 WCF 服務設為與 WSE 3.0 用戶端相互操作</span><span class="sxs-lookup"><span data-stu-id="96e98-102">How to: Configure WCF Services to Interoperate with WSE 3.0 Clients</span></span>
<span data-ttu-id="96e98-103">當 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務設定為使用 WS-Addressing August 2004 版本規格時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的連線層級與 Microsoft .NET 用戶端的 Web Services Enhancements (WSE) 3.0 相容。</span><span class="sxs-lookup"><span data-stu-id="96e98-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) clients when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a><span data-ttu-id="96e98-104">讓 WCF 服務與 WSE 3.0 用戶端相互操作</span><span class="sxs-lookup"><span data-stu-id="96e98-104">To enable a WCF service to interoperate with WSE 3.0 clients</span></span>  
  
1.  <span data-ttu-id="96e98-105">定義 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="96e98-105">Define a custom binding for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
     <span data-ttu-id="96e98-106">若要指定使用 WS-Addressing August 2004 版本規格進行訊息編碼，這時必須要建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="96e98-106">To specify that the August 2004 version of the WS-Addressing specification is used for message encoding, a custom binding must be created.</span></span>  
  
    1.  <span data-ttu-id="96e98-107">新增子系[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)至[\<繫結 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)服務的組態檔。</span><span class="sxs-lookup"><span data-stu-id="96e98-107">Add a child [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) of the service's configuration file.</span></span>  
  
    2.  <span data-ttu-id="96e98-108">加入指定的繫結，名稱[\<繫結 >](../../../../docs/framework/misc/binding.md)至[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)和設定`name`屬性。</span><span class="sxs-lookup"><span data-stu-id="96e98-108">Specify a name for the binding, by adding a [\<binding>](../../../../docs/framework/misc/binding.md) to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) and setting the `name` attribute.</span></span>  
  
    3.  <span data-ttu-id="96e98-109">指定驗證模式和 Ws-security 規格，可用來保護訊息藉由新增子系與 WSE 3.0 相容的新版[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)至[ \<繫結 >](../../../../docs/framework/misc/binding.md)。</span><span class="sxs-lookup"><span data-stu-id="96e98-109">Specify an authentication mode and the version of the WS-Security specifications that are used to secure messages that are compatible with WSE 3.0, by adding a child [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) to the [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
         <span data-ttu-id="96e98-110">若要設定驗證模式，請設定`authenicationMode`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="96e98-110">To set the authentication mode, set the `authenicationMode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="96e98-111">驗證模式約略相等於 WSE 3.0 中的組合安全性判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="96e98-111">An authentication mode is roughly equivalent to a turnkey security assertion in WSE 3.0.</span></span> <span data-ttu-id="96e98-112">下表會將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的驗證模式對應到 WSE 3.0 中的組合安全性判斷提示。</span><span class="sxs-lookup"><span data-stu-id="96e98-112">The following table maps authentication modes in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to turnkey security assertions in WSE 3.0.</span></span>  
  
        |<span data-ttu-id="96e98-113">WCF 驗證模式</span><span class="sxs-lookup"><span data-stu-id="96e98-113">WCF Authentication Mode</span></span>|<span data-ttu-id="96e98-114">WSE 3.0 組合安全性判斷提示</span><span class="sxs-lookup"><span data-stu-id="96e98-114">WSE 3.0 turnkey security assertion</span></span>|  
        |-----------------------------|----------------------------------------|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|  
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|  
  
         <span data-ttu-id="96e98-115">\*其中一個主要差異`mutualCertificate10Security`和`mutualCertificate11Security`通行安全性判斷提示是 WSE 用來保護 SOAP 訊息安全的 Ws-security 規格的版本。</span><span class="sxs-lookup"><span data-stu-id="96e98-115">\* One of the primary differences between the `mutualCertificate10Security` and `mutualCertificate11Security` turnkey security assertions is the version of the WS-Security specification that WSE uses to secure the SOAP messages.</span></span> <span data-ttu-id="96e98-116">若是 `mutualCertificate10Security` 會使用 WS-Security 1.0，若是 `mutualCertificate11Security` 則使用 WS-Security 1.1。</span><span class="sxs-lookup"><span data-stu-id="96e98-116">For `mutualCertificate10Security`, WS-Security 1.0 is used, whereas WS-Security 1.1 is used for `mutualCertificate11Security`.</span></span> <span data-ttu-id="96e98-117">如[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，Ws-security 規格的版本中指定`messageSecurityVersion`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="96e98-117">For [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the version of the WS-Security specification is specified in the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="96e98-118">若要設定用來保護 SOAP 訊息安全的 Ws-security 規格的版本，設定`messageSecurityVersion`屬性[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="96e98-118">To set the version of the WS-Security specification that is used to secure SOAP messages, set the `messageSecurityVersion` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span> <span data-ttu-id="96e98-119">為了與 WSE 3.0 進行相互操作，`messageSecurityVersion` 屬性的值要設定為 <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>。</span><span class="sxs-lookup"><span data-stu-id="96e98-119">To interoperate with WSE 3.0, set the value of the `messageSecurityVersion` attribute to <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>.</span></span>  
  
    4.  <span data-ttu-id="96e98-120">指定為使用 August 2004 版本的 Ws-addressing 規格[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]加[ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)並設定`messageVersion`為其值，以<xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>。</span><span class="sxs-lookup"><span data-stu-id="96e98-120">Specify that the August 2004 version of the WS-Addressing specification is used by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by adding a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md) and set the `messageVersion` to its value to <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="96e98-121">如果使用的是 SOAP 1.2，請將 `messageVersion` 屬性設為 <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>。</span><span class="sxs-lookup"><span data-stu-id="96e98-121">When you are using SOAP 1.2, set the `messageVersion` attribute to <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>.</span></span>  
  
2.  <span data-ttu-id="96e98-122">指定服務使用自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="96e98-122">Specify that the service uses the custom binding.</span></span>  
  
    1.  <span data-ttu-id="96e98-123">設定`binding`屬性[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)元素`customBinding`。</span><span class="sxs-lookup"><span data-stu-id="96e98-123">Set the `binding` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to `customBinding`.</span></span>  
  
    2.  <span data-ttu-id="96e98-124">設定`bindingConfiguration`屬性[\<端點 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目中指定的值`name`屬性[\<繫結 >](../../../../docs/framework/misc/binding.md)自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="96e98-124">Set the `bindingConfiguration` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element to the value specified in the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) for the custom binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96e98-125">範例</span><span class="sxs-lookup"><span data-stu-id="96e98-125">Example</span></span>  
 <span data-ttu-id="96e98-126">下列程式碼範例會指定 `Service.HelloWorldService` 使用自訂繫結來與 WSE 3.0 用戶端相互操作。</span><span class="sxs-lookup"><span data-stu-id="96e98-126">The following code example specifies that the `Service.HelloWorldService` uses a custom binding to interoperate with WSE 3.0 clients.</span></span> <span data-ttu-id="96e98-127">自訂繫結會指定使用 WS-Addressing August 2004 版本和 WS-Security 1.1 的規格組合來編碼已交換訊息。</span><span class="sxs-lookup"><span data-stu-id="96e98-127">The custom binding specifies that the August 2004 version of the WS-Addressing and the WS-Security 1.1 set of specifications are used to encode the exchanged messages.</span></span> <span data-ttu-id="96e98-128">這些訊息會使用 <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> 驗證模式來加以保護。</span><span class="sxs-lookup"><span data-stu-id="96e98-128">The messages are secured using the <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> authentication mode.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        behaviorConfiguration="ServiceBehavior"   
        name="Service.HelloWorldService">  
        <endpoint binding="customBinding" address=""  
          bindingConfiguration="ServiceBinding"  
          contract="Service.IHelloWorld"></endpoint>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="ServiceBinding">  
          <security authenticationMode="AnonymousForCertificate"  
                  messageProtectionOrder="SignBeforeEncrypt"  
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"  
                  requireDerivedKeys="false">  
          </security>  
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">  
        <serviceCredentials>  
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>  
        </serviceCredentials>  
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96e98-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96e98-129">See Also</span></span>  
 [<span data-ttu-id="96e98-130">如何： 自訂系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="96e98-130">How to: Customize a System-Provided Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
