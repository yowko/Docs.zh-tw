---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721163"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a><span data-ttu-id="39572-101">Linux 上的根憑證不再支援「開始信任的憑證」語法</span><span class="sxs-lookup"><span data-stu-id="39572-101">"BEGIN TRUSTED CERTIFICATE" syntax no longer supported for root certificates on Linux</span></span>

<span data-ttu-id="39572-102">Linux 上的根憑證和其他類似 Unix 的系統（但不是 macOS）可以用兩種形式呈現：標準 `BEGIN CERTIFICATE` PEM 標頭和 OpenSSL 特定的 `BEGIN TRUSTED CERTIFICATE` pem 標頭。</span><span class="sxs-lookup"><span data-stu-id="39572-102">Root certificates on Linux and other Unix-like systems (but not macOS) can be presented in two forms: the standard `BEGIN CERTIFICATE` PEM header, and the OpenSSL-specific `BEGIN TRUSTED CERTIFICATE` PEM header.</span></span> <span data-ttu-id="39572-103">後者的語法允許其他設定導致 .NET Core 的類別發生相容性問題 <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="39572-103">The latter syntax allows for additional configuration that has caused compatibility issues with .NET Core's <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> class.</span></span> <span data-ttu-id="39572-104">`BEGIN TRUSTED CERTIFICATE`從 .NET Core 3.0 開始，連鎖引擎不再載入根憑證內容。</span><span class="sxs-lookup"><span data-stu-id="39572-104">`BEGIN TRUSTED CERTIFICATE` root certificate contents are no longer loaded by the chain engine starting in .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="39572-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="39572-105">Change description</span></span>

<span data-ttu-id="39572-106">之前， `BEGIN CERTIFICATE` 和語法都 `BEGIN TRUSTED CERTIFICATE` 是用來填入根信任清單。</span><span class="sxs-lookup"><span data-stu-id="39572-106">Previously, both the `BEGIN CERTIFICATE` and `BEGIN TRUSTED CERTIFICATE` syntaxes were used to populate the root trust list.</span></span> <span data-ttu-id="39572-107">如果 `BEGIN TRUSTED CERTIFICATE` 使用語法，並在檔案中指定了其他選項， <xref:System.Security.Cryptography.X509Certificates.X509Chain> 可能會報告已明確禁止鏈信任（ <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType> ）。</span><span class="sxs-lookup"><span data-stu-id="39572-107">If the `BEGIN TRUSTED CERTIFICATE` syntax was used and additional options were specified in the file, <xref:System.Security.Cryptography.X509Certificates.X509Chain> may have reported that the chain trust was explicitly disallowed (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span></span> <span data-ttu-id="39572-108">不過，如果憑證也以先前載入之檔案 `BEGIN CERTIFICATE` 中的語法指定，則允許鏈信任。</span><span class="sxs-lookup"><span data-stu-id="39572-108">However, if the certificate was also specified with the `BEGIN CERTIFICATE` syntax in a previously loaded file, the chain trust was allowed.</span></span>

<span data-ttu-id="39572-109">從 .NET Core 3.0 開始， `BEGIN TRUSTED CERTIFICATE` 將不會再讀取內容。</span><span class="sxs-lookup"><span data-stu-id="39572-109">Starting in .NET Core 3.0, `BEGIN TRUSTED CERTIFICATE` contents are no longer read.</span></span> <span data-ttu-id="39572-110">如果未透過標準語法指定憑證 `BEGIN CERTIFICATE` ，則會 <xref:System.Security.Cryptography.X509Certificates.X509Chain> 報告根不受信任（ <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType> ）。</span><span class="sxs-lookup"><span data-stu-id="39572-110">If the certificate is not also specified via a standard `BEGIN CERTIFICATE` syntax, the <xref:System.Security.Cryptography.X509Certificates.X509Chain> reports that the root is not trusted (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="39572-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="39572-111">Version introduced</span></span>

<span data-ttu-id="39572-112">3.0</span><span class="sxs-lookup"><span data-stu-id="39572-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="39572-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="39572-113">Recommended action</span></span>

<span data-ttu-id="39572-114">大部分的應用程式不會受到這項變更的影響，但因為許可權問題而無法看到兩個根憑證來源的應用程式，可能會在升級之後遇到未預期的 `UntrustedRoot` 錯誤。</span><span class="sxs-lookup"><span data-stu-id="39572-114">Most applications are unaffected by this change, but applications that cannot see both root certificate sources because of permissions problems may experience unexpected `UntrustedRoot` errors after upgrading.</span></span>

<span data-ttu-id="39572-115">許多 Linux 散發套件（或散發版本）會將根憑證寫入兩個位置：每個檔案一個憑證目錄，以及一個檔案串連。</span><span class="sxs-lookup"><span data-stu-id="39572-115">Many Linux distributions (or distros) write root certificates into two locations: a one-certificate-per-file directory, and a one-file concatenation.</span></span> <span data-ttu-id="39572-116">在某些散發版本上， `BEGIN TRUSTED CERTIFICATE` 當檔案串連使用標準語法時，每個檔案的單一憑證目錄會使用語法 `BEGIN CERTIFICATE` 。</span><span class="sxs-lookup"><span data-stu-id="39572-116">On some distros, the one-certificate-per-file directory uses the `BEGIN TRUSTED CERTIFICATE` syntax while the file concatenation uses the standard `BEGIN CERTIFICATE` syntax.</span></span> <span data-ttu-id="39572-117">請確定已將任何自訂根憑證新增為其中 `BEGIN CERTIFICATE` 至少一個位置，而且您的應用程式可以讀取這兩個位置。</span><span class="sxs-lookup"><span data-stu-id="39572-117">Ensure that any custom root certificates are added as `BEGIN CERTIFICATE` in at least one of these locations, and that both locations can be read by your application.</span></span>

<span data-ttu-id="39572-118">一般目錄是 */etc/ssl/certs/* ，而一般的串連檔案則是 */etc/ssl/cert.pem*。</span><span class="sxs-lookup"><span data-stu-id="39572-118">The typical directory is */etc/ssl/certs/* and the typical concatenated file is */etc/ssl/cert.pem*.</span></span> <span data-ttu-id="39572-119">使用命令 `openssl version -d` 來判斷平臺特定的根，這可能會與 */etc/ssl/* 不同。</span><span class="sxs-lookup"><span data-stu-id="39572-119">Use the command `openssl version -d` to determine the platform-specific root, which may differ from */etc/ssl/*.</span></span> <span data-ttu-id="39572-120">例如，在 Ubuntu 18.04 上，目錄是 */usr/lib/ssl/certs/* ，而檔案是 */usr/lib/ssl/cert.pem*。</span><span class="sxs-lookup"><span data-stu-id="39572-120">For example, on Ubuntu 18.04, the directory is */usr/lib/ssl/certs/* and the file is */usr/lib/ssl/cert.pem*.</span></span> <span data-ttu-id="39572-121">不過， */usr/lib/ssl/certs/* 是 */etc/ssl/certs/* 的符號，而且 */usr/lib/ssl/cert.pem*不存在。</span><span class="sxs-lookup"><span data-stu-id="39572-121">However, */usr/lib/ssl/certs/* is a symlink to */etc/ssl/certs/* and */usr/lib/ssl/cert.pem* does not exist.</span></span>

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

#### <a name="category"></a><span data-ttu-id="39572-122">類別</span><span class="sxs-lookup"><span data-stu-id="39572-122">Category</span></span>

<span data-ttu-id="39572-123">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="39572-123">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="39572-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="39572-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
