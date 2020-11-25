---
title: 重大變更：巢狀型別的硬體內部 IsSupported 檢查可能不同
description: 瞭解檢查 X64 的核心 .NET 程式庫中的 .NET 5.0 重大變更。硬體內建函式的 IsSupported 現在可能會產生不同的結果。
ms.date: 11/01/2020
ms.openlocfilehash: 9acef15860de76a9743621cb4c5edba5aac3931c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760719"
---
# <a name="hardware-intrinsic-issupported-checks-may-differ-for-nested-types"></a>巢狀型別的硬體內部 IsSupported 檢查可能不同

檢查 `<Isa>.X64.IsSupported` （其中 `<Isa>` 參考命名空間中的類別 <xref:System.Runtime.Intrinsics.X86?displayProperty=nameWithType> ），現在可能會產生與舊版 .net 不同的結果。

> [!TIP]
> *ISA* 代表業界標準架構。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="change-description"></a>變更描述

在舊版的 .NET 中，某些硬體內 <xref:System.Runtime.Intrinsics.X86> 建類型（例如）不會 <xref:System.Runtime.Intrinsics.X86.Aes?displayProperty=nameWithType> 公開嵌套 `X64` 類別。 針對這些類型，呼叫會 `<Isa>.X64.IsSupported` 解析為的 `IsSupported` 父類別的嵌套類別上的屬性 `X64` `<Isa>` 。 這表示即使傳回，屬性也可以傳回 `true` `<Isa>.IsSupported` `false` 。

在 .NET 5.0 和更新版本中，所有 <xref:System.Runtime.Intrinsics.X86> 類型都會公開 `X64` 適當報告支援的嵌套類別。 這可確保一般階層保持正確，而且如果 `<Isa>.X64.IsSupported` 是 `true` ，則 `<Isa>.IsSupported` 也可以假設為 `true` 。

## <a name="reason-for-change"></a>變更的原因

它的目標是 `<Isa>.X64.IsSupported` ，如果是 `true` ，也會 `<Isa>.IsSupported` 隱含為 `true` 。 不過，由於成員解析在 c # 中的運作方式，沒有嵌套類別的類別會 `X64` 公開一種情況，而這種情況不一定會發生，而且會導致使用者程式碼中的 bug。

## <a name="recommended-action"></a>建議的動作

如有必要，請調整檢查 `IsSupported` 以檢查適當 ISA 的程式碼。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.Intrinsics.X86.Aes.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Avx2.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Fma.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Pclmulqdq.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Sse3.X64.IsSupported`
- `P:System.Runtime.Intrinsics.X86.Ssse3.X64.IsSupported`

-->
