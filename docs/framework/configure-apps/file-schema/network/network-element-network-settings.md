---
title: <network> 項目 (網路設定)
description: <network>網路設定元素會在 .NET Framework 中設定外部 SMTP 伺服器選項的網路選項。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: cd142febc0b3aacf1be7978178a6a05d9b9aebbf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190276"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="a8d7b-103">\<network> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="a8d7b-103">\<network> Element (Network Settings)</span></span>

<span data-ttu-id="a8d7b-104">設定外部 Simple Mail Transport Protocol (SMTP) server 的網路選項。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-104">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="a8d7b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8d7b-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8d7b-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8d7b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a8d7b-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8d7b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a8d7b-108">Attributes</span></span>  
  
|<span data-ttu-id="a8d7b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a8d7b-109">Attribute</span></span>|<span data-ttu-id="a8d7b-110">描述</span><span class="sxs-lookup"><span data-stu-id="a8d7b-110">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="a8d7b-111">指定要在初始 SMTP 通訊協定要求中用來連接到 SMTP 郵件伺服器的用戶端功能變數名稱。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-111">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="a8d7b-112">預設值是送出要求的本機電腦的 localhost 名稱。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-112">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="a8d7b-113">指定是否應該使用預設的使用者認證來存取 smtp 郵件伺服器的 SMTP 交易。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-113">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="a8d7b-114">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-114">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="a8d7b-115">指定是否使用 SSL 來存取 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-115">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="a8d7b-116">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-116">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="a8d7b-117">指定要用於 SMTP 交易的 SMTP 郵件伺服器主機名稱。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-117">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="a8d7b-118">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-118">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="a8d7b-119">指定要用於 SMTP 郵件伺服器驗證的密碼。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-119">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="a8d7b-120">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-120">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="a8d7b-121">指定要用來連接到 SMTP 郵件伺服器的埠號碼。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-121">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="a8d7b-122">預設值為 25。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-122">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="a8d7b-123">指定服務提供者名稱 (SPN) ，以在使用 SMTP 交易的延伸保護時用於驗證。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-123">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="a8d7b-124">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-124">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="a8d7b-125">指定要用於 SMTP 郵件伺服器驗證的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-125">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="a8d7b-126">此屬性沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-126">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8d7b-127">子元素</span><span class="sxs-lookup"><span data-stu-id="a8d7b-127">Child Elements</span></span>  

 <span data-ttu-id="a8d7b-128">無。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8d7b-129">父項目</span><span class="sxs-lookup"><span data-stu-id="a8d7b-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a8d7b-130">項目</span><span class="sxs-lookup"><span data-stu-id="a8d7b-130">Element</span></span>|<span data-ttu-id="a8d7b-131">描述</span><span class="sxs-lookup"><span data-stu-id="a8d7b-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8d7b-132">\<smtp> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="a8d7b-132">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="a8d7b-133">設定 Simple Mail Transport Protocol (SMTP) Mail 傳送選項。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-133">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8d7b-134">備註</span><span class="sxs-lookup"><span data-stu-id="a8d7b-134">Remarks</span></span>  

 <span data-ttu-id="a8d7b-135">某些 SMTP 伺服器會要求您在使用之前先向伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-135">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="a8d7b-136">如果您想要使用主機上的預設網路認證來自行驗證，請將 `defaultCredentials` 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-136">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="a8d7b-137"><xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `defaultCredentials` 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-137">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="a8d7b-138">您也可以使用基本驗證 (使用者名稱和密碼) ，向 SMTP 伺服器驗證您自己的身分。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-138">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="a8d7b-139">若要使用此選項，您必須為指定的 SMTP 伺服器指定有效的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-139">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8d7b-140">基本驗證會將 `userName` 和 `password` 值傳送到未加密的伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-140">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="a8d7b-141">監視網路流量的任何人都可以查看您的認證，並使用它們來連線到伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-141">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="a8d7b-142">您應該考慮使用更安全的驗證機制，例如 Kerberos 或 NT LAN Manager (NTLM。 ) 如果 `defaultCredentials` 是 `true` ，則會使用 KERBEROS 或 ntlm，如果伺服器支援這些通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-142">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="a8d7b-143">基本驗證和預設網路認證選項互斥。如果您將設定 `defaultCredentials` 為， `true` 並指定使用者名稱和密碼，則會使用預設的網路認證，而且會忽略基本驗證資料。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-143">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="a8d7b-144">若為基本驗證，則您 `userName` 也應該指定， `password` 以將自己驗證到郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-144">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="a8d7b-145"><xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `userName` 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-145">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="a8d7b-146"><xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `password` 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-146">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="a8d7b-147">基於 `password` 安全性考慮，通常不會在設定檔中輸入屬性。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-147">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="a8d7b-148">屬性會將 `clientDomain` 初始 SMTP 通訊協定要求中使用的用戶端功能變數名稱變更為 SMTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-148">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="a8d7b-149">`clientDomain`屬性可以設定為本機電腦的完整功能變數名稱，而不是預設使用的 localhost 名稱。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-149">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="a8d7b-150">這可提供較高的 SMTP 通訊協定標準相容性。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-150">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="a8d7b-151">預設值是送出要求的本機電腦的 localhost 名稱。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-151">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="a8d7b-152"><xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `clientDomain` 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-152">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="a8d7b-153">`targetName`使用擴充保護時，會使用屬性來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-153">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="a8d7b-154">預設值的格式為 "SMTPSVC/"， \<host> 其中 \<host> 是 SMTP 郵件伺服器的主機名稱。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-154">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="a8d7b-155"><xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `targetName` 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-155">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="a8d7b-156">`enableSsl`屬性會指定是否使用 SSL 來存取 SMTP 郵件伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-156">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="a8d7b-157"><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>類別僅支援透過傳輸層安全性安全的 Smtp 服務延伸，如 RFC 3207 中所定義。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-157">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="a8d7b-158">在此模式中，SMTP 會話會在未加密的通道上開始，然後用戶端會將 STARTTLS 命令發出至伺服器，以切換到使用 SSL 的安全通訊。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-158">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="a8d7b-159">如需詳細資訊，請參閱網際網路工程任務推動小組所發佈的 RFC 3207 (IETF) 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-159">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="a8d7b-160">替代連接方法是在傳送任何通訊協定命令之前，先建立 SSL 會話的位置。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-160">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="a8d7b-161">此連接方法有時稱為 SMTPS，預設會使用埠465。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-161">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="a8d7b-162">目前不支援使用 SSL 的替代連接方法。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-162">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="a8d7b-163"><xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得屬性的目前值 `enableSsl` 。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-163">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8d7b-164">範例</span><span class="sxs-lookup"><span data-stu-id="a8d7b-164">Example</span></span>  

 <span data-ttu-id="a8d7b-165">下列範例會指定適當的 SMTP 參數，以使用預設網路認證來傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="a8d7b-165">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a8d7b-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8d7b-166">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="a8d7b-167">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a8d7b-167">Network Settings Schema</span></span>](index.md)
