---
title: "ASP.NET 中的內嵌式程式碼不支援 XML 常值和 XML 屬性"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31200
- bc31200
helpviewer_keywords: BC31200
ms.assetid: 053e8cba-8584-45cc-9fa0-43d122779772
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 932c36778720718d777412f958c16b4a650e3b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
