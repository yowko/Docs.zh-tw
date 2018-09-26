---
title: '&lt;網路&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 96a6c8a3c2d7114004278d3c40daf4d01b6c1d90
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170018"
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="f5e5e-102">&lt;網路&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="f5e5e-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="f5e5e-103">設定外部的 Simple Mail Transport Protocol (SMTP) 伺服器的網路選項。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="f5e5e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f5e5e-104">\<configuration></span></span>  
<span data-ttu-id="f5e5e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f5e5e-105">\<system.net></span></span>  
<span data-ttu-id="f5e5e-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="f5e5e-106">\<mailSettings></span></span>  
<span data-ttu-id="f5e5e-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="f5e5e-107">\<smtp></span></span>  
<span data-ttu-id="f5e5e-108">\<network></span><span class="sxs-lookup"><span data-stu-id="f5e5e-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5e5e-109">語法</span><span class="sxs-lookup"><span data-stu-id="f5e5e-109">Syntax</span></span>  
  
```xml  
<network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5e5e-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f5e5e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f5e5e-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5e5e-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f5e5e-112">Attributes</span></span>  
  
|<span data-ttu-id="f5e5e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f5e5e-113">Attribute</span></span>|<span data-ttu-id="f5e5e-114">描述</span><span class="sxs-lookup"><span data-stu-id="f5e5e-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="f5e5e-115">指定要用於連接到 SMTP 郵件伺服器的初始 SMTP 通訊協定要求的用戶端網域名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="f5e5e-116">預設值是傳送要求到本機電腦的本機主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="f5e5e-117">指定是否應該使用預設使用者認證存取 SMTP 交易的 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="f5e5e-118">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="f5e5e-119">指定是否使用 SSL 存取 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="f5e5e-120">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="f5e5e-121">指定要用於 SMTP 交易的 SMTP 郵件伺服器的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="f5e5e-122">此屬性有沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="f5e5e-123">指定要用於驗證的 SMTP 郵件伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="f5e5e-124">此屬性有沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="f5e5e-125">指定要用來連線到 SMTP 郵件伺服器的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="f5e5e-126">預設值為 25。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="f5e5e-127">指定要用於 SMTP 交易的擴充的保護時，用於驗證服務提供者名稱 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="f5e5e-128">此屬性有沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="f5e5e-129">指定要用來驗證的 SMTP 郵件伺服器的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="f5e5e-130">此屬性有沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5e5e-131">子元素</span><span class="sxs-lookup"><span data-stu-id="f5e5e-131">Child Elements</span></span>  
 <span data-ttu-id="f5e5e-132">無。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5e5e-133">父項目</span><span class="sxs-lookup"><span data-stu-id="f5e5e-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f5e5e-134">項目</span><span class="sxs-lookup"><span data-stu-id="f5e5e-134">Element</span></span>|<span data-ttu-id="f5e5e-135">描述</span><span class="sxs-lookup"><span data-stu-id="f5e5e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5e5e-136">\<smtp > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="f5e5e-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="f5e5e-137">設定 Simple Mail Transport Protocol (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5e5e-138">備註</span><span class="sxs-lookup"><span data-stu-id="f5e5e-138">Remarks</span></span>  
 <span data-ttu-id="f5e5e-139">部分 SMTP 伺服器需要您自行向伺服器使用之前進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="f5e5e-140">如果您想要驗證您在主機上使用預設網路認證、 設定`defaultCredentials`屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="f5e5e-141"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>屬性可用來取得目前的值`defaultCredentials`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="f5e5e-142">您也可以使用基本驗證 （使用者名稱和密碼） 來驗證您自己的 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="f5e5e-143">若要使用此選項，您必須指定有效的使用者名稱和指定的 SMTP 伺服器的密碼。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5e5e-144">基本驗證會傳送`userName`和`password`值，以未加密的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="f5e5e-145">監視網路流量的任何人都可以檢視您的認證，並使用它們來連線到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="f5e5e-146">您應該考慮使用更安全的驗證機制，例如 Kerberos 或 NT LAN Manager (NTLM)。如果`defaultCredentials`是`true`，將會使用 Kerberos 或 NTLM，如果伺服器支援這些通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="f5e5e-147">基本驗證和預設網路認證選項是互斥;如果您設定`defaultCredentials`至`true`使用者名稱和密碼，會使用預設網路認證，並指定基本驗證的資料會被忽略。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="f5e5e-148">基本驗證，如果您指定`userName`，您也應指定`password`驗證自己的郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="f5e5e-149"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>屬性可用來取得目前的值`userName`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="f5e5e-150"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>屬性可用來取得目前的值`password`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="f5e5e-151">A`password`屬性會無法正常輸入基於安全性的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="f5e5e-152">`clientDomain`屬性變更到 SMTP 伺服器的初始 SMTP 通訊協定要求中使用的用戶端網域名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="f5e5e-153">`clientDomain`屬性可以設為本機電腦的完整網域名稱，而不是預設會使用本機主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="f5e5e-154">這可提供更高的 SMTP 通訊協定標準的合規性。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="f5e5e-155">預設值是傳送要求到本機電腦的本機主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="f5e5e-156"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>屬性可用來取得目前的值`clientDomain`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="f5e5e-157">`targetName`屬性用來驗證擴充的保護時。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="f5e5e-158">預設值是"SMTPSVC /\<主機 > 」 其中\<主機 > 是 SMTP 郵件伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="f5e5e-159"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>屬性可用來取得目前的值`targetName`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="f5e5e-160">`enableSsl`屬性可讓您指定是否使用 SSL 存取 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="f5e5e-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類別只支援 SMTP 服務延伸模組保護 smtp 傳輸層安全性透過 RFC 3207 中所定義。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="f5e5e-162">在此模式中，SMTP 工作階段開始在未加密的通道，然後 STARTTLS 命令發出用戶端到伺服器，以切換為使用 SSL 的安全通訊。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="f5e5e-163">RFC 3207 發佈由 Internet Engineering Task Force (IETF) 如需詳細資訊，請參閱。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="f5e5e-164">其他連線方法是 SSL 工作階段事先建立之前命令會傳送任何通訊協定。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="f5e5e-165">此連線方法有時稱為 SMTPS，而且根據預設會使用連接埠 465。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="f5e5e-166">目前不支援這種替代的連線方法，使用 SSL。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="f5e5e-167"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>屬性可用來取得目前的值`enableSsl`適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e5e-168">範例</span><span class="sxs-lookup"><span data-stu-id="f5e5e-168">Example</span></span>  
 <span data-ttu-id="f5e5e-169">下列範例會指定適當的 SMTP 參數，使用預設網路認證傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="f5e5e-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5e5e-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5e5e-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="f5e5e-171">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f5e5e-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
