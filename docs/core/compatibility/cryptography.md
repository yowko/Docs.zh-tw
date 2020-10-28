---
title: 密碼編譯的重大變更
description: 列出 .NET Core 中的密碼編譯相關的重大變更。
ms.date: 04/22/2020
ms.openlocfilehash: b755876624a7709cfe08b5993655e78be9f8e1f2
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888605"
---
# <a name="cryptography-breaking-changes"></a>密碼編譯的重大變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
| [TripleDES 建立之實例的預設 FeedbackSize 值。建立變更](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | 5.0 |
| [不支援具現化密碼編譯抽象概念的預設實值](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | 5.0 |
| [Linux 上適用于 .NET 的預設 TLS 加密套件](#default-tls-cipher-suites-for-net-on-linux) | 5.0 |
| [Blazor WebAssembly 不支援的密碼編譯 Api](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | 5.0 |
| [在功能上，加密功能僅限初始化](#systemsecuritycryptographyoid-is-functionally-init-only) | 5.0 |
| [Linux 上不再支援開始受信任的憑證語法](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3.0 |
| [EnvelopedCms 預設為 AES-256 加密](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [RSAOpenSsl 金鑰產生的大小下限已增加](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [.NET Core 3.0 偏好將 OpenSSL 1.1. x OpenSSL 1.0. x](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [CryptoStream 只會在寫入時轉換最終區塊](#cryptostreamdispose-transforms-final-block-only-when-writing) | 3.0 |
| [已遵守 SignedCms 的布林值參數。 ComputeSignature](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

**_

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

_*_

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

_*_

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

_**
