---
title: 重大變更：單一檔案發佈格式的元件相關 API 行為變更
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中元件檔案位置的多個相關 Api 在以單一檔案發行格式叫用時，會有行為變更。
ms.date: 11/01/2020
ms.openlocfilehash: d77e30318040c8298065073a41caab56f2ca3875
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760706"
---
# <a name="assembly-related-api-behavior-changes-for-single-file-publishing-format"></a>單一檔案發佈格式的元件相關 API 行為變更

多個與元件檔案位置相關的 Api 在以單一檔案發行格式叫用時，會有行為變更。

## <a name="change-description"></a>變更描述

在 .NET 5.0 和更新版本的單一檔案發行中，配套的元件會從記憶體載入，而不是解壓縮至磁片。 針對單一檔案發佈的應用程式，這表示某些位置相關的 Api 會在 .NET 5.0 和更新版本上，傳回與舊版 .NET 不同的值。 變更如下所示：

| API | 舊版 | .NET 5.0 和更新版本 |
| - | - | - |
| <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> | 傳回解壓縮的 DLL 檔案路徑 | 針對配套的元件傳回空字串 |
| <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> | 傳回解壓縮的 DLL 檔案路徑 | 針對配套的元件擲回例外狀況 |
| <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType> | `null`針對配套的元件傳回 | 針對配套的元件擲回例外狀況 |
| `Environment.GetCommandLineArgs()[0]` | 值為進入點 DLL 的名稱 | 值是主機可執行檔的名稱 |
| <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> | 值是暫存的解壓縮目錄 | 值是主機可執行檔的包含目錄 |

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

以單一檔案的形式發行時，請避免元件的檔案位置相依性。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.GetFile(System.String)?displayProperty=nameWithType>
- <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>
- <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.Location`
- `P:System.Reflection.Assembly.CodeBase`
- `M:System.Reflection.Assembly.GetFile(System.String)`
- `M:System.Environment.GetCommandLineArgs`
- `P:System.AppContext.BaseDirectory`

-->
