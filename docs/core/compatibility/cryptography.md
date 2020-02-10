---
title: 密碼編譯的重大變更
description: 列出 .NET Core 中與密碼編譯相關的重大變更。
ms.date: 09/20/2019
ms.openlocfilehash: fcef4b65245a5dd9219cbdbb548ca575a823a949
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093028"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="32a62-103">密碼編譯的重大變更</span><span class="sxs-lookup"><span data-stu-id="32a62-103">Cryptography breaking changes</span></span>

<span data-ttu-id="32a62-104">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="32a62-104">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="32a62-105">EnvelopedCms 預設為 AES-256 加密</span><span class="sxs-lookup"><span data-stu-id="32a62-105">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption)
- [<span data-ttu-id="32a62-106">RSAOpenSsl 金鑰產生的大小下限已增加</span><span class="sxs-lookup"><span data-stu-id="32a62-106">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased)
- [<span data-ttu-id="32a62-107">.NET Core 3.0 傾向于將 OpenSSL 1.1. x OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="32a62-107">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x)
- [<span data-ttu-id="32a62-108">Pkcs8PrivateKeyInfo 的函式中有更好的引數驗證</span><span class="sxs-lookup"><span data-stu-id="32a62-108">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor)

## <a name="net-core-30"></a><span data-ttu-id="32a62-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="32a62-109">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-30-preview-9"></a><span data-ttu-id="32a62-110">.NET Core 3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="32a62-110">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***
