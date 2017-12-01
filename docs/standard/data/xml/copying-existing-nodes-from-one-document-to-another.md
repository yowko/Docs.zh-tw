---
title: "將現有節點從一個文件複製到另一個文件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f20e5bd595c8eb49360e58f281a8cf6eda89acf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>將現有節點從一個文件複製到另一個文件
**ImportNode**方法是一種機制，藉以節點或整個節點樹狀子目錄會從一個複製**XmlDocument**到另一個。 從呼叫傳回的節點是來自來源文件的節點複本，包括屬性值、節點名稱、節點型別和所有與命名空間相關的屬性，例如前置詞、區域名稱和命名空間統一資源識別元 (URI)。 來源文件不會變更。 在匯入節點之後，您仍然必須使用用於插入節點的其中一種方法將它加入至樹狀結構。  
  
 當節點附加於它的新文件時，新文件即擁有節點。 原因是在建立時，每個節點都會有自己的文件，即使節點是建立在不同的文件片段中也一樣。 這是 XML 文件物件模型 (DOM) 的需求，在會強制執行原廠建立設計**XmlDocument**類別。 例如， **CreateElement**，是以建立新節點的唯一方式。  
  
 根據節點類型的值匯入的節點以及*深層*參數，其他資訊會適當的複製。 若 XML 或 HTML 來源的片段是從某份文件複製到另一份文件，則這個方法會嘗試反映預期的行為，這表示對於 XML，這兩份文件可能具有不同的文件類型定義 (DTD)。  
  
 下列表格說明可以匯入之每種節點型別的特定行為。  
  
|節點類型|*深層*參數為 true|*深層*參數為 false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A>設**true**在 XmlAttribute 上。 來源的下階**XmlAttribute**會遞迴匯入與產生的節點會重組以形成對應的樹狀子目錄。|*深層*參數不適用於**XmlAttribute**節點，因為它們永遠會執行具有匯入時及其子節點。|  
|XmlCDataSection|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlComment|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlDocumentFragment|來源節點的子代會遞迴匯入，而且產生的節點會重組以形成對應的樹狀子目錄。|空白**XmlDocumentFragment**建立。|  
|XmlDocumentType|複製節點，包含其 data.*|複製節點，包含其 data.*|  
|XmlElement|來源項目的子代會遞迴匯入，而且產生的節點會重組以形成對應的樹狀子目錄。 **注意：**不會複製預設屬性。 如果要匯入的文件定義這個項目名稱的預設屬性，就會指派這些屬性。|指定匯入的來源項目節點、 屬性和產生**XmlAttribute**節點會附加到新的項目。 不會複製子代節點。 **注意：**不會複製預設屬性。 如果要匯入的文件定義這個項目名稱的預設屬性，就會指派這些屬性。|  
|XmlEntityReference|因為來源和目的文件可以擁有定義不同的實體，這個方法只會複製**XmlEntityReference**節點。 不包括取代文字。 如果目的文件有定義的實體，就會指派它的值。|因為來源和目的文件可以擁有定義不同的實體，這個方法只會複製**XmlEntityReference**節點。 不包括取代文字。 如果目的文件有定義的實體，就會指派它的值。|  
|XmlProcessingInstruction|從匯入的節點複製目標和資料值。|從匯入的節點複製目標和資料值。|  
|XmlText|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlSignificantWhitespace|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlWhitespace|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlDeclaration|從匯入的節點複製目標和資料值。|從匯入的節點複製目標和資料值。|  
|其他所有的節點型別|這些節點型別不會匯入。|這些節點型別不會匯入。|  
  
> [!NOTE]
>  雖然 DocumentType 節點可以匯入，但是一份文件只能有一個 DocumentType。 因此，當您匯入文件型別之後，在將它插入樹狀之前，您必須確定文件中有文件型別。 如需移除節點的詳細資訊，請參閱[移除節點、 內容和值從 XML 文件](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
