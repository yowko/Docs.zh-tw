---
title: '如何使用指標來複製位元組陣列-c # 程式設計手冊'
description: 瞭解如何使用指標來複製位元組陣列。 請參閱程式碼範例和其他可用的資源。
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 70ab1441d25ea69afb2244bd94bd404a3e32838d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381784"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>如何使用指標來複製位元組陣列（c # 程式設計手冊）

下列範例會使用指標，以將位元組從某個陣列複製到另一個陣列。

這個範例會使用 [unsafe](../../language-reference/keywords/unsafe.md) 關鍵字，讓您可以使用 `Copy` 方法中的指標。 [fixed](../../language-reference/keywords/fixed-statement.md) 陳述式用來宣告來源和目的陣列的指標。 `fixed` 陳述式會將來源和目的陣列的位置「釘選」** 到記憶體中，讓記憶體回收不會移動它們。 `fixed` 區塊完成時，會取消釘選陣列的記憶體區塊。 因為這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，所以必須使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項進行編譯。

這個範例會使用索引 (而不是第二個非受控指標) 來存取這兩個陣列的項目。 `pSource` 和 `pTarget` 指標的宣告會釘選到陣列。 這項功能從 C# 7.3 開始可供使用。

## <a name="example"></a>範例

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [Unsafe 程式碼和指標](index.md)
- [-unsafe (C# 編譯器選項)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
