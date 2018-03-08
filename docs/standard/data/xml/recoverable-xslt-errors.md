---
title: "可復原的 XSLT 錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4564530cd173793519471c78105d0394595f6d5c
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="recoverable-xslt-errors"></a>可復原的 XSLT 錯誤
＜W3C XSL 轉換 (XSLT) 1.0 版建議事項＞中所包含的領域，可告訴實作提供者該採取哪些決策來處理哪種狀況。 這些領域視為 Discretionary 行為。 例如，在 7.3 節＜建立處理指示＞中，XSLT 1.0 版建議事項指出如果具現化 `xsl:processing-instruction` 的內容會建立非文字節點的節點，就會產生錯誤。 針對某些問題，XSLT 1.0 版建議事項中會指出在處理器決定從錯誤復原時要採取的決策。 針對 7.3 節中的問題，W3C 指出只要忽略節點及其內容，實作即可從這項錯誤中復原。  
  
## <a name="discretionary-behaviors"></a>Discretionary 行為  
 下表會列出 XSLT 1.0 版建議事項所允許的每個 Discretionary 行為，以及 <xref:System.Xml.Xsl.XslCompiledTransform> 類別如何處理這些行為。  
  
-   「復原」表示 <xref:System.Xml.Xsl.XslCompiledTransform> 類別將從此錯誤復原。 <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> 事件可用於報告 XSLT 處理器的任何事件。  
  
-   「錯誤」表示引發此情況的例外狀況。  
  
-   您可以在 [W3C XSL 轉換 (XSLT) 1.0 版建議事項](http://www.w3.org/TR/xslt) (英文) 和 [W3C XSL 轉換 (XSLT) 1.0 版規格錯誤](http://www.w3.org/1999/11/REC-xslt-19991116-errata/) (英文) 中找到章節參考資料。  
  
|XSLT 條件|區段|XslCompiledTransform 行為|  
|--------------------|-------------|-----------------------------------|  
|文字節點同時符合 `xsl:strip-space` 及 `xsl:preserve-space`。|3.4|復原|  
|來源節點符合一個以上的範本 (Template) 規則。|5.5|復原|  
|命名空間 URI 會宣告成多個命名空間 URI 的別名，且全都具有相同的匯入優先順序。|7.1.1|復原|  
|從屬性值產生之 `name` 及 `xsl:attribute` 中的 `xsl:element` 屬性不是 QName。|7.1.2, 7.1.3|錯誤*|  
|具有相同匯入及展開名稱的兩個屬性集具有通用的屬性，而且其他任何屬性集都不會包含具有相同名稱、更高重要性的通用屬性。|7.1.4|復原|  
|將項目子系加入至項目後，將屬性加入至該項目。|7.1.3|錯誤*|  
|建立具有 xmlns 名稱的屬性|7.1.3|錯誤*|  
|將非項目的屬性加入至節點。|7.1.3|錯誤*|  
|具現化 `xsl:attribute` 屬性的內容期間，建立非文字節點的節點。|7.1.3|錯誤*|  
|`name` 的 `xsl:processing-instruction` 屬性不會同時產生 NCName 及處理指示目標。|7.3|錯誤*|  
|具現化 `xsl:processing-instruction` 的內容會建立非文字節點的節點。|7.3|錯誤*|  
|具現化 `xsl:processing-instruction` 內容的結果包含字串「?>」|7.3|復原|  
|具現化 `xsl:processing-instruction` 內容的結果包含字串 --，或以 - 為結尾。|7.4|復原|  
|具現化 `xsl:comment` 內容的結果會建立非文字節點的節點。|7.4|錯誤*|  
|變數繫結項目內的範本會傳回屬性節點或命名空間節點。|11.2|錯誤*|  
|從傳遞至文件函式的 URI 上擷取資源時發生錯誤。|12.1|錯誤|  
|文件函式中的 URI 參考包含片段識別項，且處理片段識別項時發生錯誤。|12.1|復原*|  
|有多個具有相同名稱、不同值的屬性，它們不是具有相同匯入優先順序之 `xsl:output` 中的具名 cdata-section 項目。|16|復原|  
|處理器不支援 `xsl:output` 編碼屬性中的編碼。|16.1|復原|  
|針對文字節點，停用結果樹狀目錄中用於非文字節點之節點的輸出逸出。|16.4|復原*|  
|如果結果樹狀結構片段包含啟用輸出逸出的文字節點，則結果樹狀結構片段會轉換成數字或字串。|16.4|復原*|  
|針對不能以 XSLT 處理器用於輸出的編碼方式表示的字元，停用輸出逸出。|16.4|復原*|  
|在項目中加入項目子系或屬性後，加入命名空間節點。|勘誤表 25|錯誤*|  
|`value` 的 `xsl:number` 屬性為 NAN、無限或小於 0.5|勘誤表 24|復原|  
|文件函式的第二個引數節點集是空的，且 URI 參考是相對的。|勘誤表 14|復原|  
  
 <sup>*</sup> 此行為與 <xref:System.Xml.Xsl.XslTransform> 類別的行為不同。 如需詳細資訊，請參閱 [XslTransform 類別中的 Discretionary 行為實作](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)。  
  
## <a name="see-also"></a>請參閱  
 [XSLT 轉換](../../../../docs/standard/data/xml/xslt-transformations.md)
