---
title: 密碼編譯的重大變更
description: 列出 .NET Core 中的密碼編譯相關的重大變更。
ms.date: 04/22/2020
ms.openlocfilehash: f7d580938fb7620728b8ff7f67412c9f5bbbb6c3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557995"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="d3969-103">密碼編譯的重大變更</span><span class="sxs-lookup"><span data-stu-id="d3969-103">Cryptography breaking changes</span></span>

<span data-ttu-id="d3969-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="d3969-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d3969-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="d3969-105">Breaking change</span></span> | <span data-ttu-id="d3969-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="d3969-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="d3969-107">在功能上，加密功能僅限初始化</span><span class="sxs-lookup"><span data-stu-id="d3969-107">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="d3969-108">5.0</span><span class="sxs-lookup"><span data-stu-id="d3969-108">5.0</span></span> |
| [<span data-ttu-id="d3969-109">Linux 上不再支援開始受信任的憑證語法</span><span class="sxs-lookup"><span data-stu-id="d3969-109">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="d3969-110">3.0</span><span class="sxs-lookup"><span data-stu-id="d3969-110">3.0</span></span> |
| [<span data-ttu-id="d3969-111">EnvelopedCms 預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="d3969-111">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="d3969-112">3.0</span><span class="sxs-lookup"><span data-stu-id="d3969-112">3.0</span></span> |
| [<span data-ttu-id="d3969-113">RSAOpenSsl 金鑰產生的大小下限已增加</span><span class="sxs-lookup"><span data-stu-id="d3969-113">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="d3969-114">3.0</span><span class="sxs-lookup"><span data-stu-id="d3969-114">3.0</span></span> |
| [<span data-ttu-id="d3969-115">.NET Core 3.0 偏好將 OpenSSL 1.1. x OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="d3969-115">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="d3969-116">3.0</span><span class="sxs-lookup"><span data-stu-id="d3969-116">3.0</span></span> |
| [<span data-ttu-id="d3969-117">已遵守 SignedCms 的布林值參數。 ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="d3969-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="d3969-118">2.1</span><span class="sxs-lookup"><span data-stu-id="d3969-118">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="d3969-119">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="d3969-119">.NET 5.0</span></span>

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="d3969-120">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d3969-120">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="d3969-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d3969-121">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
