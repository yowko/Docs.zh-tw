---
title: "'Module' 陳述式只可以發生在檔案或命名空間層級"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: b946a527d3de3a030ac03691c77afcf440f518ee
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160310"
---
# <a name="bc30617-module-statements-can-occur-only-at-file-or-namespace-level"></a>BC30617： ' Module ' 語句只可以發生在檔案或命名空間層級

`Module` 語句必須緊接在 `Option` 和 `Imports` 語句、全域屬性和命名空間宣告之後，但在所有其他宣告之前，都必須出現在原始程式檔的頂端。

 **錯誤識別碼：** BC30617

## <a name="to-correct-this-error"></a>更正這個錯誤

- 將 `Module` 陳述式移至命名空間宣告或原始程式檔的上方。

## <a name="see-also"></a>另請參閱

- [Module 陳述式](../statements/module-statement.md)
