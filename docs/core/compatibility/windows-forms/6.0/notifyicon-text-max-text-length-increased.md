---
title: 重大變更： NotifyIcon。文字長度上限增加
description: 瞭解 .NET 6.0 中的重大變更，其中 NotifyIcon 的文字長度上限已增加。
ms.date: 01/19/2021
ms.openlocfilehash: 0029556f3ec2795fb079575b329e7fbd187d486f
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98617988"
---
# <a name="notifyicontext-maximum-text-length-increased"></a>NotifyIcon。文字長度上限增加

屬性所允許的最大文字長度（ <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 從63增加到127）。

## <a name="change-description"></a>變更描述

在先前的 .NET 版本中，屬性允許的最大文字長度 <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 為63個字元。 從 .NET 6.0 開始，允許的文字長度上限是127個字元。 在任何版本中， <xref:System.ArgumentException> 當您嘗試設定的值超過限制時，就會擲回。

## <a name="reason-for-change"></a>變更的原因

允許的文字長度上限已增加，使其與 [基礎 WINDOWS API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080)對齊。 Windows API 在 Windows 2000 中已更新，但由於相容性的緣故，此屬性的大小限制未在 .NET Framework 中更新。

## <a name="version-introduced"></a>引進的版本

.NET 6.0 Preview 1

## <a name="recommended-action"></a>建議的動作

如有必要，請檢查您的程式碼，並放寬任何現有的防護條件。

## <a name="affected-apis"></a>受影響的 API

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
