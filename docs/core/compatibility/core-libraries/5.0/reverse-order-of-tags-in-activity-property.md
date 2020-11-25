---
title: 重大變更：活動中的標記順序。標記已反轉
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中的主動標記現在會根據加入的順序，將專案儲存在清單中。
ms.date: 11/01/2020
ms.openlocfilehash: 1ff14dc1a4f7a0bf8cf9e79f3750b819f4d4a5ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760681"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a>活動中標記的順序。標記會反轉

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> 現在會根據加入的順序，將專案儲存在清單中，也就是第一個加入的專案會在清單中。 這項變更是為了符合 [OpenTelemetry 屬性規格](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes)而進行。

## <a name="change-description"></a>變更描述

在舊版的 .NET 中，會依其 <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> 加入的相反順序來儲存專案。 也就是說，第一個加入的專案是清單中的最後一個專案。 從 .NET 5.0 開始，會反轉專案的順序，而第一個加入的專案一律會在清單中的第一個專案。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

如果您的應用程式相依于 <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> 清單順序，而您要升級至 .net 5.0 或更新版本，您必須變更程式碼的這個部分。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
