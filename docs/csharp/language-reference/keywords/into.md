---
description: into - C# 參考
title: into - C# 參考
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: 4712a6906195c5d8bc09c7b734dba0df4d2b08c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134519"
---
# <a name="into-c-reference"></a>into (C# 參考)

`into` 內容關鍵字可以用來建立暫時識別碼，以將 [group](group-clause.md)、[join](join-clause.md) 或 [select](select-clause.md) 子句結果儲存至新的識別碼。 這個識別碼本身可以是其他查詢命令的產生器。 用於 `group` 或 `select` 子句時，使用 new 識別碼有時稱為「接續」**。

## <a name="example"></a>範例

下列範例示範如何使用 `into` 關鍵字啟用推斷類型為 `IGrouping` 的暫時識別碼 `fruitGroup`。 使用識別碼，即可在每個群組上叫用 <xref:System.Linq.Enumerable.Count%2A> 方法，並且只選取包含兩個以上單字的群組。

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

只有在您想要對每個群組執行其他查詢作業時，才需要在 `group` 子句中使用 `into`。 如需詳細資訊，請參閱 [group 子句](group-clause.md)。

如需在 `join` 子句中使用 `into` 的範例，請參閱 [join 子句](join-clause.md)。

## <a name="see-also"></a>另請參閱

- [LINQ)  (查詢關鍵字 ](query-keywords.md)
- [C# 中的 LINQ](../../linq/index.md)
- [group 子句](group-clause.md)
