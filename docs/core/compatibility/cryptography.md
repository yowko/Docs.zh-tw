---
title: 密碼編譯的重大變更
description: 列出 .NET Core 中的密碼編譯相關的重大變更。
ms.date: 02/10/2020
ms.openlocfilehash: c25eefa8e3ee01ed7a1df4ec4aa9225f2c347a4d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449207"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="9e1e3-103">密碼編譯的重大變更</span><span class="sxs-lookup"><span data-stu-id="9e1e3-103">Cryptography breaking changes</span></span>

<span data-ttu-id="9e1e3-104">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="9e1e3-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9e1e3-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="9e1e3-105">Breaking change</span></span> | <span data-ttu-id="9e1e3-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9e1e3-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9e1e3-107">EnvelopedCms 預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="9e1e3-107">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="9e1e3-108">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1e3-108">3.0</span></span> |
| [<span data-ttu-id="9e1e3-109">RSAOpenSsl 金鑰產生的大小下限已增加</span><span class="sxs-lookup"><span data-stu-id="9e1e3-109">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="9e1e3-110">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1e3-110">3.0</span></span> |
| [<span data-ttu-id="9e1e3-111">.NET Core 3.0 傾向于將 OpenSSL 1.1. x OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="9e1e3-111">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="9e1e3-112">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1e3-112">3.0</span></span> |
| [<span data-ttu-id="9e1e3-113">Pkcs8PrivateKeyInfo 的函式中有更好的引數驗證</span><span class="sxs-lookup"><span data-stu-id="9e1e3-113">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="9e1e3-114">3.0</span><span class="sxs-lookup"><span data-stu-id="9e1e3-114">3.0</span></span> |
| [<span data-ttu-id="9e1e3-115">遵守 SignedCms 的布林值參數。 ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="9e1e3-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="9e1e3-116">2.1</span><span class="sxs-lookup"><span data-stu-id="9e1e3-116">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="9e1e3-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9e1e3-117">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="9e1e3-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9e1e3-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
