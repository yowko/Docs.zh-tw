---
title: 不支援 XML 實體參考
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 37e72dbd6de61a50b4192a0151db40cb4be49d1c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163268"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a>BC31180：不支援 XML 實體參考

例如，實體參考 (例如， `©` 未在 xml 1.0 規格中定義的) 會包含為 xml 常值的值。 `&`Xml 常值只支援、、、 `"` `<` `>` 和 `'` xml 實體參考。

 **錯誤識別碼：** BC31180

## <a name="to-correct-this-error"></a>更正這個錯誤

- 請移除不支援的實體參考。

## <a name="see-also"></a>另請參閱

- [XML 常值和 XML 1.0 規格](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [XML 常值](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
