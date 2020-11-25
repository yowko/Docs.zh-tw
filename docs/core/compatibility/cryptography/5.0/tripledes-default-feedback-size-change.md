---
title: 重大變更： TripleDES 建立之實例的預設 FeedbackSize 值。建立變更
description: '深入瞭解 .NET 5.0 中的重大變更，其中 TripleDES 所傳回之 TripleDES 實例上 FeedbackSize 屬性的預設值。 Create ( # A1 已從64變更為8。'
ms.date: 10/16/2020
ms.openlocfilehash: 4179da17bf2e5cc5fcc7d64d83ba92119f912042
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760742"
---
# <a name="default-feedbacksize-value-for-instances-created-by-tripledescreate-changed"></a>TripleDES 建立之實例的預設 FeedbackSize 值。建立變更

<xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=nameWithType>從傳回的實例上，屬性的預設值 <xref:System.Security.Cryptography.TripleDES> <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> 已從64變更為8，以簡化 .NET Framework 的遷移。 除非直接在呼叫端程式碼中使用這個屬性，否則此屬性只會在 <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode> 屬性為時使用 <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> 。

針對 <xref:System.Security.Cryptography.CipherMode.CFB> 5.0 RC1 版本，第一次將模式的支援新增至 .net，因此只有 .net 5.0 RC1 和 .net 5.0 RC2 應用程式才會受到這項變更的影響。

## <a name="change-description"></a>變更描述

在 .NET Core 和舊版的 .NET 5.0 發行前版本中， `TripleDES.Create().FeedbackSize` 預設值是64。 從 .NET 5.0 的 RTM 版本開始， `TripleDES.Create().FeedbackSize` 預設值為8。

## <a name="reason-for-change"></a>變更的原因

在 .NET Framework 中， <xref:System.Security.Cryptography.TripleDES> 基類會將的值預設為 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 64，但類別會將 <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> 預設值覆寫為8。 當 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性在2.0 版中引進 .Net Core 時，會保留相同的行為。 不過，在 .NET Framework 中，會傳回的 <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> 實例 <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> ，因此演算法 factory 的預設值為8。 若是 .NET Core 和 .NET 5 +，演算法處理站會傳回非公用的執行，而在目前為止，預設值為64。

將 <xref:System.Security.Cryptography.TripleDES> 實數值型別的 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 值變更為8可讓針對指定加密模式的 .NET Framework 寫入的應用程式， <xref:System.Security.Cryptography.CipherMode.CFB> 但未明確指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性，以便在 .net 5 上繼續運作。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

當符合下列條件時，在 .NET 5.0 的 RC1 或 RC2 版本中加密或解密資料的應用程式會使用 CFB64 來執行此作業：

- 的 <xref:System.Security.Cryptography.TripleDES> 實例 <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=nameWithType> 。
- 使用的預設值 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode>屬性設定為 <xref:System.Security.Cryptography.CipherMode.CFB?displayProperty=nameWithType> 。

若要維護這種行為，請將 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性指派給 `64` 。

並非所有 `TripleDES` 的實施都使用相同的預設值 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 。 如果您 <xref:System.Security.Cryptography.CipherMode.CFB> 在實例上使用加密模式，建議 <xref:System.Security.Cryptography.TripleDES> 您一律明確指派 <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize> 屬性值。

```csharp
TripleDES cipher = TripleDES.Create();
cipher.Mode = CipherMode.CFB;
// Explicitly set the FeedbackSize for CFB to control between CFB8 and CFB64.
cipher.FeedbackSize = 8;
```

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.TripleDES.Create?displayProperty=fullName>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Security.Cryptography.TripleDES.Create`
- `P:System.Security.Cryptography.SymmetricAlgorithm.FeedbackSize`

### Category

- Cryptography

-->
