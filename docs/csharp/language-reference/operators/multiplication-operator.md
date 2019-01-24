---
title: '* 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333729"
---
# <a name="-operator-c-reference"></a>* 運算子 (C# 參考)

乘法運算子 (`*`)，它會計算其運算元的乘積。 所有數字類型都有預先定義的乘法運算子。

`*` 也可做為取值運算子，其允許讀取和寫入指標中。

## <a name="remarks"></a>備註

`*` 運算子也可以用來宣告指標類型，並對指標取值 (Dereference)。 此運算子只可用於 Unsafe 內容中，並透過使用 [unsafe](../keywords/unsafe.md) 關鍵字及需要 [/unsafe](../compiler-options/unsafe-compiler-option.md) 編譯器選項來表示。  取值運算子也稱作間接運算子。

使用者定義型別可以多載二進位 `*` 運算子 (請參閱 [operator](../keywords/operator.md))。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。

## <a name="example"></a>範例

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a>範例

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [Unsafe 程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)
- [C# 運算子](index.md)