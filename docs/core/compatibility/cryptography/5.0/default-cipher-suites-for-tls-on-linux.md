---
title: 重大變更： Linux 上適用于 .NET 的預設 TLS 加密套件
description: 瞭解 .net 5.0 中的重大變更，在此情況下，Linux 上的 .NET 現在會在執行 TLS/SSL 時遵守預設加密套件的 OpenSSL 設定。
ms.date: 10/16/2020
ms.openlocfilehash: f1c23517161ac213a9cd7cf6e7da8eebeb91583b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760424"
---
# <a name="default-tls-cipher-suites-for-net-on-linux"></a><span data-ttu-id="695ed-103">Linux 上適用于 .NET 的預設 TLS 加密套件</span><span class="sxs-lookup"><span data-stu-id="695ed-103">Default TLS cipher suites for .NET on Linux</span></span>

<span data-ttu-id="695ed-104">.NET 在 Linux 上，現在會在透過 <xref:System.Net.Security.SslStream> 類別或更高層級的作業（例如透過類別的 HTTPS）進行 TLS/SSL 時，遵循預設加密套件的 OpenSSL 設定 <xref:System.Net.Http.HttpClient> 。</span><span class="sxs-lookup"><span data-stu-id="695ed-104">.NET, on Linux, now respects the OpenSSL configuration for default cipher suites when doing TLS/SSL via the <xref:System.Net.Security.SslStream> class or higher-level operations, such as HTTPS via the <xref:System.Net.Http.HttpClient> class.</span></span> <span data-ttu-id="695ed-105">未明確設定預設的加密套件時，Linux 上的 .NET 會使用受嚴格限制的允許密碼套件清單。</span><span class="sxs-lookup"><span data-stu-id="695ed-105">When default cipher suites aren't explicitly configured, .NET on Linux uses a tightly restricted list of permitted cipher suites.</span></span>

## <a name="change-description"></a><span data-ttu-id="695ed-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="695ed-106">Change description</span></span>

<span data-ttu-id="695ed-107">在舊版的 .NET 中，.NET 不遵守預設加密套件的系統組態。</span><span class="sxs-lookup"><span data-stu-id="695ed-107">In previous .NET versions, .NET does not respect system configuration for default cipher suites.</span></span> <span data-ttu-id="695ed-108">Linux 上適用于 .NET 的預設加密套件清單非常寬鬆。</span><span class="sxs-lookup"><span data-stu-id="695ed-108">The default cipher suite list for .NET on Linux is very permissive.</span></span>

<span data-ttu-id="695ed-109">從 .NET 5.0 開始，Linux 上的 .NET 在 *OpenSSL. my.cnf* 中指定時，會遵循預設加密套件的 OpenSSL 設定。</span><span class="sxs-lookup"><span data-stu-id="695ed-109">Starting in .NET 5.0, .NET on Linux respects the OpenSSL configuration for default cipher suites when it's specified in *openssl.cnf*.</span></span> <span data-ttu-id="695ed-110">未明確設定加密套件時，唯一允許的加密套件如下所示：</span><span class="sxs-lookup"><span data-stu-id="695ed-110">When cipher suites aren't explicitly configured, the only permitted cipher suites are as follows:</span></span>

- <span data-ttu-id="695ed-111">TLS 1.3 加密套件</span><span class="sxs-lookup"><span data-stu-id="695ed-111">TLS 1.3 cipher suites</span></span>
- <span data-ttu-id="695ed-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="695ed-112">TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="695ed-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="695ed-113">TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="695ed-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span><span class="sxs-lookup"><span data-stu-id="695ed-114">TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384</span></span>
- <span data-ttu-id="695ed-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span><span class="sxs-lookup"><span data-stu-id="695ed-115">TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256</span></span>
- <span data-ttu-id="695ed-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="695ed-116">TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="695ed-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="695ed-117">TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256</span></span>
- <span data-ttu-id="695ed-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span><span class="sxs-lookup"><span data-stu-id="695ed-118">TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</span></span>
- <span data-ttu-id="695ed-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span><span class="sxs-lookup"><span data-stu-id="695ed-119">TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256</span></span>

<span data-ttu-id="695ed-120">因為此回復預設不包含任何與 TLS 1.0 或 TLS 1.1 相容的加密套件，所以這些較舊的通訊協定版本預設會有效停用。</span><span class="sxs-lookup"><span data-stu-id="695ed-120">Since this fallback default doesn't include any cipher suites that are compatible with TLS 1.0 or TLS 1.1, these older protocol versions are effectively disabled by default.</span></span>

<span data-ttu-id="695ed-121">針對特定會話提供 CipherSuitePolicy 值給 SslStream，仍會取代設定檔內容和/或 .NET 回預設值。</span><span class="sxs-lookup"><span data-stu-id="695ed-121">Supplying a CipherSuitePolicy value to SslStream for a specific session will still replace the configuration file content and/or .NET fallback default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="695ed-122">變更的原因</span><span class="sxs-lookup"><span data-stu-id="695ed-122">Reason for change</span></span>

<span data-ttu-id="695ed-123">在 Linux 上執行 .NET 的使用者要求將預設設定 <xref:System.Net.Security.SslStream> 變更為從協力廠商評量工具提供高安全性評等的設定。</span><span class="sxs-lookup"><span data-stu-id="695ed-123">Users running .NET on Linux requested that the default configuration for <xref:System.Net.Security.SslStream> be changed to one that provided a high security rating from third-party assessment tools.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="695ed-124">引進的版本</span><span class="sxs-lookup"><span data-stu-id="695ed-124">Version introduced</span></span>

<span data-ttu-id="695ed-125">5.0</span><span class="sxs-lookup"><span data-stu-id="695ed-125">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="695ed-126">建議的動作</span><span class="sxs-lookup"><span data-stu-id="695ed-126">Recommended action</span></span>

<span data-ttu-id="695ed-127">當與新式用戶端或伺服器通訊時，新的預設值可能會運作。</span><span class="sxs-lookup"><span data-stu-id="695ed-127">The new defaults are likely to work when communicating with modern clients or servers.</span></span> <span data-ttu-id="695ed-128">如果您需要展開預設的加密套件清單以接受舊版用戶端 (或要) 的舊版伺服器，請指定 `CipherSuitePolicy` 值或變更 OpenSSL 設定檔。</span><span class="sxs-lookup"><span data-stu-id="695ed-128">If you need to expand the default cipher suite list to accept legacy clients (or to contact legacy servers), either specify a `CipherSuitePolicy` value or change the OpenSSL configuration file.</span></span> <span data-ttu-id="695ed-129">在許多 Linux 發行版本上，OpenSSL 設定檔位於 */etc/ssl/openssl.cnf*。</span><span class="sxs-lookup"><span data-stu-id="695ed-129">On many Linux distributions, the OpenSSL configuration file is at */etc/ssl/openssl.cnf*.</span></span>

<span data-ttu-id="695ed-130">這個範例 *openssl. my.cnf* 檔案是最基本的檔案，相當於 Linux 上 .net 5.0 和更新版本的預設加密套件原則。</span><span class="sxs-lookup"><span data-stu-id="695ed-130">This sample *openssl.cnf* file is a minimal file that's equivalent to the default cipher suites policy for .NET 5.0 and later on Linux.</span></span> <span data-ttu-id="695ed-131">與其取代系統檔案，請將這些概念與系統上存在的檔案合併。</span><span class="sxs-lookup"><span data-stu-id="695ed-131">Instead of replacing the system file, merge these concepts with the file that's present on your system.</span></span>

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

<span data-ttu-id="695ed-132">在 Red Hat Enterprise Linux、CentOS 和 Fedora 發行版本上，.NET 應用程式預設為全系統密碼編譯原則所允許的加密套件。</span><span class="sxs-lookup"><span data-stu-id="695ed-132">On the Red Hat Enterprise Linux, CentOS, and Fedora distributions, .NET applications default to the cipher suites permitted by the system-wide cryptographic policies.</span></span> <span data-ttu-id="695ed-133">在這些散發套件上，請使用加密原則設定，而不是 *openssl. my.cnf*。</span><span class="sxs-lookup"><span data-stu-id="695ed-133">On these distributions, use the crypto-policies configuration instead of *openssl.cnf*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="695ed-134">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="695ed-134">Affected APIs</span></span>

<span data-ttu-id="695ed-135">未透過 API 分析 detectible。</span><span class="sxs-lookup"><span data-stu-id="695ed-135">Not detectible via API analysis.</span></span>

<!--

### Affected APIs

- Not detectible via API analysis.

### Category

- Cryptography
- Security

-->
