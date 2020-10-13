---
ms.openlocfilehash: d312ba2a22797ff6afff6b893f998c965e68e86e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997762"
---
### <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="74b98-101">Linux 上適用于 .NET 的預設 TLS 加密套件</span><span class="sxs-lookup"><span data-stu-id="74b98-101">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="74b98-102">.NET 在 Linux 上，現在會在透過 <xref:System.Net.Security.SslStream> 類別或更高層級的作業（例如透過類別的 HTTPS）進行 TLS/SSL 時，遵循預設加密套件的 OpenSSL 設定 <xref:System.Net.Http.HttpClient> 。</span><span class="sxs-lookup"><span data-stu-id="74b98-102">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="74b98-103">未明確設定預設的加密套件時，Linux 上的 .NET 會使用受嚴格限制的允許密碼套件清單。</span><span class="sxs-lookup"><span data-stu-id="74b98-103">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74b98-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="74b98-104">Change description</span></span>

<span data-ttu-id="74b98-105">在舊版的 .NET 中，.NET 不遵守預設加密套件的系統組態。</span><span class="sxs-lookup"><span data-stu-id="74b98-105">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="74b98-106">Linux 上適用于 .NET 的預設加密套件清單非常寬鬆。</span><span class="sxs-lookup"><span data-stu-id="74b98-106">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="74b98-107">從 .NET 5.0 開始，Linux 上的 .NET 在 *OpenSSL. my.cnf*中指定時，會遵循預設加密套件的 OpenSSL 設定。</span><span class="sxs-lookup"><span data-stu-id="74b98-107">Starting in .NET 5.0, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="74b98-108">未明確設定加密套件時，唯一允許的加密套件如下所示：</span><span class="sxs-lookup"><span data-stu-id="74b98-108">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="74b98-109">TLS 1.3 加密套件</span><span class="sxs-lookup"><span data-stu-id="74b98-109">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="74b98-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="74b98-110">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="74b98-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="74b98-111">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="74b98-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="74b98-112">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="74b98-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="74b98-113">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="74b98-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="74b98-114">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="74b98-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="74b98-115">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="74b98-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="74b98-116">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="74b98-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="74b98-117">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="74b98-118">因為此回復預設不包含任何與 TLS 1.0 或 TLS 1.1 相容的加密套件，所以這些較舊的通訊協定版本預設會有效停用。</span><span class="sxs-lookup"><span data-stu-id="74b98-118">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="74b98-119">針對特定會話提供 CipherSuitePolicy 值給 SslStream，仍會取代設定檔內容和/或 .NET 回預設值。</span><span class="sxs-lookup"><span data-stu-id="74b98-119">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="74b98-120">變更的原因</span><span class="sxs-lookup"><span data-stu-id="74b98-120">Reason for change</span></span>

<span data-ttu-id="74b98-121">在 Linux 上執行 .NET 的使用者要求將預設設定 <xref:System.Net.Security.SslStream> 變更為從協力廠商評量工具提供高安全性評等的設定。</span><span class="sxs-lookup"><span data-stu-id="74b98-121">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74b98-122">引進的版本</span><span class="sxs-lookup"><span data-stu-id="74b98-122">Version introduced</span></span>

<span data-ttu-id="74b98-123">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="74b98-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74b98-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="74b98-124">Recommended action</span></span>

<span data-ttu-id="74b98-125">當與新式用戶端或伺服器通訊時，新的預設值可能會運作。</span><span class="sxs-lookup"><span data-stu-id="74b98-125">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="74b98-126">如果您需要展開預設的加密套件清單以接受舊版用戶端 (或要) 的舊版伺服器，請指定 `CipherSuitePolicy` 值或變更 OpenSSL 設定檔。</span><span class="sxs-lookup"><span data-stu-id="74b98-126">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="74b98-127">在許多 Linux 發行版本上，OpenSSL 設定檔位於 */etc/ssl/openssl.cnf*。</span><span class="sxs-lookup"><span data-stu-id="74b98-127">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="74b98-128">這個範例 *openssl. my.cnf* 檔案是最基本的檔案，相當於 Linux 上 .net 5.0 和更新版本的預設加密套件原則。</span><span class="sxs-lookup"><span data-stu-id="74b98-128">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5.0 and later on Linux.</span></span> <span data-ttu-id="74b98-129">與其取代系統檔案，請將這些概念與系統上存在的檔案合併。</span><span class="sxs-lookup"><span data-stu-id="74b98-129">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="74b98-130">在 Red Hat Enterprise Linux、CentOS 和 Fedora 發行版本上，.NET 應用程式預設為全系統密碼編譯原則所允許的加密套件。</span><span class="sxs-lookup"><span data-stu-id="74b98-130">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="74b98-131">在這些散發套件上，請使用加密原則設定，而不是 *openssl. my.cnf*。</span><span class="sxs-lookup"><span data-stu-id="74b98-131">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

#### <a name="category"></a><span data-ttu-id="74b98-132">類別</span><span class="sxs-lookup"><span data-stu-id="74b98-132">Category</span></span>

- <span data-ttu-id="74b98-133">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="74b98-133">Cryptography</span></span>
- <span data-ttu-id="74b98-134">安全性</span><span class="sxs-lookup"><span data-stu-id="74b98-134">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74b98-135">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="74b98-135">Affected APIs</span></span>

<span data-ttu-id="74b98-136">未透過 API 分析 detectible。</span><span class="sxs-lookup"><span data-stu-id="74b98-136">Not detectible via API analysis.</span></span>

<!--

#### Affected APIs

- Not detectible via API analysis.

-->
