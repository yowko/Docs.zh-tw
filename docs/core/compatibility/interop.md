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
# <a name="interop-breaking-changes"></a><span data-ttu-id="9fc16-103">Interop 的重大變更</span><span class="sxs-lookup"><span data-stu-id="9fc16-103">Interop breaking changes</span></span>

<span data-ttu-id="9fc16-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="9fc16-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9fc16-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="9fc16-105">Breaking change</span></span> | <span data-ttu-id="9fc16-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9fc16-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9fc16-107">將 RCW 轉換成介面會擲回 `InterfaceIsIInspectable` PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="9fc16-107">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | <span data-ttu-id="9fc16-108">5.0</span><span class="sxs-lookup"><span data-stu-id="9fc16-108">5.0</span></span> |
| [<span data-ttu-id="9fc16-109">非 Windows 平臺上沒有任何/W 尾碼探查</span><span class="sxs-lookup"><span data-stu-id="9fc16-109">No A/W suffix probing on non-Windows platforms</span></span>](#no-aw-suffix-probing-on-non-windows-platforms) | <span data-ttu-id="9fc16-110">5.0</span><span class="sxs-lookup"><span data-stu-id="9fc16-110">5.0</span></span> |
| [<span data-ttu-id="9fc16-111">WinRT 的內建支援已從 .NET 移除</span><span class="sxs-lookup"><span data-stu-id="9fc16-111">Built-in support for WinRT is removed from .NET</span></span>](#built-in-support-for-winrt-is-removed-from-net) | <span data-ttu-id="9fc16-112">5.0</span><span class="sxs-lookup"><span data-stu-id="9fc16-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="9fc16-113">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="9fc16-113">.NET 5.0</span></span>

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
