---
title: "如何：區塊序列化資料"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: 3
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 5d8c56be905d6dbfa966546c109a322e013baaac
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-chunk-serialized-data"></a>如何：區塊序列化資料

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

在 Web 服務訊息中發送大型資料集時發生的兩項問題為：  
  
1.  由於序列化引擎緩衝而產生的大型工作集 (記憶體)。  
  
2.  由於 Base64 編碼後暴增 33%，因此過度消耗頻寬。  
  
 若要解決這些問題，請實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面以控制序列化與還原序列化。 具體地說，實作 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 和 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法將資料區分成區塊。  
  
### <a name="to-implement-server-side-chunking"></a>實作伺服器端區分區塊的功能  
  
1.  在伺服器機器上，Web 方法必須關閉 ASP.NET 緩衝並傳回實作 <xref:System.Xml.Serialization.IXmlSerializable>的型別。  
  
2.  實作 <xref:System.Xml.Serialization.IXmlSerializable> 的型別會將 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法中的資料區分區塊。  
  
### <a name="to-implement-client-side-processing"></a>實作用戶端處理  
  
1.  變更用戶端 Proxy 上的 Web 方法以傳回實作 <xref:System.Xml.Serialization.IXmlSerializable>的型別。 您可以使用 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 自動執行這個作業，不過在此不予以討論。  
  
2.  實作 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法讀取區分成區塊的資料流並將位元組寫入磁碟。 此實作也引發圖形控制項可使用的進度事件，例如進度列。  
  
## <a name="example"></a>範例  
下列程式碼範例顯示關閉 ASP.NET 緩衝之用戶端上的 Web 方法。 它也顯示用戶端 <xref:System.Xml.Serialization.IXmlSerializable> 介面的實作，將 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法中的資料區分區塊。  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)] [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)] [!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)] [!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   程式碼使用下列命名空間：<xref:System>、<xref:System.Runtime.Serialization>、<xref:System.Web.Services>、<xref:System.Web.Services.Protocols>、<xref:System.Xml>、<xref:System.Xml.Serialization> 和 <xref:System.Xml.Schema>。  
  
## <a name="see-also"></a>請參閱  
 [自訂序列化](custom-serialization.md)

