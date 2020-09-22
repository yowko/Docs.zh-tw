---
title: 類型 'type1' 的值無法轉換成 'type2'
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 8c80429db618e1bcadce1a58a6514d625f0b3cf1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870233"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>類型 'type1' 的值無法轉換成 'type2'

類型 ' type1 ' 的值無法轉換成 ' type2 '。 您可以使用 ' Value ' 屬性來取得 ' ' 第一個元素的字串值 \<parentElement> 。  
  
 已嘗試將 XML 常值隱含轉換成特定類型。 您無法將 XML 常值隱含轉換成指定的類型。  
  
 **錯誤識別碼：** BC31194  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 使用 XML 常值的 `Value` 屬性以 `String`形式來參考其值。 使用 `CType` 函式、另一個類型轉換函式或 <xref:System.Convert> 類別，將值轉換為指定的類型。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Convert>
- [Type Conversion Functions](../functions/type-conversion-functions.md)
- [XML 常值](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
