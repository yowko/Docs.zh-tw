---
title: 在 '<name>' 中找不到具有適當簽名碼的可存取 'Main' 方法
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: b3aa66416f0cad6a6fb29a20aa0bca5e3486a18e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275427"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>在找不到具有適當簽章沒有存取 'Main' 方法 '\<名稱 >'
命令列應用程式必須具備`Sub Main`定義。 `Main` 必須宣告為`Public Shared`如果已定義在類別中，或為`Public`如果模組中定義。  
  
 **錯誤 ID:** BC30737  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   定義`Public Sub Main`程序，為您的專案。 將它宣告為`Shared`如果且只有在類別內定義它。  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 程式的結構](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)
