---
title: 如何：區塊序列化資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: 65e332d229da8fe51ad9c3e9850603471b1dfb12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018095"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="28063-102">如何：區塊序列化資料</span><span class="sxs-lookup"><span data-stu-id="28063-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="28063-103">在 Web 服務訊息中發送大型資料集時發生的兩項問題為：</span><span class="sxs-lookup"><span data-stu-id="28063-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="28063-104">由於序列化引擎緩衝而產生的大型工作集 (記憶體)。</span><span class="sxs-lookup"><span data-stu-id="28063-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="28063-105">由於 Base64 編碼後暴增 33%，因此過度消耗頻寬。</span><span class="sxs-lookup"><span data-stu-id="28063-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="28063-106">若要解決這些問題，請實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面以控制序列化與還原序列化。</span><span class="sxs-lookup"><span data-stu-id="28063-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="28063-107">具體地說，實作 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 和 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法將資料區分成區塊。</span><span class="sxs-lookup"><span data-stu-id="28063-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="28063-108">實作伺服器端區分區塊的功能</span><span class="sxs-lookup"><span data-stu-id="28063-108">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="28063-109">在伺服器機器上，Web 方法必須關閉 ASP.NET 緩衝並傳回實作 <xref:System.Xml.Serialization.IXmlSerializable>的型別。</span><span class="sxs-lookup"><span data-stu-id="28063-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="28063-110">實作 <xref:System.Xml.Serialization.IXmlSerializable> 的型別會將 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法中的資料區分區塊。</span><span class="sxs-lookup"><span data-stu-id="28063-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="28063-111">實作用戶端處理</span><span class="sxs-lookup"><span data-stu-id="28063-111">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="28063-112">變更用戶端 Proxy 上的 Web 方法以傳回實作 <xref:System.Xml.Serialization.IXmlSerializable>的型別。</span><span class="sxs-lookup"><span data-stu-id="28063-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="28063-113">您可以使用 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 自動執行這個作業，不過在此不予以討論。</span><span class="sxs-lookup"><span data-stu-id="28063-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="28063-114">實作 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法讀取區分成區塊的資料流並將位元組寫入磁碟。</span><span class="sxs-lookup"><span data-stu-id="28063-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="28063-115">此實作也引發圖形控制項可使用的進度事件，例如進度列。</span><span class="sxs-lookup"><span data-stu-id="28063-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28063-116">範例</span><span class="sxs-lookup"><span data-stu-id="28063-116">Example</span></span>  
<span data-ttu-id="28063-117">下列程式碼範例顯示關閉 ASP.NET 緩衝之用戶端上的 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="28063-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="28063-118">它也顯示用戶端 <xref:System.Xml.Serialization.IXmlSerializable> 介面的實作，將 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法中的資料區分區塊。</span><span class="sxs-lookup"><span data-stu-id="28063-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="28063-119">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="28063-119">Compiling the code</span></span>  
  
-   <span data-ttu-id="28063-120">程式碼使用下列命名空間：<xref:System>、<xref:System.Runtime.Serialization>、<xref:System.Web.Services>、<xref:System.Web.Services.Protocols>、<xref:System.Xml>、<xref:System.Xml.Serialization> 和 <xref:System.Xml.Schema>。</span><span class="sxs-lookup"><span data-stu-id="28063-120">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28063-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28063-121">See also</span></span>

- [<span data-ttu-id="28063-122">自訂序列化</span><span class="sxs-lookup"><span data-stu-id="28063-122">Custom Serialization</span></span>](custom-serialization.md)
