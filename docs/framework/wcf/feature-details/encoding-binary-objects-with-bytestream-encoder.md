---
title: 以位元組資料流編碼器將二進位物件編碼
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 9619fdf6979833c30159e1ea02b3f8d6b98a6629
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489478"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="74014-102">以位元組資料流編碼器將二進位物件編碼</span><span class="sxs-lookup"><span data-stu-id="74014-102">Encoding Binary Objects with ByteStream Encoder</span></span>
<span data-ttu-id="74014-103">傳送和接收原始二進位資料與 Windows Communication Foundation (WCF) 已設定使用<xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="74014-103">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="74014-104">位元組資料流訊息編碼器架構</span><span class="sxs-lookup"><span data-stu-id="74014-104">Byte Stream Message Encoder Architecture</span></span>  
 <span data-ttu-id="74014-105">二進位訊息編碼器，會由 WCF 有沒有能力處理、 驗證或識別訊息中的基礎二進位資料。</span><span class="sxs-lookup"><span data-stu-id="74014-105">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="74014-106">資料封裝會編碼為 XML，傳送、接收及解碼。</span><span class="sxs-lookup"><span data-stu-id="74014-106">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="74014-107">編碼器處理資料的時間，是在資料傳遞到傳輸之後，且在訊息傳送至訊息佇列之前。</span><span class="sxs-lookup"><span data-stu-id="74014-107">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="74014-108">在功能上，二進位編碼器會將訊息資料包裝在 `<binary>` 項目中進行傳送，而在訊息接收到之後會移除這些項目。</span><span class="sxs-lookup"><span data-stu-id="74014-108">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="74014-109">使用位元組資料流訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="74014-109">Using the Byte Stream Message Encoder</span></span>  
 <span data-ttu-id="74014-110">下列範例示範實作位元組資料流訊息編碼器的服務合約。</span><span class="sxs-lookup"><span data-stu-id="74014-110">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="74014-111">下列範例示範正在叫用的服務。</span><span class="sxs-lookup"><span data-stu-id="74014-111">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="74014-112">如果使用實作訊息基礎結構 (例如路由器) 的服務，處理訊息時並不會檢查、驗證訊息，或是與訊息有其他形式的互動，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="74014-112">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="74014-113">案例</span><span class="sxs-lookup"><span data-stu-id="74014-113">Scenarios</span></span>  
 <span data-ttu-id="74014-114">在下列案例中，位元組資料流編碼器很有用。</span><span class="sxs-lookup"><span data-stu-id="74014-114">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
-   <span data-ttu-id="74014-115">使用 WCF 的電腦之間傳輸 JPEG 影像。</span><span class="sxs-lookup"><span data-stu-id="74014-115">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="74014-116">在此案例中，影像將透過外部來源的傳輸送達，而且所傳送的資料是構成影像的未經處理位元組。</span><span class="sxs-lookup"><span data-stu-id="74014-116">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="74014-117">服務將會接收二進位資料並顯示影像。</span><span class="sxs-lookup"><span data-stu-id="74014-117">A service will receive the binary data and display the image.</span></span>  
  
-   <span data-ttu-id="74014-118">從訊息佇列中讀取資訊並加以處理。</span><span class="sxs-lookup"><span data-stu-id="74014-118">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="74014-119">系統將從訊息佇列管理員讀取訊息，並且在即將處理的訊息佇列通道中向上傳遞。</span><span class="sxs-lookup"><span data-stu-id="74014-119">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="74014-120">訊息佇列通道就會成為 WCF 通道堆疊中的佇列管理員。</span><span class="sxs-lookup"><span data-stu-id="74014-120">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="74014-121">如果透過訊息佇列通道傳送訊息，寄件者將無法控制從佇列管理員接收的位元組。</span><span class="sxs-lookup"><span data-stu-id="74014-121">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="74014-122">如果接收處理序無法讀取未經處理的位元組，接收的訊息格式將會呈現錯誤而且無法處理。系統會假設接收處理序能夠將接收的位元組轉譯回可用的格式。</span><span class="sxs-lookup"><span data-stu-id="74014-122">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
