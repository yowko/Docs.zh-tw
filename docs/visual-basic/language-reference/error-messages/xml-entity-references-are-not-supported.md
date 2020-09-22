---
title: 不支援 XML 實體參考
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 470e5577654ce8b6bbc2732a41c130a85ddc96e5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874993"
---
# <a name="xml-entity-references-are-not-supported"></a>不支援 XML 實體參考

例如，實體參考 (例如， `©` 未在 xml 1.0 規格中定義的) 會包含為 xml 常值的值。 `&`Xml 常值只支援、、、 `"` `<` `>` 和 `'` xml 實體參考。  
  
 **錯誤識別碼：** BC31180  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請移除不支援的實體參考。  
  
## <a name="see-also"></a>另請參閱

- [XML 常值和 XML 1.0 規格](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML 常值](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
