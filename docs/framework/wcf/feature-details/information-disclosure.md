---
title: 資訊洩漏
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: a58ac4dd3715052031c7fb5c1da480c0d01396ea
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596860"
---
# <a name="information-disclosure"></a><span data-ttu-id="6b2ef-102">資訊洩漏</span><span class="sxs-lookup"><span data-stu-id="6b2ef-102">Information Disclosure</span></span>

<span data-ttu-id="6b2ef-103">資訊洩漏讓攻擊者可以取得與系統有關的寶貴資訊。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-103">Information disclosure enables an attacker to gain valuable information about a system.</span></span> <span data-ttu-id="6b2ef-104">因此，公開資訊時，請務必考慮您要公開的是哪些資訊，以及是否會遭到惡意使用者的使用。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-104">Therefore, always consider what information you are revealing and whether it can be used by a malicious user.</span></span> <span data-ttu-id="6b2ef-105">下列列出可能的資訊洩漏攻擊，並針對各種攻擊提供減少受到攻擊的方法。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-105">The following lists possible information disclosure attacks and provides mitigations for each.</span></span>

## <a name="message-security-and-http"></a><span data-ttu-id="6b2ef-106">訊息安全性和 HTTP</span><span class="sxs-lookup"><span data-stu-id="6b2ef-106">Message Security and HTTP</span></span>

<span data-ttu-id="6b2ef-107">如果您正在使用 HTTP 傳輸層上的訊息層級安全性，請注意，訊息層級安全性不會保護 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-107">If you are using message-level security over an HTTP transport layer, be aware that message-level security does not protect HTTP headers.</span></span> <span data-ttu-id="6b2ef-108">保護 HTTP 標頭的唯一方法就是使用 HTTPS 傳輸取代 HTTP。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-108">The only way to protect HTTP headers is to use HTTPS transport instead of HTTP.</span></span> <span data-ttu-id="6b2ef-109">HTTPS 傳輸使用 Secure Sockets Layer (SSL) 通訊協定加密整個訊息，包括 HTTP 標頭。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-109">HTTPS transport causes the entire message, including the HTTP headers, to be encrypted using the Secure Sockets Layer (SSL) protocol.</span></span>

## <a name="policy-information"></a><span data-ttu-id="6b2ef-110">原則資訊</span><span class="sxs-lookup"><span data-stu-id="6b2ef-110">Policy Information</span></span>

<span data-ttu-id="6b2ef-111">維持原則的安全相當重要，特別是在原則中公開敏感的發行權杖需求或權杖簽發者資訊的聯合案例中。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-111">Keeping policy secure is important, especially in federation scenarios where sensitive issued-token requirements or token-issuer information is exposed in policy.</span></span> <span data-ttu-id="6b2ef-112">在這些情況中，建議保護聯合服務的原則端點，以避免攻擊者取得與服務有關的資訊，例如放在發行權杖中的宣告類型，或將用戶端重新導向至惡意的權杖簽發者。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-112">In these cases, the recommendation is to secure the federated service's policy endpoint to prevent attackers from obtaining information about the service, such as the type of claims to put in the issued token, or redirecting clients to malicious token issuers.</span></span> <span data-ttu-id="6b2ef-113">例如，攻擊者可以透過重新設定聯合信任鏈結來找出使用者名組/密碼組，以終止執行中間人攻擊的簽發者。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-113">For example, an attacker could discover user name/password pairs by reconfiguring the federated trust chain to terminate in an issuer that executed a man-in-the-middle attack.</span></span> <span data-ttu-id="6b2ef-114">同時，也建議透過原則擷取來取得繫結的同盟用戶端，確認他們信任所取得之同盟信任鏈結中的簽發者。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-114">It is also recommended that federated clients who obtain their bindings through policy retrieval verify that they trust the issuers in the obtained federated trust chain.</span></span> <span data-ttu-id="6b2ef-115">如需同盟案例的詳細資訊，請參閱[同盟](federation.md)。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-115">For more information about federation scenarios, see [Federation](federation.md).</span></span>

## <a name="memory-dumps-can-reveal-claim-information"></a><span data-ttu-id="6b2ef-116">記憶體傾印會洩漏宣告資訊</span><span class="sxs-lookup"><span data-stu-id="6b2ef-116">Memory Dumps Can Reveal Claim Information</span></span>

<span data-ttu-id="6b2ef-117">應用程式失敗時，Dr. Watson 等產生的記錄檔會包含宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-117">When an application fails, log files, such as those produced by Dr. Watson, can contain the claim information.</span></span> <span data-ttu-id="6b2ef-118">這項資訊不應該匯出到其他實體，例如支援團隊等，否則可能會一併匯出包含私人資料的宣告資訊。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-118">This information should not be exported to other entities, such as support teams; otherwise, the claim information that contains private data is also exported.</span></span> <span data-ttu-id="6b2ef-119">只要不將記錄檔傳送給未知的實體，即可減少這種情況。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-119">You can mitigate this by not sending the log files to unknown entities.</span></span>

## <a name="endpoint-addresses"></a><span data-ttu-id="6b2ef-120">端點位址</span><span class="sxs-lookup"><span data-stu-id="6b2ef-120">Endpoint Addresses</span></span>

<span data-ttu-id="6b2ef-121">端點位址包含與端點通訊所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-121">An endpoint address contains the information needed to communicate with an endpoint.</span></span> <span data-ttu-id="6b2ef-122">SOAP 安全性必須在交換的安全性交涉訊息中加入完整位址，以便在用戶端和伺服器之間交涉對稱金鑰。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-122">SOAP security must include the address in full in the security negotiation messages that are exchanged in order to negotiate a symmetric key between a client and a server.</span></span> <span data-ttu-id="6b2ef-123">因為安全性交涉是開機處理序，所以在執行此處理序期間無法將位址標頭加密。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-123">Because security negotiation is a bootstrap process, the address headers cannot be encrypted during this process.</span></span> <span data-ttu-id="6b2ef-124">因此，位址不應含有任何機密資料，否則會導致發生資訊洩漏攻擊。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-124">Therefore, the address should not contain any confidential data; otherwise, it leads to information disclosure attacks.</span></span>

## <a name="certificates-transferred-unencrypted"></a><span data-ttu-id="6b2ef-125">未加密的憑證傳輸</span><span class="sxs-lookup"><span data-stu-id="6b2ef-125">Certificates Transferred Unencrypted</span></span>

<span data-ttu-id="6b2ef-126">當您使用 X.509 憑證驗證用戶端時，會在 SOAP 標頭內明確傳送憑證。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-126">When you use an X.509 certificate to authenticate a client, the certificate is transferred in the clear, inside the SOAP header.</span></span> <span data-ttu-id="6b2ef-127">請注意，這樣可能會洩漏個人可識別資訊 (PII)。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-127">Be aware of this as a potential personally identifiable information (PII) disclosure.</span></span> <span data-ttu-id="6b2ef-128">這不是 `TransportWithMessageCredential` 模式的問題，此模式會以傳輸層級安全性加密整個訊息。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-128">This is not an issue for `TransportWithMessageCredential` mode, where the entire message is encrypted with transport-level security.</span></span>

## <a name="service-references"></a><span data-ttu-id="6b2ef-129">服務參考</span><span class="sxs-lookup"><span data-stu-id="6b2ef-129">Service References</span></span>

<span data-ttu-id="6b2ef-130">服務參考是其他服務的參考。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-130">A service reference is a reference to another service.</span></span> <span data-ttu-id="6b2ef-131">例如，服務可能傳遞服務參考到運作中的用戶端。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-131">For example, a service may pass a service reference to a client in the course of an operation.</span></span> <span data-ttu-id="6b2ef-132">服務參考也會與*信任身分識別驗證*器搭配使用，這是一個內部元件，可確保目標主體的身分識別，再將資訊（例如應用程式資料或認證）公開給目標。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-132">The service reference is also used with a *trust identity verifier*, an internal component that ensures the identity of the target principal before disclosing information such as application data or credentials to the target.</span></span> <span data-ttu-id="6b2ef-133">如果遠端信任識別無法確認或不正確，傳送者應確保不會洩漏可能危害到自己、應用程式或使用者的資料。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-133">If the remote trust identity cannot be verified or is incorrect, the sender should ensure that no data was disclosed that could compromise itself, the application, or the user.</span></span>

<span data-ttu-id="6b2ef-134">安全防護包括下列：</span><span class="sxs-lookup"><span data-stu-id="6b2ef-134">Mitigations include the following:</span></span>

- <span data-ttu-id="6b2ef-135">服務參考假設為可以信任。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-135">Service references are assumed to be trustworthy.</span></span> <span data-ttu-id="6b2ef-136">每次傳送服務參考執行個體時，小心確保它們不會遭到竄改。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-136">Take care whenever transferring service reference instances to ensure that they have not been tampered with.</span></span>

- <span data-ttu-id="6b2ef-137">有些應用程式會提供使用者體驗，可根據服務參考中的資料以及經由遠端主機證實的信任資料，互相建立信任。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-137">Some applications can present a user experience that allows interactive establishment of trust based on data in the service reference and trust data proven by the remote host.</span></span> <span data-ttu-id="6b2ef-138">WCF 為這類設施提供了擴充點，但使用者必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-138">WCF provides extensibility points for such a facility, but the user must implemented them.</span></span>

## <a name="ntlm"></a><span data-ttu-id="6b2ef-139">NTLM</span><span class="sxs-lookup"><span data-stu-id="6b2ef-139">NTLM</span></span>

<span data-ttu-id="6b2ef-140">在預設情況下，Windows 網域環境中的 Windows 驗證會使用 Kerberos 通訊協定來驗證和授權使用者。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-140">By default, in the Windows domain environment, Windows authentication uses the Kerberos protocol to authenticate and authorize users.</span></span> <span data-ttu-id="6b2ef-141">如果基於某個原因而無法使用 Kerberos 通訊協定，請使用 NT LAN Manager (NTLM) 做為後援。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-141">If the Kerberos protocol cannot be used for some reason, NT LAN Manager (NTLM) is used as a fallback.</span></span> <span data-ttu-id="6b2ef-142">透過將 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> 屬性設定為 `false`，即可停用此行為。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-142">You can disable this behavior by setting the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property to `false`.</span></span> <span data-ttu-id="6b2ef-143">允許 NTLM 時要注意的問題包括：</span><span class="sxs-lookup"><span data-stu-id="6b2ef-143">Issues to be aware of when allowing NTLM include:</span></span>

- <span data-ttu-id="6b2ef-144">NTLM 會公開用戶端使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-144">NTLM exposes the client user name.</span></span> <span data-ttu-id="6b2ef-145">如果使用者名稱需要保密，請將繫結上的 `AllowNTLM` 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-145">If the user name needs to be kept confidential, then set the `AllowNTLM` property on the binding to `false`.</span></span>

- <span data-ttu-id="6b2ef-146">NTLM 不會提供伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-146">NTLM does not provide server authentication.</span></span> <span data-ttu-id="6b2ef-147">因此，當您使用 NTLM 做為驗證通訊協定時，用戶端無法確保能與正確的服務通訊。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-147">Therefore, the client cannot ensure that it is communicating with the right service when you use NTLM as an authentication protocol.</span></span>

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a><span data-ttu-id="6b2ef-148">指定用戶端認證或無效的識別強制 NTLM 使用</span><span class="sxs-lookup"><span data-stu-id="6b2ef-148">Specifying Client Credentials or Invalid Identity Forces NTLM Usage</span></span>

<span data-ttu-id="6b2ef-149">當建立用戶端、指定沒有網域名稱的用戶端認證或指定無效的伺服器識別時，會導致使用 NTLM 取代 Kerberos 通訊協定 (如果 `AllowNtlm` 屬性設定為 `true`)。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-149">When creating a client, specifying client credentials without a domain name, or specifying an invalid server identity, causes NTLM to be used instead of the Kerberos protocol (if the `AllowNtlm` property is set to `true`).</span></span> <span data-ttu-id="6b2ef-150">由於 NTLM 不會驗證伺服器，因此資訊可能會遭到洩漏。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-150">Because  NTLM does not do server authentication, information can potentially be disclosed.</span></span>

<span data-ttu-id="6b2ef-151">例如，您可以指定沒有功能變數名稱的 Windows 用戶端認證，如下列 Visual c # 程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-151">For example, it is possible to specify Windows client credentials without a domain name, as shown in the following Visual C# code.</span></span>

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

<span data-ttu-id="6b2ef-152">程式碼沒有指定網域名稱，因此將會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-152">The code does not specify a domain name, and therefore NTLM will be used.</span></span>

<span data-ttu-id="6b2ef-153">如果有指定網域，但使用端點識別功能來指定無效的服務主體名稱，則會使用 NTLM。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-153">If the domain is specified, but an invalid service principal name is specified using the endpoint identity feature, then NTLM is used.</span></span> <span data-ttu-id="6b2ef-154">如需如何指定端點身分識別的詳細資訊，請參閱[服務身分識別和驗證](service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="6b2ef-154">For more information about how endpoint identity is specified, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6b2ef-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="6b2ef-155">See also</span></span>

- [<span data-ttu-id="6b2ef-156">安全性考量</span><span class="sxs-lookup"><span data-stu-id="6b2ef-156">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="6b2ef-157">權限提高</span><span class="sxs-lookup"><span data-stu-id="6b2ef-157">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="6b2ef-158">拒絕服務</span><span class="sxs-lookup"><span data-stu-id="6b2ef-158">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="6b2ef-159">竄改</span><span class="sxs-lookup"><span data-stu-id="6b2ef-159">Tampering</span></span>](tampering.md)
- [<span data-ttu-id="6b2ef-160">不支援的案例</span><span class="sxs-lookup"><span data-stu-id="6b2ef-160">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="6b2ef-161">重新執行攻擊</span><span class="sxs-lookup"><span data-stu-id="6b2ef-161">Replay Attacks</span></span>](replay-attacks.md)
