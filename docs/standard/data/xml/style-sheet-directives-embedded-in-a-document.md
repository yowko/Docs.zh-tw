---
title: 內嵌在文件中的樣式表指示詞
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fa671304c611db571b160cd1d960b83bf451c9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="style-sheet-directives-embedded-in-a-document"></a>內嵌在文件中的樣式表指示詞
有時候，現有的 XML 會包含 `<?xml:stylesheet?>` 的樣式表指示詞。 Microsoft Internet Explorer 將它視為 `<?xml-stylesheet?>` 語法的不同寫法。 XML 資料包含 `<?xml:stylesheet?>` 指示詞時，如果嘗試將這個資料載入 XML 文件物件模型 (DOM)，則會擲回例外狀況 (如同下列資料所示)。  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 因為 DOM 將 `<?xml:stylesheet?>` 視為無效的 **ProcessingInstruction**，所以會發生這種情況。 根據 Namespaces in XML 規格，任何 **ProcessingInstruction** 只能是無冒號名稱 (NCName)，相對於限定名稱 (QName)。  
  
 根據 Namespaces in XML 規格的第 6 節，在文件中，讓 **Load** 和 **LoadXml** 方法與規格相符的效果如下：  
  
-   所有的項目型別和屬性名稱都包含零或一個冒號。  
  
-   沒有任何實體名稱、ProcessingInstruction 目標或標記法名稱包含冒號。  
  
 如果 `<?xml:stylesheet?>` 包含冒號，即違反了第二個項目符號中的規則。  
  
 根據全球資訊網協會 (W3C) 將樣式表與 XML 文件產生關聯 1.0 版建議事項 (位於 www.w3.org/TR/xml-stylesheet)(英文)，能使 XSLT 樣式表與 XML 文件產生關聯的處理指示為 `<?xml-stylesheet?>`，以破折號取代冒號。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
