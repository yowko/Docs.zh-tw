---
title: ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: bda92b4244631f66142499a94be562854b35437e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406465"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性
ASP.NET 內的內嵌程式碼不支援 XML 常值和 XML 屬性。 若要使用 XML 功能，請將程式碼移至程式碼後置。  
  
 XML 常值或 XML 軸屬性是在 ASP.NET 檔案中的內嵌程式碼（）內定義 `<%= =>` 。  
  
 **錯誤識別碼：** BC31200  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將包含 XML 常值或 XML 軸屬性的程式碼移至 ASP.NET 程式碼後置檔案。  
  
## <a name="see-also"></a>另請參閱

- [XML 常值](../xml-literals/index.md)
- [XML 軸屬性](../xml-axis/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
