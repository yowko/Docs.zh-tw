---
title: "從讀取器載入資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b899ae870fe92b31d7f4fcd088531f63694bd233
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="load-data-from-a-reader"></a>從讀取器載入資料
使用 <xref:System.Xml.XmlDocument.Load%2A> 方法及 <xref:System.Xml.XmlReader> 的參數載入 XML 文件所發生的行為，與從其他格式載入資料的行為相比會有所不同。 如果讀取器處於其初始狀態，則 <xref:System.Xml.XmlDocument.Load%2A> 會使用讀取器的整個內容，並利用讀取器中的所有資料建置 XML 文件物件模型 (DOM)。  
  
 如果已將讀取器置於文件中某處的節點上，而且隨後將讀取器傳遞至 <xref:System.Xml.XmlDocument.Load%2A> 方法，則 <xref:System.Xml.XmlDocument.Load%2A> 會嘗試將目前節點及其所有同層級節點 (直到關閉目前深度的結束標記) 讀取至記憶體。 嘗試進行的 <xref:System.Xml.XmlDocument.Load%2A> 是否能夠成功，取決於嘗試載入時讀取器所在的節點，因為 <xref:System.Xml.XmlDocument.Load%2A> 會驗證來自讀取器的 XML 格式是否正確。 如果 XML 的格式不正確，則 <xref:System.Xml.XmlDocument.Load%2A> 會擲回例外狀況。 例如，下列節點集包含兩個根層級的項目，XML 的格式不正確，並且 <xref:System.Xml.XmlDocument.Load%2A> 會擲回例外狀況。  
  
-   Comment 節點之後依次跟隨 Element 節點、Element 節點及 EndElement 節點。  
  
 由於缺少根層級的項目，因此下列節點集會建立不完整的 DOM。  
  
-   Comment 節點之後依次跟隨 ProcessingInstruction 節點、Comment 節點及 EndElement 節點。  
  
 如此就不會擲回例外狀況，而且會載入資料。 您可以將根項目加入至這些節點的最上層，並建立可正確儲存且格式正確的 XML。  
  
 如果將讀取器置於對文件之根層級而言是無效的分葉節點 (例如，泛空白字元或屬性節點) 上，則讀取器會繼續讀取，直到將其置於可用於根層級的節點上。 此時文件會開始載入。  
  
 依預設，<xref:System.Xml.XmlDocument.Load%2A> 不會使用文件類型定義 (DTD) 或結構描述驗證，來驗證 XML 是否有效。 它只會驗證 XML 的格式是否正確。 為了執行驗證，您需要使用 <xref:System.Xml.XmlReader> 類別來建立 <xref:System.Xml.XmlReaderSettings>。 <xref:System.Xml.XmlReader> 類別可以使用 DTD 或結構描述定義語言 (XSD) 結構描述來強制執行驗證。 <xref:System.Xml.ValidationType> 類別上的 <xref:System.Xml.XmlReaderSettings> 屬性可以決定 <xref:System.Xml.XmlReader> 執行個體是否能夠強制執行驗證。 如需驗證 XML 資料的詳細資訊，請參閱 <xref:System.Xml.XmlReader> 參考頁面的＜備註＞一節。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
