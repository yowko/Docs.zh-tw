---
title: XML 命名空間 URI '<uri>' 只可繫結到 'xmlns'
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: 1aec6ac0a354bfe7e0378a2e46a70a7161bf6d36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163242"
---
# <a name="bc31183-xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a>BC31183： XML 命名空間 URI; 只能系結 `http://www.w3.org/XML/1998/namespace` 至 ' xmlns '

URI `http://www.w3.org/XML/1998/namespace` 用於 XML 命名空間宣告中。 此 URI 是保留的命名空間，不能包含在 XML 命名空間宣告中。

 **錯誤識別碼：** BC31183

## <a name="to-correct-this-error"></a>更正這個錯誤

請移除 XML 命名空間宣告，或將 URI 取代為 `http://www.w3.org/XML/1998/namespace` 有效的命名空間 URI。

## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (XML 命名空間)](../statements/imports-statement-xml-namespace.md)
- [XML 常值](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
