---
title: 將現有節點從一個文件複製到另一個文件
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 744c97e8728d0a65bff8e7bb7a7dbb298afe1800
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44088085"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>將現有節點從一個文件複製到另一個文件
**ImportNode** 方法是一種機制，藉由這個機制，節點或整個節點樹狀子目錄會從一個 **XmlDocument** 複製到另一個。 從呼叫傳回的節點是來自來源文件的節點複本，包括屬性值、節點名稱、節點型別和所有與命名空間相關的屬性，例如前置詞、區域名稱和命名空間統一資源識別元 (URI)。 來源文件不會變更。 在匯入節點之後，您仍然必須使用用於插入節點的其中一種方法將它加入至樹狀結構。  
  
 當節點附加於它的新文件時，新文件即擁有節點。 原因是在建立時，每個節點都會有自己的文件，即使節點是建立在不同的文件片段中也一樣。 這是 XML 文件物件模型 (DOM) 的必要需求，**XmlDocument** 類別上的原廠建立設計會加以強制執行。 例如，**CreateElement** 即為建立新節點的方式之一。  
  
 根據匯入節點的節點型別和 *deep* 參數的值，其他的資訊會適當的複製。 若 XML 或 HTML 來源的片段是從某份文件複製到另一份文件，則這個方法會嘗試反映預期的行為，這表示對於 XML，這兩份文件可能具有不同的文件類型定義 (DTD)。  
  
 下列表格說明可以匯入之每種節點型別的特定行為。  
  
|節點類型|*deep* 參數為 true|*deep* 參數為 false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> 在 XmlAttribute 上會設為 **true**。 來源 **XmlAttribute** 的子代會遞迴匯入，而且產生的節點會重組以形成對應的樹狀子目錄。|*deep* 參數不會套用至 **XmlAttribute** 節點，因為它們在匯入時一定會帶著它們的子節點。|  
|XmlCDataSection|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlComment|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlDocumentFragment|來源節點的子代會遞迴匯入，而且產生的節點會重組以形成對應的樹狀子目錄。|會建立空白的 **XmlDocumentFragment**。|  
|XmlDocumentType|複製節點，包含其 data.*|複製節點，包含其 data.*|  
|XmlElement|來源項目的子代會遞迴匯入，而且產生的節點會重組以形成對應的樹狀子目錄。 **注意：** 不會複製預設屬性。 如果要匯入的文件定義這個項目名稱的預設屬性，就會指派這些屬性。|來源項目的指定屬性節點會匯入，而且產生的 **XmlAttribute** 節點會附加至新項目。 不會複製子代節點。 **注意：** 不會複製預設屬性。 如果要匯入的文件定義這個項目名稱的預設屬性，就會指派這些屬性。|  
|XmlEntityReference|因為來源和目的文件可以擁有定義不同的實體，這個方法只會複製 **XmlEntityReference** 節點。 不包括取代文字。 如果目的文件有定義的實體，就會指派它的值。|因為來源和目的文件可以擁有定義不同的實體，這個方法只會複製 **XmlEntityReference** 節點。 不包括取代文字。 如果目的文件有定義的實體，就會指派它的值。|  
|XmlProcessingInstruction|從匯入的節點複製目標和資料值。|從匯入的節點複製目標和資料值。|  
|XmlText|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlSignificantWhitespace|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlWhitespace|複製節點，包含其資料。|複製節點，包含其資料。|  
|XmlDeclaration|從匯入的節點複製目標和資料值。|從匯入的節點複製目標和資料值。|  
|其他所有的節點型別|這些節點型別不會匯入。|這些節點型別不會匯入。|  
  
> [!NOTE]
>  雖然 DocumentType 節點可以匯入，但是一份文件只能有一個 DocumentType。 因此，當您匯入文件型別之後，在將它插入樹狀之前，您必須確定文件中有文件型別。 如需移除節點的資訊，請參閱[從 XML 文件移除節點、內容和值](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
