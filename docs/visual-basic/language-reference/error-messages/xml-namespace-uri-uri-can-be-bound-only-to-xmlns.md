---
title: XML 命名空間 URI '<uri>' 只可繫結到 'xmlns'
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: 9d791ae699f369ebe69e03fc5019d3ca58554224
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406478"
---
# <a name="xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a>XML 命名空間 URI; 只能系結 `http://www.w3.org/XML/1998/namespace` 至 ' xmlns '
URI `http://www.w3.org/XML/1998/namespace` 會用於 XML 命名空間宣告中。 此 URI 是保留的命名空間，而且不能包含在 XML 命名空間宣告中。  
  
 **錯誤識別碼：** BC31183  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
請移除 XML 命名空間宣告，或 `http://www.w3.org/XML/1998/namespace` 使用有效的命名空間 URI 來取代 uri。  
  
## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (XML 命名空間)](../statements/imports-statement-xml-namespace.md)
- [XML 常值](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
