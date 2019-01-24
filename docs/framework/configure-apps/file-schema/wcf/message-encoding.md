---
title: 訊息編碼
ms.date: 03/30/2017
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
ms.openlocfilehash: d797b810af5df5fc1acf31e0ab6338689da9f55c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734009"
---
# <a name="message-encoding"></a><span data-ttu-id="1277c-102">訊息編碼</span><span class="sxs-lookup"><span data-stu-id="1277c-102">Message Encoding</span></span>
<span data-ttu-id="1277c-103">編碼是將一組 Unicode 字元轉換成位元組序列的處理程序。</span><span class="sxs-lookup"><span data-stu-id="1277c-103">Encoding is the process of transforming a set of Unicode characters into a sequence of bytes.</span></span> <span data-ttu-id="1277c-104">解碼則是相反的處理序。</span><span class="sxs-lookup"><span data-stu-id="1277c-104">Decoding is the reverse process.</span></span> <span data-ttu-id="1277c-105">Windows Communication Foundation (WCF) 包含三種類型的 SOAP 訊息的編碼方式：文字、 二進位和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="1277c-105">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="1277c-106">`binaryMessageEncoding` 組態區段會指定用於二進位 XML 訊息的字元編碼和訊息版本處理。</span><span class="sxs-lookup"><span data-stu-id="1277c-106">The `binaryMessageEncoding` configuration section specifies the character encoding and message versioning used for binary-based XML messages.</span></span> <span data-ttu-id="1277c-107">二進位訊息編碼器會以二進位編碼網路上的 Windows Communication Foundation (WCF) 訊息。</span><span class="sxs-lookup"><span data-stu-id="1277c-107">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="1277c-108">雖然這個編碼會讓訊息傳輸速度非常快，但是會失去以 WS-\* 標準為基礎的互通性 (Interoperability)。</span><span class="sxs-lookup"><span data-stu-id="1277c-108">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
 <span data-ttu-id="1277c-109">`mtomMessageEncoding` 組態區段會指定字元編碼方式和訊息版本處理，用於使用訊息傳輸最佳化機制 (MTOM) 編碼方式的訊息。</span><span class="sxs-lookup"><span data-stu-id="1277c-109">The `mtomMessageEncoding` configuration section specifies the character encoding and message versioning used for a message using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="1277c-110">(MTOM) 是在 Windows Communication Foundation (WCF) 訊息中傳輸二進位資料的有效技術。</span><span class="sxs-lookup"><span data-stu-id="1277c-110">(MTOM) is an efficient technology for transmitting binary data in Windows Communication Foundation (WCF) messages.</span></span> <span data-ttu-id="1277c-111">MTOM 編碼器會嘗試在效率和互通性之間保持平衡。</span><span class="sxs-lookup"><span data-stu-id="1277c-111">The MTOM encoder attempts to strike a balance between efficiency and interoperability.</span></span> <span data-ttu-id="1277c-112">MTOM 編碼方式會以文字格式傳輸大部分的 XML，但是在傳輸大型區塊的二進位資料時，會依照原狀來傳送 (不轉換成文字)，好讓這些資料最佳化。</span><span class="sxs-lookup"><span data-stu-id="1277c-112">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to text.</span></span>  
  
 <span data-ttu-id="1277c-113">`textMessageEncoding` 組態區段會指定文字編碼器，以用於建立網路上的文字訊息。</span><span class="sxs-lookup"><span data-stu-id="1277c-113">The `textMessageEncoding` configuration section specifies a text encoder used to create text-based messages on the wire.</span></span> <span data-ttu-id="1277c-114">此編碼器產生的訊息適合 WS-\* 型的互通性。</span><span class="sxs-lookup"><span data-stu-id="1277c-114">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="1277c-115">Web 服務或 Web 服務用戶端通常可以了解文字 XML。</span><span class="sxs-lookup"><span data-stu-id="1277c-115">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="1277c-116">不過，若要針對 XML 訊息進行編碼，將大型二進位資料區塊當做文字傳輸是效率最差的方法。</span><span class="sxs-lookup"><span data-stu-id="1277c-116">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1277c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1277c-117">See also</span></span>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- [<span data-ttu-id="1277c-118">繫結</span><span class="sxs-lookup"><span data-stu-id="1277c-118">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1277c-119">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="1277c-119">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1277c-120">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="1277c-120">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1277c-121">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1277c-121">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="1277c-122">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="1277c-122">Choosing a Message Encoder</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)
