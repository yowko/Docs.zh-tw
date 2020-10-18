---
title: 必須是宣告
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 2755f5afcb96ca7a6c4d140908649390dd66d571
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162696"
---
# <a name="bc30188-declaration-expected"></a>BC30188：需要宣告

Nondeclarative 語句（例如指派或迴圈語句）發生在任何程式之外。 在程式之外只允許宣告。

 或者，在不使用宣告關鍵字（例如或）的情況下宣告程式設計項目 `Dim` `Const` 。

 **錯誤識別碼：** BC30188

## <a name="to-correct-this-error"></a>更正這個錯誤

- 將 nondeclarative 語句移至程式的主體。

- 使用適當的宣告關鍵字來開始宣告。

- 確定宣告關鍵字未拼寫錯誤。

## <a name="see-also"></a>另請參閱

- [程序](../../programming-guide/language-features/procedures/index.md)
- [Dim 陳述式](../statements/dim-statement.md)
