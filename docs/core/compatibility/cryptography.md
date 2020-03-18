---
title: 加密中斷更改
description: 列出 .NET Core 中與密碼學相關的重大更改。
ms.date: 02/10/2020
ms.openlocfilehash: c25eefa8e3ee01ed7a1df4ec4aa9225f2c347a4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449207"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="01208-103">加密中斷更改</span><span class="sxs-lookup"><span data-stu-id="01208-103">Cryptography breaking changes</span></span>

<span data-ttu-id="01208-104">此頁面將記錄以下重大更改：</span><span class="sxs-lookup"><span data-stu-id="01208-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="01208-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="01208-105">Breaking change</span></span> | <span data-ttu-id="01208-106">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="01208-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="01208-107">信封Cm預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="01208-107">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="01208-108">3.0</span><span class="sxs-lookup"><span data-stu-id="01208-108">3.0</span></span> |
| [<span data-ttu-id="01208-109">RSAOpenSsl 金鑰生成的最低大小已增加</span><span class="sxs-lookup"><span data-stu-id="01208-109">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="01208-110">3.0</span><span class="sxs-lookup"><span data-stu-id="01208-110">3.0</span></span> |
| [<span data-ttu-id="01208-111">.NET 核心 3.0 更喜歡 OpenSSL 1.1.x 到 OpenSSL 1.0.x</span><span class="sxs-lookup"><span data-stu-id="01208-111">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="01208-112">3.0</span><span class="sxs-lookup"><span data-stu-id="01208-112">3.0</span></span> |
| [<span data-ttu-id="01208-113">在 Pkcs8PrivateKeyInfo 建構函式中更好的參數驗證</span><span class="sxs-lookup"><span data-stu-id="01208-113">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="01208-114">3.0</span><span class="sxs-lookup"><span data-stu-id="01208-114">3.0</span></span> |
| [<span data-ttu-id="01208-115">簽名Cms的布林參數.計算簽名得到尊重</span><span class="sxs-lookup"><span data-stu-id="01208-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="01208-116">2.1</span><span class="sxs-lookup"><span data-stu-id="01208-116">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="01208-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="01208-117">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="01208-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="01208-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
