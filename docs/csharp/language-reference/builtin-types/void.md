---
description: 深入瞭解 C 中的 void 關鍵字#
title: 'void-c # 參考'
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: c0282a1eafd03506cd9ff05b209b2a27af216b2f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118152"
---
# <a name="void-c-reference"></a>void (c # 參考) 

您可以使用 `void` 做為 [方法](../../programming-guide/classes-and-structs/methods.md) 的傳回類型 (或 [區域函數](../../programming-guide/classes-and-structs/local-functions.md)) 來指定方法不會傳回值。

[!code-csharp[void method](snippets/VoidType.cs#VoidExample)]

您也可以使用 `void` 做為參考型別來宣告未知類型的指標。 如需詳細資訊，請參閱[指標類型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。

您無法使用 `void` 做為變數的類型。

## <a name="see-also"></a>另請參閱

- [C# 參考資料](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
