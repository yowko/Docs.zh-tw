---
title: 參考型別 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: 4b3b1d5b27c3f6a88ce752243ab2d1389b168f0e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634065"
---
# <a name="reference-types-c-reference"></a>參考型別 (C# 參考)

C# 中有兩種型別：參考型別和實值型別。 參考型別的變數會儲存期資料 (物件) 的參考，而實值型別的變數則會直接包含其資料。 使用參考型別時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。 使用實值型別時，每個變數都有自己的資料複本，因此對某一個變數進行的作業，不可能會影響其他變數 (但 in、ref 及 out 參數變數除外，請參閱 [in](in-parameter-modifier.md)、[ref](ref.md) 及 [out](out-parameter-modifier.md) 參數修飾詞)。

 下列關鍵字用來宣告參考型別：

- [class](class.md)

- [interface](interface.md)

- [delegate](delegate.md)

 C# 還提供下列內建參考型別：

- [dynamic](dynamic.md)

- [object](object.md)

- [string](string.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](index.md)
- [型別](types.md)
- [實值型別](value-types.md)
