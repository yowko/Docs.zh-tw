---
title: 在 '<name>' 中找不到具有適當簽名碼的可存取 'Main' 方法
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6760b931ceb2ad5c2c04169d664da8629badc487
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409409"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>在 '\<name>' 中找不到具有適當簽名碼的可存取 'Main' 方法
命令列應用程式必須已 `Sub Main` 定義。 `Main`必須宣告為 `Public Shared` 在類別中定義，或如同 `Public` 在模組中定義一樣。  
  
 **錯誤識別碼：** BC30737  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 定義專案的程式 `Public Sub Main` 。 `Shared`只有當您在類別內定義它時，才將它宣告為。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 程式的結構](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [程序](../../programming-guide/language-features/procedures/index.md)
