---
title: 必須有陳述式結尾
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 36883989fe5aa0b5c70aa9ab1f7c991fab99e778
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163125"
---
# <a name="bc30205-end-of-statement-expected"></a>BC30205：預期的語句結尾

語句的語法已完成，但其他程式設計專案會在完成語句的元素之後。 在每個語句的結尾都需要行結束字元。

 行結束字元會將 Visual Basic 原始程式檔的字元分成幾行。 行結束字元的範例有 Unicode 換行字元 ( # B0 HD) 、Unicode 換行字元 ( # B1 HA) ，以及 unicode 換行字元（後面接著 Unicode 換行字元）。 如需行結束字元的詳細資訊，請參閱 [Visual Basic 語言規格](~/_vblang/spec/lexical-grammar.md#line-terminators)。

 **錯誤識別碼：** BC30205

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 檢查是否有兩個不同的語句不小心放在同一行上。

2. 在完成語句的元素之後插入行結束字元。

## <a name="see-also"></a>另請參閱

- [作法：程式碼中的 Break 及 Combine 陳述式](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [陳述式](../../programming-guide/language-features/statements.md)
