---
title: <network> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154812"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="f160f-102">\<網路>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="f160f-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="f160f-103">配置外部簡單郵件傳輸協議 （SMTP） 伺服器的網路選項。</span><span class="sxs-lookup"><span data-stu-id="f160f-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

<span data-ttu-id="f160f-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f160f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f160f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f160f-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="f160f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<郵件設置>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f160f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="f160f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<斯姆特普>**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f160f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="f160f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<網路>**</span><span class="sxs-lookup"><span data-stu-id="f160f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f160f-109">語法</span><span class="sxs-lookup"><span data-stu-id="f160f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f160f-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f160f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f160f-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f160f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f160f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f160f-112">Attributes</span></span>  
  
|<span data-ttu-id="f160f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f160f-113">Attribute</span></span>|<span data-ttu-id="f160f-114">描述</span><span class="sxs-lookup"><span data-stu-id="f160f-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="f160f-115">指定要在初始 SMTP 協定請求中用於連接到 SMTP 郵件伺服器的用戶端功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="f160f-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="f160f-116">預設值是發送請求的本地電腦的本地主機名稱稱。</span><span class="sxs-lookup"><span data-stu-id="f160f-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="f160f-117">指定是否應使用預設使用者憑據訪問 SMTP 事務中的 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f160f-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="f160f-118">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="f160f-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="f160f-119">指定是否使用 SSL 訪問 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f160f-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="f160f-120">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="f160f-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="f160f-121">指定用於 SMTP 事務的 SMTP 郵件伺服器的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f160f-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="f160f-122">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f160f-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="f160f-123">指定用於對 SMTP 郵件伺服器進行身份驗證的密碼。</span><span class="sxs-lookup"><span data-stu-id="f160f-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="f160f-124">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f160f-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="f160f-125">指定用於連接到 SMTP 郵件伺服器的埠號。</span><span class="sxs-lookup"><span data-stu-id="f160f-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="f160f-126">預設值為 25。</span><span class="sxs-lookup"><span data-stu-id="f160f-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="f160f-127">指定用於對 SMTP 事務使用擴展保護的服務提供者名稱 （SPN）。</span><span class="sxs-lookup"><span data-stu-id="f160f-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="f160f-128">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f160f-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="f160f-129">指定用於對 SMTP 郵件伺服器進行身份驗證的使用者名。</span><span class="sxs-lookup"><span data-stu-id="f160f-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="f160f-130">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="f160f-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f160f-131">子元素</span><span class="sxs-lookup"><span data-stu-id="f160f-131">Child Elements</span></span>  
 <span data-ttu-id="f160f-132">無。</span><span class="sxs-lookup"><span data-stu-id="f160f-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f160f-133">父項目</span><span class="sxs-lookup"><span data-stu-id="f160f-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f160f-134">元素</span><span class="sxs-lookup"><span data-stu-id="f160f-134">Element</span></span>|<span data-ttu-id="f160f-135">描述</span><span class="sxs-lookup"><span data-stu-id="f160f-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f160f-136">\<smtp>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="f160f-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="f160f-137">配置簡單的郵件傳輸協議 （SMTP） 郵件發送選項。</span><span class="sxs-lookup"><span data-stu-id="f160f-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f160f-138">備註</span><span class="sxs-lookup"><span data-stu-id="f160f-138">Remarks</span></span>  
 <span data-ttu-id="f160f-139">某些 SMTP 伺服器要求您在使用前向伺服器進行身份驗證。</span><span class="sxs-lookup"><span data-stu-id="f160f-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="f160f-140">如果要使用主機上的預設網路憑據進行身份驗證，請將`defaultCredentials`屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="f160f-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="f160f-141">該<xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`defaultCredentials`當前值。</span><span class="sxs-lookup"><span data-stu-id="f160f-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="f160f-142">您還可以使用基本驗證（使用者名和密碼）對 SMTP 伺服器進行身份驗證。</span><span class="sxs-lookup"><span data-stu-id="f160f-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="f160f-143">要使用此選項，必須為指定的 SMTP 伺服器指定有效的使用者名和密碼。</span><span class="sxs-lookup"><span data-stu-id="f160f-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f160f-144">基本驗證將`userName`和`password`值發送到未加密的伺服器。</span><span class="sxs-lookup"><span data-stu-id="f160f-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="f160f-145">監視網路流量的任何人都可以查看您的憑據，並使用它們連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="f160f-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="f160f-146">應考慮使用更安全的身份驗證機制，如 Kerberos 或 NT LAN 管理器 （NTLM）。如果是`defaultCredentials``true`，如果伺服器支援這些協定，將使用 Kerberos 或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="f160f-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="f160f-147">基本驗證和預設網路憑據選項是互斥的;如果設置為`defaultCredentials``true`並指定使用者名和密碼，則使用預設網路憑據，並忽略基本驗證資料。</span><span class="sxs-lookup"><span data-stu-id="f160f-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="f160f-148">對於基本驗證，如果指定`userName`了 ，則還應指定`password`以自行對郵件伺服器進行身份驗證。</span><span class="sxs-lookup"><span data-stu-id="f160f-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="f160f-149">該<xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`userName`當前值。</span><span class="sxs-lookup"><span data-stu-id="f160f-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="f160f-150">該<xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`password`當前值。</span><span class="sxs-lookup"><span data-stu-id="f160f-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="f160f-151">出於`password`安全原因，通常不會在設定檔中輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="f160f-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="f160f-152">該`clientDomain`屬性將初始 SMTP 協定請求中使用的用戶端功能變數名稱更改為 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="f160f-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="f160f-153">該`clientDomain`屬性可以設置為本地電腦的完全限定功能變數名稱，而不是預設情況下使用的本地主機名稱稱。</span><span class="sxs-lookup"><span data-stu-id="f160f-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="f160f-154">這提高了 SMTP 協定標準的合規性。</span><span class="sxs-lookup"><span data-stu-id="f160f-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="f160f-155">預設值是發送請求的本地電腦的本地主機名稱稱。</span><span class="sxs-lookup"><span data-stu-id="f160f-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="f160f-156">該<xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`clientDomain`當前值。</span><span class="sxs-lookup"><span data-stu-id="f160f-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="f160f-157">使用`targetName`擴展保護時，該屬性用於身份驗證。</span><span class="sxs-lookup"><span data-stu-id="f160f-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="f160f-158">預設值為"SMTPSVC/\<主機>"的形式，其中\<主機>是 SMTP 郵件伺服器的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f160f-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="f160f-159">該<xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`targetName`當前值。</span><span class="sxs-lookup"><span data-stu-id="f160f-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="f160f-160">該`enableSsl`屬性指定是否使用 SSL 訪問 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="f160f-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="f160f-161">該<xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類僅支援 RFC 3207 中定義的通過傳輸層安全性實現安全 SMTP 的 SMTP 服務擴展。</span><span class="sxs-lookup"><span data-stu-id="f160f-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="f160f-162">在此模式下，SMTP 會話從未加密的通道開始，然後用戶端向伺服器發出 STARTTLS 命令，以便使用 SSL 切換到安全通信。</span><span class="sxs-lookup"><span data-stu-id="f160f-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="f160f-163">有關詳細資訊，請參閱互聯網工程工作組 （IETF） 發佈的 RFC 3207。</span><span class="sxs-lookup"><span data-stu-id="f160f-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="f160f-164">備用連接方法是在發送任何協定命令之前預先建立 SSL 會話。</span><span class="sxs-lookup"><span data-stu-id="f160f-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="f160f-165">此連接方法有時稱為 SMTPS，預設情況下使用埠 465。</span><span class="sxs-lookup"><span data-stu-id="f160f-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="f160f-166">當前不支援使用此 SSL 的替代連接方法。</span><span class="sxs-lookup"><span data-stu-id="f160f-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="f160f-167">該<xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>屬性可用於從適用的設定檔獲取屬性的`enableSsl`當前值。</span><span class="sxs-lookup"><span data-stu-id="f160f-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f160f-168">範例</span><span class="sxs-lookup"><span data-stu-id="f160f-168">Example</span></span>  
 <span data-ttu-id="f160f-169">下面的示例指定使用預設網路憑據發送電子郵件的相應 SMTP 參數。</span><span class="sxs-lookup"><span data-stu-id="f160f-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f160f-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f160f-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="f160f-171">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="f160f-171">Network Settings Schema</span></span>](index.md)
