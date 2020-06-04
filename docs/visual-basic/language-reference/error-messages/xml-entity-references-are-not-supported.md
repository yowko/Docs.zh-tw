---
title: 不支援 XML 實體參考
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: ae997d853a93999a3b29215ea1257da7a1d48c84
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406452"
---
# <a name="xml-entity-references-are-not-supported"></a>不支援 XML 實體參考
`©`未在 xml 1.0 規格中定義的實體參考（例如）會包含為 xml 常值的值。 `&` `"` Xml 常值中僅支援、、 `<` 、 `>` 和 `'` xml 實體參考。  
  
 **錯誤識別碼：** BC31180  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 移除不支援的實體參考。  
  
## <a name="see-also"></a>另請參閱

- [XML 常值和 XML 1.0 規格](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML 常值](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
