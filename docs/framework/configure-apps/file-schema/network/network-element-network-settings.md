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
ms.openlocfilehash: 40d89f7bd7a1f4a38a1c4030a86405e09c497899
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659319"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="060b3-102">\<網路 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="060b3-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="060b3-103">設定外部簡易郵件傳輸通訊協定 (SMTP) 伺服器的網路選項。</span><span class="sxs-lookup"><span data-stu-id="060b3-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="060b3-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="060b3-104">\<configuration></span></span>  
<span data-ttu-id="060b3-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="060b3-105">\<system.net></span></span>  
<span data-ttu-id="060b3-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="060b3-106">\<mailSettings></span></span>  
<span data-ttu-id="060b3-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="060b3-107">\<smtp></span></span>  
<span data-ttu-id="060b3-108">\<network></span><span class="sxs-lookup"><span data-stu-id="060b3-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060b3-109">語法</span><span class="sxs-lookup"><span data-stu-id="060b3-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="060b3-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="060b3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="060b3-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="060b3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="060b3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="060b3-112">Attributes</span></span>  
  
|<span data-ttu-id="060b3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="060b3-113">Attribute</span></span>|<span data-ttu-id="060b3-114">說明</span><span class="sxs-lookup"><span data-stu-id="060b3-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="060b3-115">指定要在初始 SMTP 通訊協定要求中用來連接 SMTP 郵件伺服器的用戶端功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="060b3-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="060b3-116">預設值是傳送要求的本機電腦的 localhost 名稱。</span><span class="sxs-lookup"><span data-stu-id="060b3-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="060b3-117">指定是否應該使用預設的使用者認證來存取 smtp 交易的 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="060b3-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="060b3-118">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="060b3-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="060b3-119">指定是否使用 SSL 來存取 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="060b3-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="060b3-120">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="060b3-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="060b3-121">指定要用於 SMTP 交易的 SMTP 郵件伺服器的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="060b3-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="060b3-122">這個屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="060b3-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="060b3-123">指定要用於 SMTP 郵件伺服器驗證的密碼。</span><span class="sxs-lookup"><span data-stu-id="060b3-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="060b3-124">這個屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="060b3-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="060b3-125">指定要用來連接 SMTP 郵件伺服器的通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="060b3-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="060b3-126">預設值為 25。</span><span class="sxs-lookup"><span data-stu-id="060b3-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="060b3-127">指定使用 SMTP 交易的擴充保護時, 用於驗證的服務提供者名稱 (SPN)。</span><span class="sxs-lookup"><span data-stu-id="060b3-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="060b3-128">這個屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="060b3-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="060b3-129">指定要用於 SMTP 郵件伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="060b3-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="060b3-130">這個屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="060b3-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="060b3-131">子元素</span><span class="sxs-lookup"><span data-stu-id="060b3-131">Child Elements</span></span>  
 <span data-ttu-id="060b3-132">無。</span><span class="sxs-lookup"><span data-stu-id="060b3-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="060b3-133">父項目</span><span class="sxs-lookup"><span data-stu-id="060b3-133">Parent Elements</span></span>  
  
|<span data-ttu-id="060b3-134">項目</span><span class="sxs-lookup"><span data-stu-id="060b3-134">Element</span></span>|<span data-ttu-id="060b3-135">說明</span><span class="sxs-lookup"><span data-stu-id="060b3-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="060b3-136">\<smtp > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="060b3-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="060b3-137">設定簡單郵件傳輸通訊協定 (SMTP) 郵件傳送選項。</span><span class="sxs-lookup"><span data-stu-id="060b3-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="060b3-138">備註</span><span class="sxs-lookup"><span data-stu-id="060b3-138">Remarks</span></span>  
 <span data-ttu-id="060b3-139">某些 SMTP 伺服器需要您先向伺服器驗證, 才能使用。</span><span class="sxs-lookup"><span data-stu-id="060b3-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="060b3-140">如果您想要使用主機上的預設網路認證來驗證自己, 請將`defaultCredentials`屬性設定`true`為。</span><span class="sxs-lookup"><span data-stu-id="060b3-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="060b3-141">屬性可以用來從適用的`defaultCredentials`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="060b3-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="060b3-142">您也可以使用基本驗證 (使用者名稱和密碼) 向 SMTP 伺服器驗證您自己的身分。</span><span class="sxs-lookup"><span data-stu-id="060b3-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="060b3-143">若要使用此選項, 您必須為指定的 SMTP 伺服器指定有效的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="060b3-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="060b3-144">基本驗證會`userName`將`password`和值傳送到未加密的伺服器。</span><span class="sxs-lookup"><span data-stu-id="060b3-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="060b3-145">監視網路流量的任何人都可以看到您的認證, 並使用它們來連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="060b3-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="060b3-146">您應該考慮使用更安全的驗證機制, 例如 Kerberos 或 NT LAN Manager (NTLM)。如果`defaultCredentials` 為`true`, 則如果伺服器支援這些通訊協定, 則會使用 Kerberos 或 NTLM。</span><span class="sxs-lookup"><span data-stu-id="060b3-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="060b3-147">[基本驗證] 和 [預設網路認證] 選項互斥。如果您將`defaultCredentials`設定`true`為, 並指定使用者名稱和密碼, 則會使用預設網路認證, 而且會忽略基本驗證資料。</span><span class="sxs-lookup"><span data-stu-id="060b3-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="060b3-148">若為 [基本驗證] `userName`, 如果您指定, 您`password`也應該指定, 以對郵件伺服器進行自我驗證。</span><span class="sxs-lookup"><span data-stu-id="060b3-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="060b3-149">屬性可以用來從適用的`userName`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="060b3-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="060b3-150">屬性可以用來從適用的`password`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="060b3-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="060b3-151">基於安全考慮, 通常不會在設定檔中輸入屬性。`password`</span><span class="sxs-lookup"><span data-stu-id="060b3-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="060b3-152">`clientDomain`屬性會將初始 smtp 通訊協定要求中所使用的用戶端功能變數名稱變更為 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="060b3-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="060b3-153">`clientDomain`屬性可以設定為本機電腦的完整功能變數名稱, 而不是預設使用的 localhost 名稱。</span><span class="sxs-lookup"><span data-stu-id="060b3-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="060b3-154">這可提供更高的 SMTP 通訊協定標準合規性。</span><span class="sxs-lookup"><span data-stu-id="060b3-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="060b3-155">預設值是傳送要求的本機電腦的 localhost 名稱。</span><span class="sxs-lookup"><span data-stu-id="060b3-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="060b3-156">屬性可以用來從適用的`clientDomain`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="060b3-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="060b3-157">當`targetName`使用擴充保護時, 會使用屬性來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="060b3-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="060b3-158">預設值的格式為 "SMTPSVC/\<host >", 其中\<host > 是 SMTP 郵件伺服器的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="060b3-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="060b3-159">屬性可以用來從適用的`targetName`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="060b3-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="060b3-160">`enableSsl`屬性會指定是否使用 SSL 來存取 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="060b3-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="060b3-161"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類別僅支援透過傳輸層安全性 (如 RFC 3207 中所定義) 的 Secure smtp 的 smtp 服務延伸。</span><span class="sxs-lookup"><span data-stu-id="060b3-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="060b3-162">在此模式中, SMTP 會話會在未加密的通道上開始, 然後用戶端會將 STARTTLS 命令發行至伺服器, 以切換至使用 SSL 的安全通訊。</span><span class="sxs-lookup"><span data-stu-id="060b3-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="060b3-163">如需詳細資訊, 請參閱網際網路工程任務推動小組 (IETF) 所發佈的 RFC 3207。</span><span class="sxs-lookup"><span data-stu-id="060b3-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="060b3-164">替代連接方法是在傳送任何通訊協定命令之前, 先建立 SSL 會話的前方。</span><span class="sxs-lookup"><span data-stu-id="060b3-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="060b3-165">此連接方法有時稱為 SMTPS, 而且預設會使用埠465。</span><span class="sxs-lookup"><span data-stu-id="060b3-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="060b3-166">目前不支援使用 SSL 的替代連接方法。</span><span class="sxs-lookup"><span data-stu-id="060b3-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="060b3-167">屬性可以用來從適用的`enableSsl`設定檔案取得屬性的目前值。 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="060b3-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="060b3-168">範例</span><span class="sxs-lookup"><span data-stu-id="060b3-168">Example</span></span>  
 <span data-ttu-id="060b3-169">下列範例會指定適當的 SMTP 參數, 以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="060b3-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="060b3-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="060b3-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="060b3-171">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="060b3-171">Network Settings Schema</span></span>](index.md)
