---
title: Interop 的重大變更
description: 列出 .NET Core 和 .NET 5.0 和更新版本 interop 中的重大變更。
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438041"
---
# <a name="interop-breaking-changes"></a>Interop 的重大變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
| [將 RCW 轉換成介面會擲回 `InterfaceIsIInspectable` PlatformNotSupportedException](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | 5.0 |
| [非 Windows 平臺上沒有任何/W 尾碼探查](#no-aw-suffix-probing-on-non-windows-platforms) | 5.0 |
| [WinRT 的內建支援已從 .NET 移除](#built-in-support-for-winrt-is-removed-from-net) | 5.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
