---
title: 解析外部資源
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef31d101769dca00f5cff545c72b3afbd59bc638
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268402"
---
# <a name="resolving-external-resources"></a>解析外部資源
**XmlDocument** 類別可以使用 **XmlDocument** 的 **XmlResolver** 屬性尋找沒有內嵌到 XML 資料的資源，例如外部文件類型定義 (DTD)、實體和結構描述。 這些項目可位於網路或本機磁碟上，並且可以由統一資源識別元 (URI) 辨識。 如此可讓 **XmlDocument** 解析文件中出現的 **EntityReference** 節點，並依據外部 DTD 或結構描述驗證文件。  
  
## <a name="fully-trusted-xmldocument"></a>完全信任的 XmlDocument  
 **XmlResolver** 屬性會影響 **XmlDocument.Load** 方法的功能。 下表顯示，在 **XmlDocument** 物件是完全受信任時，**XmlDocument.XmlResolver** 屬性將會如何運作。 下表說明當 Load 的輸入為 **TextReader**、**String**、**Stream** 或 **URI** 時的 **XmlDocument.Load** 方法。 如果 **XmlDocument** 是從 **XmlReader** 載入，則這個表格不適用於 **Load** 方法。  
  
|XmlResolver 屬性|功能|注意|  
|--------------------------|--------------|-----------|  
|屬性設定為之前已建立的 **XmlResolver** 類別，而這個類別已經有由使用者設定好的屬性。|**XmlDocument** 使用的 **XmlResolver**，是指定用來解析檔案名稱、解析外部資源的參考 (例如 DTD、實體和結構描述)。<br /><br /> 當解析在加入或編輯 **XmlDocument** 中節點必要的外部資源時，也會使用 **XmlResolver**。|每當您要尋找並解析外部資源時，就必須使用指定給 **XmlDocument** 之 **XmlResolver** 解析程式。|  
|屬性會設定為 **null** (在 Microsoft Visual Basic .NET中則為 **Nothing**)。|不支援需要外部資源的功能，例如尋找外部結構描述或 DTD。 也不會解析外部實體，並且也不支援執行編輯功能 (例如插入需要解析的實體節點)。|**XmlDocument** 將檔案以匿名載入，並且不會嘗試解析任何其他的資源。|  
|尚未設定屬性，但是保留為預設狀態。|在解析檔案名稱、尋找外部 DTD、實體和結構描述時，帶有 NULL 認證的 **XmlUrlResolver** 會被具現化，並且被 **XmlDocument** 使用，同時在編輯節點時會使用 **null** 認證。||  
  
 下表說明當 **Load** 的輸入是 **XmlReader**，且 **XmlDocument** 是完全受信任時的 **XmlDocument.Load** 方法。  
  
|XmlResolver 屬性|功能|注意|  
|--------------------------|--------------|-----------|  
|**XmlDocument** 使用的 **XmlResolver** 類別與 **XmlReader** 使用的類別相同。|**XmlDocument** 使用指定給 **XmlReader** 的 **XmlResolver**。<br /><br /> 因為 **XmlDocument.Resolver** 是從 **XmlReader** 取得 **XmlResolver**，所以不論 **XmlDocument** 的信任層級為何，其屬性都無法設定。 您無法藉由設定 **XmlDocument** 的 **XmlResolver** 屬性，來覆寫 **XmlReader** 的 **XmlResolver** 的設定。|**XmlReader** 可能是 **XmlTextReader**、**XmlValidatingReader** 或自訂撰寫的讀取器。 如果所用的讀取器支援實體解析，則會解析外部實體。 如果傳遞的讀取器不支援實體參考，則不會解析實體參考。|  
  
## <a name="semi-trusted-xmldocument"></a>非完全信任的 XmlDocument  
 下表顯示當物件是非完全信任時，**XmlDocument.XmlResolver** 屬性如何運作。 當 Load 的輸入為 **TextReader**、**String**、**Stream** 或 **URI** 時，此表格即適用於 **XmlDocument.Load** 方法。 如果 **XmlDocument** 是從 **XmlReader** 載入，則這個表格不適用於 **Load** 方法。  
  
|XmlResolver 屬性|功能|注意|  
|--------------------------|--------------|-----------|  
|在非完全信任的案例中，**XmlResolver** 屬性只能設定為 Null。|在解析檔案名稱、尋找外部 DTD、實體和結構描述時，帶有 **null** 認證的 **XmlUrlResolver** 會被具現化，並且被 **XmlDocument** 使用，同時在編輯節點時會使用 **null** 認證。|這個行為和 **XmlResolver** 屬性沒有設定並保留為預設狀態時的行為相同。<br /><br /> **XmlDocument** 使用匿名權限執行所有的動作。|  
|屬性會設定為 **null** (在 Microsoft Visual Basic .NET中則為 **Nothing**)。|不支援需要外部資源的功能，例如尋找外部結構描述或 DTD。 也不會解析外部實體，並且也不支援執行編輯功能，例如插入需要資源的實體節點。|若屬性是 **null**，則不論 **XmlDocument** 是完全受信任或非完全受信任，都會有相同的行為。|  
|尚未設定屬性，但是保留為預設狀態。|在解析檔案名稱、尋找外部 DTD、實體和結構描述時，帶有 **null** 認證的 **XmlUrlResolver** 會被具現化，並且被 **XmlDocument** 使用，同時在編輯節點時會使用 **null** 認證。|**XmlDocument** 使用匿名權限執行所有的動作。|  
  
 當 **Load** 的輸入為 **XmlReader** 並且 **XmlDocument** 是非完全信任時，這個表格適用於 **XmlDocument.Load** 方法。  
  
|XmlResolver 屬性|功能|注意|  
|--------------------------|--------------|-----------|  
|**XmlDocument** 使用的 **XmlResolver** 類別與 **XmlReader** 使用的類別相同。|**XmlDocument** 使用指定給 **XmlReader** 的 **XmlResolver**。<br /><br /> 因為 **XmlDocument.Resolver** 是從 **XmlReader** 取得 **XmlResolver**，所以不論 **XmlDocument** 的信任層級為何，其屬性都無法設定。 您無法藉由設定 **XmlDocument** 的 **XmlResolver** 屬性，來覆寫 **XmlReader** 的 **XmlResolver** 的設定。|**XmlReader** 可以是 **XmlTextReader**、驗證的 <xref:System.Xml.XmlReader> 或自訂撰寫的讀取器。 如果所用的讀取器支援實體解析，則會解析外部實體。 如果傳遞的讀取器不支援實體參考，則不會解析實體參考。|  
  
 設定 XmlResolver 使其含有正確的認證，即可存取外部資源。  
  
> [!NOTE]
>  您無法擷取 **XmlResolver** 屬性。 這有助於防止使用者重複使用已經在其上設定安全性認證的 **XmlResolver**。 此外，若使用 **XmlTextReader** 或驗證的 <xref:System.Xml.XmlReader> 來載入 **XmlDocument**，且 **XmlDocument** 具有已經設定的解析程式，則 **XmlDocument** 在 **Load** 階段之後將不會快取這些讀取器的解析程式，因為這也會帶來安全性方面的風險。  
  
 如需詳細資訊，請參閱 <xref:System.Xml.XmlResolver> 參考頁面的＜備註＞一節。  
  
## <a name="see-also"></a>另請參閱

- [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
