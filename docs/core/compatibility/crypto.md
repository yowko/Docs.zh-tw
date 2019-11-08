---
title: 密碼編譯的重大變更，版本2.2 至 3.0-.NET Core
description: 列出 .NET Core、ASP.NET Core 和 EF Core 版本2.2 到3.0 版的重大變更。
ms.date: 09/10/2019
ms.openlocfilehash: e8b2894e6988c0b475e45c6d5602a7f54943f3ed
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739430"
---
# <a name="breaking-changes-for-migration-from-version-22-to-30"></a><span data-ttu-id="006e4-103">從2.2 版遷移至3.0 的突破性變更</span><span class="sxs-lookup"><span data-stu-id="006e4-103">Breaking changes for migration from Version 2.2 to 3.0</span></span>

<span data-ttu-id="006e4-104">如果您要從版本2.2 遷移至 .NET Core 的3.0 版、ASP.NET Core 或 EF Core，請參閱下列主題，以取得可能會影響應用程式的重大變更：</span><span class="sxs-lookup"><span data-stu-id="006e4-104">If you are migrating from version 2.2 to version 3.0 of .NET Core, ASP.NET Core, or EF Core, review the following topics for breaking changes that may affect your app:</span></span>

## <a name="corefx"></a><span data-ttu-id="006e4-105">CoreFx</span><span class="sxs-lookup"><span data-stu-id="006e4-105">CoreFx</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/floating-point-changes.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/ziparchiveentry-and-inconsistent-entry-sizes.md)]

## <a name="cryptography"></a><span data-ttu-id="006e4-106">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="006e4-106">Cryptography</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/net-core-3-0-prefers-openssl-1-1-x.md)]

## <a name="globalization"></a><span data-ttu-id="006e4-107">全球化</span><span class="sxs-lookup"><span data-stu-id="006e4-107">Globalization</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/c-locale-maps-to-invariant-locale.md)]

## <a name="visual-basic"></a><span data-ttu-id="006e4-108">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="006e4-108">Visual Basic</span></span>

[!INCLUDE[vbNewLine is obsolete](~/includes/core-changes/visualbasic/vbnewline-is-obsolete.md)]

## <a name="entity-framework-core"></a><span data-ttu-id="006e4-109">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="006e4-109">Entity Framework Core</span></span>

[<span data-ttu-id="006e4-110">Entity Framework Core 的重大變更</span><span class="sxs-lookup"><span data-stu-id="006e4-110">Entity Framework Core breaking changes</span></span>](/ef/core/what-is-new/ef-core-3.0/breaking-changes)
