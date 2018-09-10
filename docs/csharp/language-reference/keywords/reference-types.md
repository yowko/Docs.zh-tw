---
title: 參考類型 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: f99415fc9a2b728917cdf829ffb9e25823a824dd
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210902"
---
# <a name="reference-types-c-reference"></a>參考類型 (C# 參考)

C# 中有兩種類型：參考類型和實值類型。 參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。 使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。 使用實值型別時，每個變數都有自己的資料複本，因此對某一個變數進行的作業，不可能會影響其他變數 (但 in、ref 及 out 參數變數除外，請參閱 [in](in-parameter-modifier.md)、[ref](ref.md) 及 [out](out-parameter-modifier.md) 參數修飾詞)。

 下列關鍵字用來宣告參考類型：

- [class](class.md)

- [interface](interface.md)

- [delegate](delegate.md)

 C# 還提供下列內建參考類型：

- [dynamic](dynamic.md)

- [object](object.md)

- [string](string.md)

## <a name="see-also"></a>另請參閱

- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](index.md)
- [型別](types.md)
- [實值型別](value-types.md)