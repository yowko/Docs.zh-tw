---
title: 在 '<name>' 中找不到具有適當簽名碼的可存取 'Main' 方法
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: e1f95484a153bdcac9543508b7f2708dc6b7d942
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160037"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>BC30737：在 ' ' 中找不到具有適當簽章的可存取 ' Main ' 方法 \<name>

命令列應用程式必須已 `Sub Main` 定義。 `Main` 必須宣告為 `Public Shared` 在類別中定義，或在 `Public` 模組中定義。

 **錯誤識別碼：** BC30737

## <a name="to-correct-this-error"></a>更正這個錯誤

- 定義專案的程式 `Public Sub Main` 。 將它宣告為 `Shared` ，而且只有在您于類別內定義它時才會進行宣告。

## <a name="see-also"></a>另請參閱

- [Visual Basic 程式的結構](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [程序](../../programming-guide/language-features/procedures/index.md)
