---
description: '#nullable-c # 參考'
title: '#nullable-c # 參考'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099458"
---
# <a name="nullable-c-reference"></a>#nullable (c # 參考) 

預處理器指示詞會 `#nullable` 設定 *可為 null 注釋內容* 和 *可為 null 的警告內容*。 這個指示詞會控制可為 null 的注釋是否有效果，以及是否提供可 null 性警告。 每個內容都已 *停用* 或 *啟用*。

這兩個內容可以在專案層級指定， (在 c # 原始程式碼) 之外。 指示詞 `#nullable` 會控制注釋和警告內容，並優先于專案層級的設定。 指示詞會設定) 它控制的 (內容，直到另一個指示詞覆寫它，或直到原始程式檔結束為止。

指示詞的效果如下所示：

- `#nullable disable`：將可為 null 的注釋和警告內容設定為 *停用*。
- `#nullable enable`：將可為 null 的注釋和警告內容設定為 *已啟用*。
- `#nullable restore`：將可為 null 的注釋和警告內容還原至專案設定。
- `#nullable disable annotations`：將可為 null 注釋內容設定為 *停用*。
- `#nullable enable annotations`：將可為 null 注釋內容設定為 *已啟用*。
- `#nullable restore annotations`：將可為 null 注釋內容還原至專案設定。
- `#nullable disable warnings`：將可為 null 的警告內容設定為 *停用*。
- `#nullable enable warnings`：將可為 null 的警告內容設定為 *已啟用*。
- `#nullable restore warnings`：將可為 null 警告內容還原至專案設定。

## <a name="see-also"></a>另請參閱

- [C # 參考](../index.md)
- [C # 程式設計指南](../../programming-guide/index.md)
- [C # 預處理器指示詞](./index.md)
