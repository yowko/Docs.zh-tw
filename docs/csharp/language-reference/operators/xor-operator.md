---
title: ^ 運算子 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 16419342fec9d6c9845e19e434787c5e4f5a5b12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632242"
---
# <a name="-operator-c-reference"></a>^ 運算子 (C# 參考)

整數型別和 `bool` 會預先定義二元 `^` 運算子。 對於整數型別，`^` 會計算其運算元的位元互斥 OR。 對於 `bool` 運算元，`^` 會計算其運算元的邏輯位元互斥 OR；亦即，如果且唯有在正好其中一個運算元是 `true` 時，結果會是 `true`。

## <a name="remarks"></a>備註

使用者定義型別可以多載 `^` 運算子 (請參閱 [operator](../keywords/operator.md))。 整數類資料類型上的作業通常允許用於列舉型別。

## <a name="example"></a>範例

[!code-csharp[csRefOperators#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#30)]

前一個範例中的 `0xf8 ^ 0x3f` 計算會執行下列兩個二進位值的位元互斥 OR，這兩個值對應於十六進位值 F8 和 3F：

`1111 1000`

`0011 1111`

互斥 OR 的結果是 `1100 0111`，這是十六進位的 C7。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
