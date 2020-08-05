---
title: 密碼編譯的重大變更
description: 列出 .NET Core 中的密碼編譯相關的重大變更。
ms.date: 04/22/2020
ms.openlocfilehash: 34098027c4cbe5e5fb31a22d981af706e07cb7da
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556018"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="37ec8-103">密碼編譯的重大變更</span><span class="sxs-lookup"><span data-stu-id="37ec8-103">Cryptography breaking changes</span></span>

<span data-ttu-id="37ec8-104">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="37ec8-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="37ec8-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="37ec8-105">Breaking change</span></span> | <span data-ttu-id="37ec8-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="37ec8-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="37ec8-107">Linux 上不再支援開始信任的憑證語法</span><span class="sxs-lookup"><span data-stu-id="37ec8-107">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="37ec8-108">3.0</span><span class="sxs-lookup"><span data-stu-id="37ec8-108">3.0</span></span> |
| [<span data-ttu-id="37ec8-109">EnvelopedCms 預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="37ec8-109">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="37ec8-110">3.0</span><span class="sxs-lookup"><span data-stu-id="37ec8-110">3.0</span></span> |
| [<span data-ttu-id="37ec8-111">RSAOpenSsl 金鑰產生的大小下限已增加</span><span class="sxs-lookup"><span data-stu-id="37ec8-111">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="37ec8-112">3.0</span><span class="sxs-lookup"><span data-stu-id="37ec8-112">3.0</span></span> |
| [<span data-ttu-id="37ec8-113">.NET Core 3.0 傾向于將 OpenSSL 1.1. x OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="37ec8-113">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="37ec8-114">3.0</span><span class="sxs-lookup"><span data-stu-id="37ec8-114">3.0</span></span> |
| [<span data-ttu-id="37ec8-115">遵守 SignedCms 的布林值參數。 ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="37ec8-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="37ec8-116">2.1</span><span class="sxs-lookup"><span data-stu-id="37ec8-116">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="37ec8-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="37ec8-117">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="37ec8-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="37ec8-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
