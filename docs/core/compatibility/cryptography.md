---
title: 密碼編譯的重大變更
description: 列出 .NET Core 中的密碼編譯相關的重大變更。
ms.date: 04/22/2020
ms.openlocfilehash: 6f37e5caacadc276562e63a728162c6b26f2e435
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159545"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="a6a96-103">密碼編譯的重大變更</span><span class="sxs-lookup"><span data-stu-id="a6a96-103">Cryptography breaking changes</span></span>

<span data-ttu-id="a6a96-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="a6a96-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="a6a96-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="a6a96-105">Breaking change</span></span> | <span data-ttu-id="a6a96-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a6a96-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="a6a96-107">不支援具現化密碼編譯抽象概念的預設實值</span><span class="sxs-lookup"><span data-stu-id="a6a96-107">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | <span data-ttu-id="a6a96-108">5.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-108">5.0</span></span> |
| [<span data-ttu-id="a6a96-109">Linux 上適用于 .NET 的預設 TLS 加密套件</span><span class="sxs-lookup"><span data-stu-id="a6a96-109">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="a6a96-110">5.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-110">5.0</span></span> |
| [<span data-ttu-id="a6a96-111">Blazor WebAssembly 不支援的密碼編譯 Api</span><span class="sxs-lookup"><span data-stu-id="a6a96-111">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="a6a96-112">5.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-112">5.0</span></span> |
| [<span data-ttu-id="a6a96-113">在功能上，加密功能僅限初始化</span><span class="sxs-lookup"><span data-stu-id="a6a96-113">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="a6a96-114">5.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-114">5.0</span></span> |
| [<span data-ttu-id="a6a96-115">Linux 上不再支援開始受信任的憑證語法</span><span class="sxs-lookup"><span data-stu-id="a6a96-115">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="a6a96-116">3.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-116">3.0</span></span> |
| [<span data-ttu-id="a6a96-117">EnvelopedCms 預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="a6a96-117">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="a6a96-118">3.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-118">3.0</span></span> |
| [<span data-ttu-id="a6a96-119">RSAOpenSsl 金鑰產生的大小下限已增加</span><span class="sxs-lookup"><span data-stu-id="a6a96-119">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="a6a96-120">3.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-120">3.0</span></span> |
| [<span data-ttu-id="a6a96-121">.NET Core 3.0 偏好將 OpenSSL 1.1. x OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="a6a96-121">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="a6a96-122">3.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-122">3.0</span></span> |
| [<span data-ttu-id="a6a96-123">CryptoStream 只會在寫入時轉換最終區塊</span><span class="sxs-lookup"><span data-stu-id="a6a96-123">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="a6a96-124">3.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-124">3.0</span></span> |
| [<span data-ttu-id="a6a96-125">已遵守 SignedCms 的布林值參數。 ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="a6a96-125">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="a6a96-126">2.1</span><span class="sxs-lookup"><span data-stu-id="a6a96-126">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="a6a96-127">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="a6a96-127">.NET 5.0</span></span>

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

***

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

***

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="a6a96-128">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a6a96-128">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="a6a96-129">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a6a96-129">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
