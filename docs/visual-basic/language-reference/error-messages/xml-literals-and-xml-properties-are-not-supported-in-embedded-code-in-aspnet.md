---
title: ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性
ms.date: 07/20/2015
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords:
- BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
ms.openlocfilehash: 559889587b30418dc2fe2860cfbf90f91605c668
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594838"
---
# <a name="xml-literals-and-xml-properties-are-not-supported-in-embedded-code-within-aspnet"></a>ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性
在 ASP.NET 中的內嵌程式碼中不支援 XML 常值和 XML 屬性。 若要使用的 XML 功能，將移至程式碼後置程式碼。  
  
 內嵌程式碼中定義的 XML 常值或 XML 軸屬性 (`<%= =>`) ASP.NET 檔中。  
  
 **錯誤 ID:** BC31200  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將程式碼，包括 XML 常值或 XML 軸屬性移至 ASP.NET 程式碼後置檔案。  
  
## <a name="see-also"></a>另請參閱  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML 軸屬性](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
