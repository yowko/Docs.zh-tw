---
title: "解析外部資源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 824a35ee5d4ecafc45167ff3f4bc89802af4ed96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="resolving-external-resources"></a>解析外部資源
**XmlResolver**屬性**XmlDocument**正由**XmlDocument**找不到沒有內嵌在 XML 資料，例如外部文件類型資源類別定義 (Dtd)、 實體和結構描述。 這些項目可位於網路或本機磁碟上，並且可以由統一資源識別元 (URI) 辨識。 這可讓**XmlDocument**解析**EntityReference**節點會出現在文件，並驗證根據外部 DTD 或結構描述文件。  
  
## <a name="fully-trusted-xmldocument"></a>完全信任的 XmlDocument  
 **XmlResolver**屬性會影響的功能**Textreader**方法。 下的表顯示如何**XmlDocument.XmlResolver**屬性的運作方式時**XmlDocument**物件是完全受信任。 下表顯示**Textreader**方法時載入的輸入是**TextReader**，**字串**，**資料流**，或**URI**。 這個表格不適用於**負載**方法如果**XmlDocument**是從載入**XmlReader**。  
  
|XmlResolver 屬性|函式|注意|  
|--------------------------|--------------|-----------|  
|屬性設定為**XmlResolver**先前已建立且已由使用者在其上設定屬性的類別。|**XmlDocument**使用**XmlResolver** ，指定用來解析檔案名稱，來解析外部資源，例如 Dtd、 實體和結構描述的參考。<br /><br /> **XmlResolver**當解析外部資源所需新增或編輯中的節點時也會使用**XmlDocument**。|**XmlResolver**提供給**XmlDocument**是需要尋找並解析外部資源時，都會使用的解析程式。|  
|屬性設定為**null** (**Nothing**在 Microsoft Visual Basic.NET)。|不支援需要外部資源的功能，例如尋找外部結構描述或 DTD。 也不會解析外部實體，並且也不支援執行編輯功能 (例如插入需要解析的實體節點)。|**XmlDocument**載入檔案匿名身分，並不會嘗試解決其他任何資源。|  
|尚未設定屬性，但是保留為預設狀態。|**XmlUrlResolver** null 認證會具現化並供**XmlDocument**時解析檔案名稱、 尋找外部 Dtd、 實體和結構描述，和**null**編輯節點時會使用的認證。||  
  
 下表顯示**Textreader**方法時的輸入**負載**是**XmlReader**和**XmlDocument**是完全信任。  
  
|XmlResolver 屬性|函式|注意|  
|--------------------------|--------------|-----------|  
|**XmlResolver**類別所使用**XmlDocument**是正在使用的相同類別**XmlReader**。|**XmlDocument**使用**XmlResolver** ，已指派給**XmlReader**。<br /><br /> **XmlDocument.Resolver**屬性不可設定，而不論**XmlDocument**信任層級，因為它即將**XmlResolver**從**XmlReader**。 您無法嘗試覆寫的設定**Xmldocument**' **XmlResolver**藉由設定**XmlResolver**屬性**XmlDocument**.|**XmlReader**可以**XmlTextReader**， **XmlValidatingReader**，或自訂撰寫的讀取器。 如果所用的讀取器支援實體解析，則會解析外部實體。 如果傳遞的讀取器不支援實體參考，則不會解析實體參考。|  
  
## <a name="semi-trusted-xmldocument"></a>非完全信任的 XmlDocument  
 下表顯示如何**XmlDocument.XmlResolver**屬性的物件是完全信任的運作方式。 此表格適用於**Textreader**方法時載入的輸入是**TextReader**，**字串**，**資料流**，或**URI**。 這個表格不適用於**負載**方法如果**XmlDocument**是從載入**XmlReader**。  
  
|XmlResolver 屬性|函式|注意|  
|--------------------------|--------------|-----------|  
|在非完全信任的案例中， **XmlResolver**屬性無法設定為 null 以外的任何項目。|**XmlUrlResolver**與**null**認證會具現化並供**XmlDocument**時解析檔案名稱、 尋找外部 Dtd、 實體和結構描述，和**null**編輯節點時會使用的認證。|此行為是相同的行為時**XmlResolver**屬性尚未設定，但是保留為預設狀態。<br /><br /> **XmlDocument**使用匿名權限執行所有動作。|  
|屬性設定為**null** (**Nothing**在 Microsoft Visual Basic.NET)。|不支援需要外部資源的功能，例如尋找外部結構描述或 DTD。 也不會解析外部實體，並且也不支援執行編輯功能，例如插入需要資源的實體節點。|若屬性是**null**，則行為是相同的不論 if **XmlDocument**是完全受信任或非完全信任。|  
|尚未設定屬性，但是保留為預設狀態。|**XmlUrlResolver**與**null**認證會具現化並供**XmlDocument**時解析檔案名稱、 尋找外部 Dtd、 實體和結構描述，和**null**編輯節點時會使用的認證。|**XmlDocument**使用匿名權限執行所有動作。|  
  
 此表格適用於**Textreader**方法時的輸入**負載**是**XmlReader**，而**XmlDocument**是非完全信任。  
  
|XmlResolver 屬性|函式|注意|  
|--------------------------|--------------|-----------|  
|**XmlResolver**類別所使用**XmlDocument**正由相同**XmlReader**。|**XmlDocument**使用**XmlResolver** ，已指派給**XmlReader**。<br /><br /> **XmlDocument.Resolver**屬性不可設定，而不論**XmlDocument**信任層級，因為它即將**XmlResolver**從**XmlReader**。 您無法嘗試覆寫的設定**Xmldocument** **XmlResolver**藉由設定**XmlResolver**屬性**XmlDocument**.|**XmlReader**可以**XmlTextReader**、 驗證<xref:System.Xml.XmlReader>，或自訂撰寫的讀取器。 如果所用的讀取器支援實體解析，則會解析外部實體。 如果傳遞的讀取器不支援實體參考，則不會解析實體參考。|  
  
 設定 XmlResolver 使其含有正確的認證，即可存取外部資源。  
  
> [!NOTE]
>  沒有任何方法來擷取**XmlResolver**屬性。 這有助於防止使用者重複使用**XmlResolver**上的認證已設定。 此外，如果**XmlTextReader**或驗證<xref:System.Xml.XmlReader>用來載入**XmlDocument**和**XmlDocument**具有已設定，從解析程式的解析程式這些讀取器不會快取**XmlDocument**之後**負載**階段，因為這也意謂著安全性風險。  
  
 如需詳細資訊，請參閱 <xref:System.Xml.XmlResolver> 參考頁面的＜備註＞一節。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
