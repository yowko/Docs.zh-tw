---
title: 類型 &#39; type1 &#39; 的值無法轉換成 &#39; type2 &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efa6fcd4d996fb3277cc4cac2af16a86a2d65977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>類型 &#39; type1 &#39; 的值無法轉換成 &#39; type2 &#39;
類型 'type1' 值無法轉換成 'type2'。 您可以使用 'Value' 屬性取得的第一個元素的字串值 '\<parentElement >'。  
  
 已嘗試將 XML 常值隱含轉換成特定類型。 您無法將 XML 常值隱含轉換成指定的類型。  
  
 **錯誤 ID:** BC31194  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   使用 XML 常值的 `Value` 屬性以 `String`形式來參考其值。 使用 `CType` 函式、另一個類型轉換函式或 <xref:System.Convert> 類別，將值轉換為指定的類型。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Convert>  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
