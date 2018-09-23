---
title: 訊息通訊協定
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 7d94b917f3d8d2fd7faed28b9320edc240724e0b
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703007"
---
# <a name="messaging-protocols"></a><span data-ttu-id="143a7-102">訊息通訊協定</span><span class="sxs-lookup"><span data-stu-id="143a7-102">Messaging Protocols</span></span>

<span data-ttu-id="143a7-103">Windows Communication Foundation (WCF) 通道堆疊利用編碼和傳輸通道轉換為其 wire 格式的內部訊息表示法，並將其傳送使用特定的傳輸。</span><span class="sxs-lookup"><span data-stu-id="143a7-103">The Windows Communication Foundation (WCF) channel stack employs encoding and transport channels to transform internal message representation into its wire format and send it by using a particular transport.</span></span> <span data-ttu-id="143a7-104">最常用於 Web 服務互通性的傳輸為 HTTP，而 Web 服務最常用的編碼為 XML 架構的 SOAP 1.1、SOAP 1.2 和訊息傳輸最佳化機制 (MTOM)。</span><span class="sxs-lookup"><span data-stu-id="143a7-104">The most common transport used for Web services interoperability is HTTP, and the most common encodings used by Web services are XML-based SOAP 1.1, SOAP 1.2, and Message Transmission Optimization Mechanism (MTOM).</span></span>

<span data-ttu-id="143a7-105">本主題涵蓋 WCF 實作詳細資料，如下列所採用的通訊協定<xref:System.ServiceModel.Channels.HttpTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="143a7-105">This topic covers WCF implementation details for the following protocols employed by <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.</span></span>

<span data-ttu-id="143a7-106">規格/文件：</span><span class="sxs-lookup"><span data-stu-id="143a7-106">Specification/document:</span></span>

- [<span data-ttu-id="143a7-107">HTTP 1.1</span><span class="sxs-lookup"><span data-stu-id="143a7-107">HTTP 1.1</span></span>](https://www.ietf.org/rfc/rfc2616.txt)
- <span data-ttu-id="143a7-108">[SOAP 1.1 HTTP 繫結](https://www.w3.org/TR/2000/NOTE-SOAP-20000508)，第 7 節</span><span class="sxs-lookup"><span data-stu-id="143a7-108">[SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7</span></span>
- <span data-ttu-id="143a7-109">[SOAP 1.2 HTTP 繫結](https://www.w3.org/TR/soap12-part2)第 7 節</span><span class="sxs-lookup"><span data-stu-id="143a7-109">[SOAP 1.2 HTTP Binding](https://www.w3.org/TR/soap12-part2) Section 7</span></span>

<span data-ttu-id="143a7-110">本主題涵蓋 WCF 實作詳細資料，如下列通訊協定<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>和<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>採用。</span><span class="sxs-lookup"><span data-stu-id="143a7-110">This topic covers WCF implementation details for the following protocols  that <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> and <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employ.</span></span>

<span data-ttu-id="143a7-111">規格/文件：</span><span class="sxs-lookup"><span data-stu-id="143a7-111">Specification/Document:</span></span>

- [<span data-ttu-id="143a7-112">XML</span><span class="sxs-lookup"><span data-stu-id="143a7-112">XML</span></span>](https://www.w3.org/TR/REC-xml)
- [<span data-ttu-id="143a7-113">SOAP 1.1</span><span class="sxs-lookup"><span data-stu-id="143a7-113">SOAP 1.1</span></span>](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [<span data-ttu-id="143a7-114">SOAP 1.2 核心</span><span class="sxs-lookup"><span data-stu-id="143a7-114">SOAP 1.2 Core</span></span>](https://www.w3.org/TR/soap12-part1/)
- [<span data-ttu-id="143a7-115">Ws-addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="143a7-115">WS-Addressing 2004/08</span></span>](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [<span data-ttu-id="143a7-116">W3C Web 服務定址 1.0-核心</span><span class="sxs-lookup"><span data-stu-id="143a7-116">W3C Web Services Addressing 1.0 - Core</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [<span data-ttu-id="143a7-117">W3C Web 服務定址 1.0-SOAP 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-117">W3C Web Services Addressing 1.0 - SOAP Binding</span></span>](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [<span data-ttu-id="143a7-118">W3C Web 服務定址 1.0-WSDL 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-118">W3C Web Services Addressing 1.0 - WSDL Binding</span></span>](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [<span data-ttu-id="143a7-119">W3C Web 服務定址 1.0-中繼資料</span><span class="sxs-lookup"><span data-stu-id="143a7-119">W3C Web Services Addressing 1.0 - Metadata</span></span>](https://www.w3.org/TR/ws-addr-metadata/)
- [<span data-ttu-id="143a7-120">WSDL SOAP1.1 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-120">WSDL SOAP1.1 Binding</span></span>](https://www.w3.org/TR/wsdl/)
- [<span data-ttu-id="143a7-121">WSDL SOAP1.2 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-121">WSDL SOAP1.2 Binding</span></span>](https://www.w3.org/Submission/wsdl11soap12/)

<span data-ttu-id="143a7-122">本主題涵蓋 WCF 實作詳細資料，如下列通訊協定<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>採用。</span><span class="sxs-lookup"><span data-stu-id="143a7-122">This topic covers WCF implementation details for the following protocols that <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> employs.</span></span>

<span data-ttu-id="143a7-123">規格/文件：</span><span class="sxs-lookup"><span data-stu-id="143a7-123">Specification/document:</span></span>

- [<span data-ttu-id="143a7-124">XOP</span><span class="sxs-lookup"><span data-stu-id="143a7-124">XOP</span></span>](https://www.w3.org/TR/xop10/)
- [<span data-ttu-id="143a7-125">MTOM + SOAP 1.2 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-125">MTOM + SOAP 1.2 Binding</span></span>](https://www.w3.org/TR/soap12-mtom/)
- [<span data-ttu-id="143a7-126">MTOM SOAP 1.1 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-126">MTOM SOAP 1.1 Binding</span></span>](https://www.w3.org/Submission/soap11mtom10/)
- [<span data-ttu-id="143a7-127">MTOM Ws-policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="143a7-127">MTOM WS-Policy Assertion</span></span>](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

<span data-ttu-id="143a7-128">在本主題中使用的下列 XML 命名空間和相關聯的前置詞：</span><span class="sxs-lookup"><span data-stu-id="143a7-128">The following XML namespaces and associated prefixes are used throughout this topic:</span></span>

<span data-ttu-id="143a7-129">|前置詞 |命名空間統一資源識別元 (URI) |[---|---| | s11 |`http://schemas.xmlsoap.org/soap/envelope`| | s12 |`http://www.w3.org/2003/05/soap-envelope`| | wsa |`http://www.w3.org/2004/08/addressing`| | wsam |`http://www.w3.org/2007/05/addressing/metadata`| | wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing`| | wsa10 |`http://www.w3.org/2005/08/addressing`| | wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl`| | xop |`http://www.w3.org/2004/08/xop/include`| | xmime |`http://www.w3.org/2004/06/xmlmime`</span><span class="sxs-lookup"><span data-stu-id="143a7-129">|Prefix|Namespace Uniform Resource Identifier (URI)| [------------|---------------------------------------------------| |s11|`http://schemas.xmlsoap.org/soap/envelope`| |s12|`http://www.w3.org/2003/05/soap-envelope`| |wsa|`http://www.w3.org/2004/08/addressing`| |wsam|`http://www.w3.org/2007/05/addressing/metadata`| |wsap|`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing`| |wsa10|`http://www.w3.org/2005/08/addressing`| |wsaw10|`http://www.w3.org/2006/05/addressing/wsdl`| |xop|`http://www.w3.org/2004/08/xop/include`| |xmime|`http://www.w3.org/2004/06/xmlmime`</span></span><br /><br /> <span data-ttu-id="143a7-130">`http://www.w3.org/2005/05/xmlmime`| | dp |`http://schemas.microsoft.com/net/2006/06/duplex`|</span><span class="sxs-lookup"><span data-stu-id="143a7-130">`http://www.w3.org/2005/05/xmlmime`| |dp|`http://schemas.microsoft.com/net/2006/06/duplex`|</span></span>

## <a name="soap-11-and-soap-12"></a><span data-ttu-id="143a7-131">SOAP 1.1 和 SOAP 1.2</span><span class="sxs-lookup"><span data-stu-id="143a7-131">SOAP 1.1 and SOAP 1.2</span></span>

### <a name="envelope-and-processing-model"></a><span data-ttu-id="143a7-132">封套和處理模型</span><span class="sxs-lookup"><span data-stu-id="143a7-132">Envelope and Processing Model</span></span>
<span data-ttu-id="143a7-133">WCF 實作 SOAP 1.1 封套，以處理下列 Basic Profile 1.1 (BP11) 和 Basic Profile 1.0 (SSBP10)。</span><span class="sxs-lookup"><span data-stu-id="143a7-133">WCF implements SOAP 1.1 envelope processing following Basic Profile 1.1 (BP11) and Basic Profile 1.0 (SSBP10).</span></span> <span data-ttu-id="143a7-134">SOAP 1.2 封套處理實作了下列 SOAP12-Part1。</span><span class="sxs-lookup"><span data-stu-id="143a7-134">SOAP 1.2 Envelope processing is implemented following SOAP12-Part1.</span></span>

<span data-ttu-id="143a7-135">本章節將說明 WCF 對於 BP11 和 SOAP12-Part1 所採取的某些實作選項。</span><span class="sxs-lookup"><span data-stu-id="143a7-135">This section explains certain implementation choices taken by WCF with regard to BP11 and SOAP12-Part1.</span></span>

#### <a name="mandatory-header-processing"></a><span data-ttu-id="143a7-136">強制處理標頭</span><span class="sxs-lookup"><span data-stu-id="143a7-136">Mandatory Header Processing</span></span>
<span data-ttu-id="143a7-137">WCF 會遵循規則處理標頭標示`mustUnderstand`在 SOAP 1.1 和 SOAP 1.2 規格中，下列變化所述。</span><span class="sxs-lookup"><span data-stu-id="143a7-137">WCF follows rules for processing headers marked `mustUnderstand` described in the SOAP 1.1 and SOAP 1.2 specifications, with the following variations.</span></span>

<span data-ttu-id="143a7-138">輸入 WCF 通道堆疊的訊息是由個別的通道相關聯的繫結項目，例如設定、 文字訊息編碼、 安全性、 可靠傳訊和交易處理。</span><span class="sxs-lookup"><span data-stu-id="143a7-138">A message that enters the WCF channel stack is processed by individual channels configured by associated binding elements, for example, Text Message Encoding, Security, Reliable Messaging, and Transactions.</span></span> <span data-ttu-id="143a7-139">每個通道都會從關聯的命名空間辨識標頭，並將其標記為已辨識。</span><span class="sxs-lookup"><span data-stu-id="143a7-139">Each channel recognizes headers from the associated namespace and marks them as understood.</span></span> <span data-ttu-id="143a7-140">一旦訊息進入發送器，作業格式器便會讀取對應之訊息/作業合約所需的標頭，並將其標記為已辨識。</span><span class="sxs-lookup"><span data-stu-id="143a7-140">Once a message enters the dispatcher, the operation formatter reads headers expected by the corresponding message/operation contract and marks them understood.</span></span> <span data-ttu-id="143a7-141">接著發送器便會檢查是否有任何剩餘之未辨識，但標記為 `mustUnderstand` 的標頭，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="143a7-141">Then the dispatcher verifies whether any remaining headers are not understood but marked as `mustUnderstand` and throws an exception.</span></span> <span data-ttu-id="143a7-142">包含 `mustUnderstand` 標頭的訊息會以尚未由收件者應用程式碼處理的收件者為目標。</span><span class="sxs-lookup"><span data-stu-id="143a7-142">Messages that contain `mustUnderstand` headers that are targeted at the recipient are not processed by recipient application code.</span></span>

<span data-ttu-id="143a7-143">此類分層式處理可將 SOAP 節點的基礎結構層與應用程式層分割：</span><span class="sxs-lookup"><span data-stu-id="143a7-143">Such layered processing allows for separation between infrastructure layers and application layers of the SOAP node:</span></span>

- <span data-ttu-id="143a7-144">B1111： 無法辨識的標頭會偵測到由 WCF 基礎結構通道堆疊中，處理訊息之後但在應用程式處理之前</span><span class="sxs-lookup"><span data-stu-id="143a7-144">B1111: Headers that are not understood are detected after the message is processed by the WCF infrastructure channel stack, but before it is processed by application</span></span>

     <span data-ttu-id="143a7-145">SOAP 1.1 和 SOAP 1.2 之間的 `mustUnderstand` 標頭值不同。</span><span class="sxs-lookup"><span data-stu-id="143a7-145">The `mustUnderstand` header value differs between SOAP 1.1 and SOAP 1.2.</span></span> <span data-ttu-id="143a7-146">Basic Profile 1.1 要求 SOAP 1.1 訊息的 `mustUnderstand` 值必須為 0 或 1。</span><span class="sxs-lookup"><span data-stu-id="143a7-146">Basic Profile 1.1 requires that the `mustUnderstand` value be 0 or 1 for SOAP 1.1 messages.</span></span> <span data-ttu-id="143a7-147">SOAP 1.2 允許 0、1、`false` 和 `true` 等值，但建議發出 `xs:boolean` 值的標準表示 (`false`、`true`)。</span><span class="sxs-lookup"><span data-stu-id="143a7-147">SOAP 1.2 allows 0, 1, `false`, and `true` as values, but recommends emitting a canonical representation of `xs:boolean` values (`false`, `true`).</span></span>

- <span data-ttu-id="143a7-148">B1112: WCF 所發出`mustUnderstand`值 0，1 表示 SOAP 1.1 和 SOAP 1.2 版的 SOAP 封套。</span><span class="sxs-lookup"><span data-stu-id="143a7-148">B1112: WCF emits `mustUnderstand` values 0 and 1 for both SOAP 1.1 and SOAP 1.2 versions of the SOAP envelope.</span></span> <span data-ttu-id="143a7-149">WCF 會接受的整個值空間`xs:boolean`for`mustUnderstand`標頭 (0、 1、 `false`， `true`)</span><span class="sxs-lookup"><span data-stu-id="143a7-149">WCF accepts the entire value space of `xs:boolean` for the `mustUnderstand` header (0, 1, `false`, `true`)</span></span>

#### <a name="soap-faults"></a><span data-ttu-id="143a7-150">SOAP 錯誤</span><span class="sxs-lookup"><span data-stu-id="143a7-150">SOAP Faults</span></span>
<span data-ttu-id="143a7-151">下列是 WCF 特定 SOAP 錯誤實作的清單。</span><span class="sxs-lookup"><span data-stu-id="143a7-151">The following is a list of WCF-specific SOAP fault implementations.</span></span>

- <span data-ttu-id="143a7-152">B2121: WCF 會傳回下列的 SOAP 1.1 錯誤代碼： `s11:mustUnderstand`， `s11:Client`，和`s11:Server`。</span><span class="sxs-lookup"><span data-stu-id="143a7-152">B2121: WCF returns the following SOAP 1.1 Fault Codes: `s11:mustUnderstand`, `s11:Client`, and `s11:Server`.</span></span>

- <span data-ttu-id="143a7-153">B2122: WCF 會傳回下列 SOAP 1.2 錯誤碼： `s12:MustUnderstand`， `s12:Sender`，和`s12:Receiver`。</span><span class="sxs-lookup"><span data-stu-id="143a7-153">B2122: WCF returns the following SOAP 1.2 Fault Codes: `s12:MustUnderstand`, `s12:Sender`, and `s12:Receiver`.</span></span>

### <a name="http-binding"></a><span data-ttu-id="143a7-154">HTTP 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-154">HTTP Binding</span></span>

#### <a name="soap-11-http-binding"></a><span data-ttu-id="143a7-155">SOAP 1.1 HTTP 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-155">SOAP 1.1 HTTP Binding</span></span>
<span data-ttu-id="143a7-156">WCF 實作 SOAP1.1 HTTP 繫結 Basic Profile 1.1 規格 3.4 節，以下列說明：</span><span class="sxs-lookup"><span data-stu-id="143a7-156">WCF implements SOAP1.1 HTTP binding following the Basic Profile 1.1 specification section 3.4 with the following clarifications:</span></span>

- <span data-ttu-id="143a7-157">B2211: WCF 服務不會實作 HTTP POST 要求重新導向。</span><span class="sxs-lookup"><span data-stu-id="143a7-157">B2211: WCF service does not implement redirection of HTTP POST requests.</span></span>

- <span data-ttu-id="143a7-158">B2212: WCF 用戶端支援 HTTP Cookie 3.4.8。</span><span class="sxs-lookup"><span data-stu-id="143a7-158">B2212: WCF clients support HTTP Cookies in accordance with 3.4.8.</span></span>

#### <a name="soap-12-http-binding"></a><span data-ttu-id="143a7-159">SOAP 1.2 HTTP 繫結</span><span class="sxs-lookup"><span data-stu-id="143a7-159">SOAP 1.2 HTTP Binding</span></span>
<span data-ttu-id="143a7-160">SOAP 1.2-part 2 (SOAP12Part2) 規格以下列說明中所述，WCF 會實作 SOAP 1.2 HTTP 繫結。</span><span class="sxs-lookup"><span data-stu-id="143a7-160">WCF implements SOAP 1.2 HTTP binding as described in the SOAP 1.2-part 2 (SOAP12Part2) specification with the following clarifications.</span></span>

<span data-ttu-id="143a7-161">SOAP 1.2 為 `application/soap+xml` 媒體類型引入了選擇性的動作參數。</span><span class="sxs-lookup"><span data-stu-id="143a7-161">SOAP 1.2 introduced an optional action parameter for the `application/soap+xml` media type.</span></span> <span data-ttu-id="143a7-162">這個參數對於最佳化訊息分派非常有用，不需要在未使用 WS-Addressing 的情況下剖析 SOAP 訊息的主體。</span><span class="sxs-lookup"><span data-stu-id="143a7-162">This parameter is useful to optimize message dispatch without requiring that the body of the SOAP message be parsed when WS-Addressing is not used.</span></span>

- <span data-ttu-id="143a7-163">R2221：在 SOAP 1.2 要求上呈現時，`application/soap+xml` 動作參數必須符合對應 WSDL 繫結內部之 `soapAction` 項目的 `wsoap12:operation` 屬性。</span><span class="sxs-lookup"><span data-stu-id="143a7-163">R2221: The `application/soap+xml` action parameter, when present on a SOAP 1.2 request, must match the `soapAction` attribute on the `wsoap12:operation` element inside the corresponding WSDL binding.</span></span>

- <span data-ttu-id="143a7-164">R2222：在 SOAP 1.2 訊息上呈現時，若使用了 WS-Addressing 2004/08 或 WS-Addressing 1.0，則 `application/soap+xml` 動作參數必須符合 `wsa:Action`。</span><span class="sxs-lookup"><span data-stu-id="143a7-164">R2222: The `application/soap+xml` action parameter, when present on a SOAP 1.2 message, must match `wsa:Action` when WS-Addressing 2004/08 or WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="143a7-165">當 WS-Addressing 已停用，且傳入的要求未包含動作參數時，訊息 `Action` 會視為未指定。</span><span class="sxs-lookup"><span data-stu-id="143a7-165">When WS-Addressing is disabled and an incoming request does not contain an action parameter, message `Action` is considered not specified.</span></span>

## <a name="ws-addressing"></a><span data-ttu-id="143a7-166">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="143a7-166">WS-Addressing</span></span>
<span data-ttu-id="143a7-167">WCF 實作 3 個 Ws-addressing 版本：</span><span class="sxs-lookup"><span data-stu-id="143a7-167">WCF implements 3 versions of WS-Addressing:</span></span>

- <span data-ttu-id="143a7-168">WS-Addressing 2004/08</span><span class="sxs-lookup"><span data-stu-id="143a7-168">WS-Addressing 2004/08</span></span>

- <span data-ttu-id="143a7-169">W3C Web 服務定址 1.0 核心 (ADDR10-CORE) 和 SOAP 繫結 (ADDR10-SOAP)</span><span class="sxs-lookup"><span data-stu-id="143a7-169">W3C Web Services Addressing 1.0 Core  (ADDR10-CORE) and SOAP Binding (ADDR10-SOAP)</span></span>

- <span data-ttu-id="143a7-170">WS-Addressing 1.0 - 中繼資料</span><span class="sxs-lookup"><span data-stu-id="143a7-170">WS-Addressing 1.0 - Metadata</span></span>

### <a name="endpoint-references"></a><span data-ttu-id="143a7-171">端點參考</span><span class="sxs-lookup"><span data-stu-id="143a7-171">Endpoint References</span></span>
<span data-ttu-id="143a7-172">所有版本的 Ws-addressing 可實作 WCF 都使用了端點參考來描述端點。</span><span class="sxs-lookup"><span data-stu-id="143a7-172">All versions of WS-Addressing that WCF implements use endpoint references to describe endpoints.</span></span>

#### <a name="endpoint-references-and-ws-addressing-versions"></a><span data-ttu-id="143a7-173">端點參考和 WS-Addressing 版本</span><span class="sxs-lookup"><span data-stu-id="143a7-173">Endpoint References and WS-Addressing Versions</span></span>
<span data-ttu-id="143a7-174">WCF 會實作一些使用 Ws-addressing 的基礎結構通訊協定，特別`EndpointReference`項目和`W3C.WsAddressing.EndpointReferenceType`類別 （比方說，WS-ReliableMessaging、 Ws-secureconversation 和 Ws-trust）。</span><span class="sxs-lookup"><span data-stu-id="143a7-174">WCF implements a number of the infrastructure protocols that use WS-Addressing and in particular the `EndpointReference` element and `W3C.WsAddressing.EndpointReferenceType` class (for example, WS-ReliableMessaging, WS-SecureConversation, and WS-Trust).</span></span> <span data-ttu-id="143a7-175">WCF 支援任一版本的 Ws-addressing 與其他基礎結構通訊協定的使用。</span><span class="sxs-lookup"><span data-stu-id="143a7-175">WCF supports the use of either version of WS-Addressing with other infrastructure protocols.</span></span> <span data-ttu-id="143a7-176">WCF 端點支援每個端點的 Ws-addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="143a7-176">WCF endpoints support one version of WS-Addressing per endpoint.</span></span>

<span data-ttu-id="143a7-177">若是 R3111 的命名空間`EndpointReference`項目或與 WCF 端點交換訊息中所使用的型別必須符合 Ws-addressing 由此端點所實作的版本。</span><span class="sxs-lookup"><span data-stu-id="143a7-177">For R3111, the namespace for the `EndpointReference` element or type used in messages exchanged with a WCF endpoint must match the version of WS-Addressing implemented by this endpoint.</span></span>

<span data-ttu-id="143a7-178">比方說，如果 WCF 端點實作了 WS-ReliableMessaging，`AcksTo`內的這類端點所傳回的標頭`CreateSequenceResponse`使用 Ws-addressing 版本，`EncodingBinding`項目會指定這個端點。</span><span class="sxs-lookup"><span data-stu-id="143a7-178">For example, if a WCF endpoint implements WS-ReliableMessaging, the `AcksTo` header returned by such an endpoint inside `CreateSequenceResponse` uses the WS-Addressing version that the `EncodingBinding` element specifies for this endpoint.</span></span>

#### <a name="endpoint-references-and-metadata"></a><span data-ttu-id="143a7-179">端點參考和中繼資料</span><span class="sxs-lookup"><span data-stu-id="143a7-179">Endpoint References and Metadata</span></span>
<span data-ttu-id="143a7-180">有許多案例都需要與中繼資料通訊，或需要參考指定之端點的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="143a7-180">A number of scenarios require communicating metadata or a reference to metadata for a given endpoint.</span></span>

<span data-ttu-id="143a7-181">B3121: WCF 會採用 Ws-metadataexchange (MEX) 規格第 6 節，以傳值或傳址包含端點參考的中繼資料中所述的機制。</span><span class="sxs-lookup"><span data-stu-id="143a7-181">B3121: WCF employs mechanisms described in the WS-MetadataExchange (MEX) specification Section 6 to include metadata for endpoint references by value or by reference.</span></span>

<span data-ttu-id="143a7-182">假設 WCF 服務需要使用在權杖簽發者所發出的安全性判斷提示標記語言 (SAML) 權杖進行驗證的 `http://sts.fabrikam123.com` 。</span><span class="sxs-lookup"><span data-stu-id="143a7-182">Consider a scenario where a WCF service requires authentication using a Security Assertions Markup Language (SAML) token issued by the token issuer at `http://sts.fabrikam123.com`.</span></span> <span data-ttu-id="143a7-183">WCF 端點使用中描述這項驗證需求`sp:IssuedToken`含有巢狀判斷提示`sp:Issuer`指向權杖簽發者的判斷提示。</span><span class="sxs-lookup"><span data-stu-id="143a7-183">The WCF endpoint describes this authentication requirement by using `sp:IssuedToken` assertion with a nested `sp:Issuer` assertion pointing to the token issuer.</span></span> <span data-ttu-id="143a7-184">存取 `sp:Issuer` 判斷提示的用戶端應用程式必須知道如何與權杖簽發者端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="143a7-184">Client applications that access the `sp:Issuer` assertion need to know how to communicate with the token issuer endpoint.</span></span> <span data-ttu-id="143a7-185">用戶端需要知道與權杖簽發者有關的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="143a7-185">The client needs to know metadata about the token issuer.</span></span> <span data-ttu-id="143a7-186">使用 MEX 中定義的端點參考中繼資料延伸模組，WCF 會提供權杖簽發者中繼資料的參考。</span><span class="sxs-lookup"><span data-stu-id="143a7-186">Using the endpoint reference metadata extensions defined in MEX, WCF provides a reference to the token issuer metadata.</span></span>

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a><span data-ttu-id="143a7-187">訊息定址標頭</span><span class="sxs-lookup"><span data-stu-id="143a7-187">Message Addressing Headers</span></span>

#### <a name="message-headers"></a><span data-ttu-id="143a7-188">訊息標頭</span><span class="sxs-lookup"><span data-stu-id="143a7-188">Message Headers</span></span>
<span data-ttu-id="143a7-189">這兩個 Ws-addressing 版本，WCF 會使用下列的訊息標頭規格所規定`wsa:To`， `wsa:ReplyTo`， `wsa:Action`， `wsa:MessageID`，和`wsa:RelatesTo`。</span><span class="sxs-lookup"><span data-stu-id="143a7-189">For both WS-Addressing versions, WCF uses the following message headers as prescribed by the specifications `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`,and `wsa:RelatesTo`.</span></span>

<span data-ttu-id="143a7-190">B3211： 對於 Ws-addressing 的所有版本，WCF 會接受，但不會產生 Ws-addressing 訊息標頭`wsa:FaultTo`和`wsa:From`。</span><span class="sxs-lookup"><span data-stu-id="143a7-190">B3211: For all WS-Addressing versions, WCF honors, but does not produce out of the box, WS-Addressing message headers `wsa:FaultTo` and `wsa:From`.</span></span>

<span data-ttu-id="143a7-191">WCF 應用程式互動的應用程式可以將這些訊息標頭和 WCF 將會處理它們。</span><span class="sxs-lookup"><span data-stu-id="143a7-191">Applications that interact with WCF applications can add these message headers and WCF will process them accordingly.</span></span>

#### <a name="reference-parameters-and-properties"></a><span data-ttu-id="143a7-192">參考參數和屬性</span><span class="sxs-lookup"><span data-stu-id="143a7-192">Reference Parameters and Properties</span></span>

<span data-ttu-id="143a7-193">WCF 實作的端點參考參數和處理參考屬性的處理。</span><span class="sxs-lookup"><span data-stu-id="143a7-193">WCF implements processing of endpoint reference parameters and reference properties in accordance with respective specifications.</span></span>

<span data-ttu-id="143a7-194">B3221： 當設定為使用 Ws-addressing 2004/08，WCF 端點不會區分處理參考屬性和參考參數。</span><span class="sxs-lookup"><span data-stu-id="143a7-194">B3221: When configured to use WS-Addressing 2004/08, WCF endpoints do not differentiate between processing Reference Properties and Reference Parameters.</span></span>

### <a name="message-exchange-patterns"></a><span data-ttu-id="143a7-195">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="143a7-195">Message Exchange Patterns</span></span>
<span data-ttu-id="143a7-196">包含 Web 服務作業引動過程中的訊息順序稱為*訊息交換模式*。</span><span class="sxs-lookup"><span data-stu-id="143a7-196">The sequence of messages involved in the Web service operation invocation is referred to as the *message exchange pattern*.</span></span> <span data-ttu-id="143a7-197">WCF 支援單向、 要求-回覆和雙工訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="143a7-197">WCF supports one-way, request-reply, and duplex message exchange patterns.</span></span> <span data-ttu-id="143a7-198">本章節將根據所使用的訊息交換模式，釐清訊息處理上的 WS-Addressing 需求。</span><span class="sxs-lookup"><span data-stu-id="143a7-198">This section clarifies WS-Addressing requirements on message processing depending on the message exchange pattern being used.</span></span>

<span data-ttu-id="143a7-199">在本章節中，要求者會傳送第一個訊息，而回應程式將會接收第一個訊息。</span><span class="sxs-lookup"><span data-stu-id="143a7-199">Throughout this section, the requester sends the first message and the responder receives the first message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="143a7-200">單向訊息</span><span class="sxs-lookup"><span data-stu-id="143a7-200">One-Way Message</span></span>
<span data-ttu-id="143a7-201">當設定為支援訊息的 WCF 端點指定`Action`遵循單向模式，WCF 端點會遵循下列行為和需求。</span><span class="sxs-lookup"><span data-stu-id="143a7-201">When a WCF endpoint is configured to support messages with a given `Action` to follow a one-way pattern, the WCF endpoint follows the following behaviors and requirements.</span></span> <span data-ttu-id="143a7-202">除非另有指定，則行為和規則將套用這兩個版本的 Ws-addressing 在 WCF 中支援：</span><span class="sxs-lookup"><span data-stu-id="143a7-202">Unless otherwise specified, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="143a7-203">R3311：要求者必須加入由端點參考指定的 `wsa:To`、`wsa:Action` 和所有參考參數的標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-203">R3311: The requester must include `wsa:To`, `wsa:Action`, and headers for all reference parameters specified by the endpoint reference.</span></span> <span data-ttu-id="143a7-204">在使用了 WS-Addressing 2004/08，並且以端點參考指定 [reference properties] 時，也必須在訊息內加入對應的標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-204">When WS-Addressing 2004/08 is used and [reference properties] are specified by the endpoint reference, the corresponding headers must be added to the message too.</span></span>

- <span data-ttu-id="143a7-205">B3312：要求者可以加入 `MessageID`、`ReplyTo` 和 `FaultTo` 標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-205">B3312: The requester may include `MessageID`, `ReplyTo`, and `FaultTo` headers.</span></span> <span data-ttu-id="143a7-206">接收者的基礎結構將會忽略它們，並且會將它們傳遞給應用程式。</span><span class="sxs-lookup"><span data-stu-id="143a7-206">The receiver infrastructure will ignore them, and they will be passed to the application.</span></span>

- <span data-ttu-id="143a7-207">R3313：使用了 HTTP，而且沒有訊息在 HTTP 回應階段傳送時，回應程式必須傳送一個含有空主體的 HTTP 回應以及 HTTP 202 狀態碼。</span><span class="sxs-lookup"><span data-stu-id="143a7-207">R3313: When HTTP is used and no message is being sent on the HTTP response leg, the responder must send an HTTP response with an empty body and an HTTP 202 status code.</span></span>

     <span data-ttu-id="143a7-208">當使用 HTTP 傳輸，而且作業合約宣告訊息為單向時，HTTP 回應仍舊可以用來傳送基礎結構訊息，例如，HTTP 回應上的可靠訊息可以傳送 `SequenceAcknowledgement` 訊息。</span><span class="sxs-lookup"><span data-stu-id="143a7-208">When the HTTP transport is in use and the operation contract declares a message one-way, the HTTP response can still be used for sending infrastructure messages—for example, reliable messaging can send a `SequenceAcknowledgement` message on an HTTP response.</span></span>

- <span data-ttu-id="143a7-209">B3314: WCF 回應程式不會在回應單向訊息傳送的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="143a7-209">B3314: The WCF responder does not send a fault message in response to a one-way message.</span></span>

#### <a name="request-reply"></a><span data-ttu-id="143a7-210">要求-回覆</span><span class="sxs-lookup"><span data-stu-id="143a7-210">Request-Reply</span></span>
<span data-ttu-id="143a7-211">當設定的 WCF 端點的訊息指定`Action`遵循要求-回覆模式，WCF 結束點前面接行為和需求。</span><span class="sxs-lookup"><span data-stu-id="143a7-211">When a WCF endpoint is configured for a message with a given `Action` to follow the request-reply pattern, the WCF endpoint follows the behaviors and requirements below.</span></span> <span data-ttu-id="143a7-212">除非另有指定，則行為和規則將套用這兩個版本的 Ws-addressing 在 WCF 中支援：</span><span class="sxs-lookup"><span data-stu-id="143a7-212">Unless specified otherwise, behaviors and rules apply for both versions of WS-Addressing supported in WCF:</span></span>

- <span data-ttu-id="143a7-213">R3321： 要求者必須在要求中包含`wsa:To`， `wsa:Action`， `wsa:MessageID`，和所有參考參數或參考屬性 （或兩者） 的端點參照所指定的標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-213">R3321: The requester must include in the request `wsa:To`, `wsa:Action`, `wsa:MessageID`, and headers for all reference parameters or reference properties (or both) specified by the endpoint reference.</span></span>

- <span data-ttu-id="143a7-214">R3322：使用 WS-Addressing 2004/08 時，`ReplyTo` 也必須包含在要求中。</span><span class="sxs-lookup"><span data-stu-id="143a7-214">R3322: When WS-Addressing 2004/08 is used, `ReplyTo` must also be included in the request.</span></span>

- <span data-ttu-id="143a7-215">R3323： 使用 Ws-addressing 1.0 時，`ReplyTo`不存在於要求中，使用等於 [address] 屬性的預設端點參考`http://www.w3.org/2005/08/addressing/anonymous`用。</span><span class="sxs-lookup"><span data-stu-id="143a7-215">R3323: When WS-Addressing 1.0 is used and `ReplyTo` is not present in the request, a default endpoint reference with the [address] property equal to `http://www.w3.org/2005/08/addressing/anonymous` is used.</span></span>

- <span data-ttu-id="143a7-216">R3324： 要求者必須包含`wsa:To`， `wsa:Action`，並`wsa:RelatesTo`回覆訊息中的標頭，以及所有的參考參數或參考屬性 （或兩者） 所指定的標頭`ReplyTo`中的端點參考要求。</span><span class="sxs-lookup"><span data-stu-id="143a7-216">R3324: The requester must include `wsa:To`, `wsa:Action`, and `wsa:RelatesTo` headers in the reply message, as well as headers for all reference parameters or reference properties (or both) specified by the `ReplyTo` endpoint reference in the request.</span></span>

### <a name="web-services-addressing-faults"></a><span data-ttu-id="143a7-217">Web 服務定址錯誤</span><span class="sxs-lookup"><span data-stu-id="143a7-217">Web Services Addressing Faults</span></span>
<span data-ttu-id="143a7-218">R3411: WCF 會產生下列由 Ws-addressing 2004/08 定義的錯誤。</span><span class="sxs-lookup"><span data-stu-id="143a7-218">R3411: WCF produces the following faults defined by WS-Addressing 2004/08.</span></span>

|<span data-ttu-id="143a7-219">程式碼</span><span class="sxs-lookup"><span data-stu-id="143a7-219">Code</span></span>|<span data-ttu-id="143a7-220">原因</span><span class="sxs-lookup"><span data-stu-id="143a7-220">Cause</span></span>|
|----------|-----------|
|`wsa:DestinationUnreachable`|<span data-ttu-id="143a7-221">訊息到達時如帶有 `ReplyTo`，其回覆位址與為此通道所建立的不同。</span><span class="sxs-lookup"><span data-stu-id="143a7-221">The message arrived with a `ReplyTo` that is different from the reply address established for this channel; there is no endpoint listening at the address specified in the To header.</span></span>|
|`wsa:ActionNotSupported`|<span data-ttu-id="143a7-222">與端點關聯的基礎結構通道或發送器，不會辨識 `Action` 標頭內指定的動作。</span><span class="sxs-lookup"><span data-stu-id="143a7-222">the infrastructure channels or dispatcher associated with the endpoint do not recognize the action specified in the `Action` header.</span></span>|

<span data-ttu-id="143a7-223">R3412: WCF 會產生下列由 Ws-addressing 1.0 定義的錯誤。</span><span class="sxs-lookup"><span data-stu-id="143a7-223">R3412: WCF produces the following faults defined by WS-Addressing 1.0.</span></span>

|<span data-ttu-id="143a7-224">程式碼</span><span class="sxs-lookup"><span data-stu-id="143a7-224">Code</span></span>|<span data-ttu-id="143a7-225">原因</span><span class="sxs-lookup"><span data-stu-id="143a7-225">Cause</span></span>|
|----------|-----------|
|`wsa10:InvalidAddressingHeader`|<span data-ttu-id="143a7-226">重複`wsa:To`， `wsa:ReplyTo`，`wsa:From`或`wsa:MessageID`。</span><span class="sxs-lookup"><span data-stu-id="143a7-226">Duplicate `wsa:To`, `wsa:ReplyTo`, `wsa:From` or `wsa:MessageID`.</span></span> <span data-ttu-id="143a7-227">重複`wsa:RelatesTo`具有相同`RelationshipType`。</span><span class="sxs-lookup"><span data-stu-id="143a7-227">Duplicate `wsa:RelatesTo` with the same `RelationshipType`.</span></span>|
|`wsa10:MessageAddressingHeaderRequired`|<span data-ttu-id="143a7-228">所需的定址標頭遺失。</span><span class="sxs-lookup"><span data-stu-id="143a7-228">The required Addressing header is missing.</span></span>|
|`wsa10:DestinationUnreachable`|<span data-ttu-id="143a7-229">以 `ReplyTo` 到達的訊息，其回覆位址與為此通道所建立的不同。</span><span class="sxs-lookup"><span data-stu-id="143a7-229">The message arrived with a `ReplyTo` that is different from the reply address established for this channel.</span></span> <span data-ttu-id="143a7-230">而且沒有端點可在 To 標頭內指定的位址上進行接聽。</span><span class="sxs-lookup"><span data-stu-id="143a7-230">There is no endpoint listening at the address specified in the To header.</span></span>|
|`wsa10:ActionNotSupported`|<span data-ttu-id="143a7-231">在 `Action` 標頭內指定的動作，不會由基礎結構通道或與端點關聯的發送器進行辨識。</span><span class="sxs-lookup"><span data-stu-id="143a7-231">An action specified in the `Action` header is not recognized by the infrastructure channels or dispatcher associated with the endpoint.</span></span>|
|`wsa10:EndpointUnavailable`|<span data-ttu-id="143a7-232">RM 通道會將此錯誤送回，指出端點將不會根據 `CreateSequence` 訊息之定址標頭檢查的順序進行處理。</span><span class="sxs-lookup"><span data-stu-id="143a7-232">The RM channel sends this fault back, indicating the endpoint will not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>|

<span data-ttu-id="143a7-233">之前表格中的程式碼對應至 SOAP 1.1 內的 `FaultCode` 和 SOAP 1.2 內的 `SubCode` (使用 Code=Sender)。</span><span class="sxs-lookup"><span data-stu-id="143a7-233">Code in the preceding tables maps to `FaultCode` in SOAP 1.1 and `SubCode` (with Code=Sender) in SOAP 1.2.</span></span>

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a><span data-ttu-id="143a7-234">WSDL 1.1 繫結和 WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="143a7-234">WSDL 1.1 Binding and WS-Policy Assertions</span></span>

#### <a name="indicating-use-of-ws-addressing"></a><span data-ttu-id="143a7-235">指出使用了 WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="143a7-235">Indicating Use of WS-Addressing</span></span>
<span data-ttu-id="143a7-236">WCF 會使用原則判斷提示來指出端點支援特定之 Ws-addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="143a7-236">WCF uses policy assertions to indicate endpoint support for a particular WS-Addressing version.</span></span>

<span data-ttu-id="143a7-237">下列原則判斷提示具有端點原則主體 [WS-PA]，並指出必須使用 WS-Addressing 2004/08，從端點傳送及接收訊息。</span><span class="sxs-lookup"><span data-stu-id="143a7-237">The following policy assertion has Endpoint Policy Subject [WS-PA] and indicates messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsap:UsingAddressing />
```

<span data-ttu-id="143a7-238">此原則判斷提示擴大了 WS-Addressing 2004/08 規格。</span><span class="sxs-lookup"><span data-stu-id="143a7-238">This policy assertion augments the WS-Addressing 2004/08 specification.</span></span>

<span data-ttu-id="143a7-239">下列原則判斷提示指出傳送/接收的訊息必須使用 WS-Addressing 1.0。</span><span class="sxs-lookup"><span data-stu-id="143a7-239">The following policy assertion this indicates that messages sent/received must use WS-Addressing 1.0.</span></span>

```xml
<wsam:Addressing/>
```

<span data-ttu-id="143a7-240">下列原則判斷提示具有端點原則主體 [WS-PA]，並指出必須使用 WS-Addressing 2004/08，從端點傳送及接收訊息。</span><span class="sxs-lookup"><span data-stu-id="143a7-240">The following policy assertion has an Endpoint Policy Subject [WS-PA] and indicates that messages sent and received from the endpoint must use WS-Addressing 2004/08.</span></span>

```xml
<wsaw10:UsingAddressing />
```

<span data-ttu-id="143a7-241">`wsaw10:UsingAddressing` 項目是從 [WS-Addressing-WSDL] 借用的，並且在 WS-Policy 的內容中使用，以符合該規格第 3.1.2 節的規範。</span><span class="sxs-lookup"><span data-stu-id="143a7-241">The `wsaw10:UsingAddressing` element is borrowed from [WS-Addressing-WSDL] and is used in the context of WS-Policy in compliance with that specification, section 3.1.2.</span></span>

<span data-ttu-id="143a7-242">使用定址不會改變 WSDL 1.1、SOAP 1.1 和 SOAP 1.2 HTTP 繫結的語意。</span><span class="sxs-lookup"><span data-stu-id="143a7-242">Use of Addressing does not alter the semantics of WSDL 1.1, SOAP 1.1, and SOAP 1.2 HTTP Bindings.</span></span> <span data-ttu-id="143a7-243">例如，若預期要回覆使用定址和 WSDL SOAP 1.x HTTP 繫結傳送至端點的要求，此回覆必須使用 HTTP 回應傳送。</span><span class="sxs-lookup"><span data-stu-id="143a7-243">For example, if a reply is expected to a request that is sent to an endpoint that uses Addressing and WSDL SOAP 1.x HTTP binding, the reply must be sent by using the HTTP response.</span></span>

<span data-ttu-id="143a7-244">若為透過 HTTP 回應傳送的回覆，WS-AM 判斷提示為：</span><span class="sxs-lookup"><span data-stu-id="143a7-244">For replies sent over the http response, the WS-AM assertion is:</span></span>

```xml
<wsam:AnonymousResponses/>
```

<span data-ttu-id="143a7-245">完整的原則判斷提示看起來可能像這樣：</span><span class="sxs-lookup"><span data-stu-id="143a7-245">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="143a7-246">不過，有一些訊息交換模式可從要求者和回應程式之間所建立的兩個獨立反向 HTTP 連線中獲益，例如，由回應程式所傳送之未經要求的單向訊息。</span><span class="sxs-lookup"><span data-stu-id="143a7-246">However, there are message exchange patterns that benefit from having two independent converse HTTP connections established between the requester and the responder, for example, unsolicited one-way messages sent by the responder.</span></span>

<span data-ttu-id="143a7-247">WCF 提供的兩個基礎傳輸通道可用以構成複合雙工通道，其中一個通道用於輸入訊息，而其他則用於輸出訊息的功能。</span><span class="sxs-lookup"><span data-stu-id="143a7-247">WCF offers a feature by which two underlying transport channels can form a Composite Duplex channel, where one channel is used for input messages and the other is used for output messages.</span></span> <span data-ttu-id="143a7-248">在使用 HTTP 傳輸的情況下，複合雙工提供了兩種反向的 HTTP 連線。</span><span class="sxs-lookup"><span data-stu-id="143a7-248">In the case of the HTTP Transport, Composite Duplex provides two converse HTTP connections.</span></span> <span data-ttu-id="143a7-249">要求者會使用其中一個連線傳送訊息給回應程式，而回應程式則使用另一個連線將訊息傳回給要求者。</span><span class="sxs-lookup"><span data-stu-id="143a7-249">The requester uses one connection to send messages to the responder, and the responder uses the other to send messages back to the requester.</span></span>

<span data-ttu-id="143a7-250">若為透過個別 HTTP 要求傳送的回覆，WS-AM 判斷提示為：</span><span class="sxs-lookup"><span data-stu-id="143a7-250">For replies sent over separate http requests, the ws-am assertion is</span></span>

```xml
<wsam:NonAnonymousResponses/>
```

<span data-ttu-id="143a7-251">完整的原則判斷提示看起來可能像這樣：</span><span class="sxs-lookup"><span data-stu-id="143a7-251">The complete policy assertion might look like this:</span></span>

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

<span data-ttu-id="143a7-252">下列具有端點原則主體 [WS-PA] 的判斷提示，在使用了 WSDL 1.1 SOAP 1.x HTTP 繫結的端點上使用時，會要求以個別的反向 HTTP 連線，將訊息在要求者和回應程式間傳送。</span><span class="sxs-lookup"><span data-stu-id="143a7-252">Use of the following assertion that has Endpoint Policy Subject [WS-PA] on endpoints that use WSDL 1.1 SOAP 1.x HTTP bindings requires two separate converse HTTP connections to be used for messages flowing from requester to responder and responder to requester, respectively.</span></span>

```xml
<cdp:CompositeDuplex/>
```

<span data-ttu-id="143a7-253">上一個陳述式會導致在要求訊息的 `wsa:ReplyTo` 標頭上，必須有以下需求：</span><span class="sxs-lookup"><span data-stu-id="143a7-253">The previous statement leads to the following requirements on the `wsa:ReplyTo` header for request messages:</span></span>

- <span data-ttu-id="143a7-254">R3514： 要求傳送至端點的訊息必須要有`ReplyTo`標頭`[address]`屬性不等於`http://www.w3.org/2005/08/addressing/anonymous`如果端點使用 WSDL 1.1 SOAP 1.x HTTP 繫結，並有替代的原則`wsap10:UsingAddressing`或`wsap:UsingAddressing`判斷提示搭配`cdp:CompositeDuplex`附加。</span><span class="sxs-lookup"><span data-stu-id="143a7-254">R3514: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property not equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with a `wsap10:UsingAddressing` or `wsap:UsingAddressing` assertion coupled with `cdp:CompositeDuplex` attached.</span></span>

- <span data-ttu-id="143a7-255">R3515： 要求傳送至端點的訊息必須要有`ReplyTo`標頭`[address]`屬性等於`http://www.w3.org/2005/08/addressing/anonymous`，或沒有`ReplyTo`標頭中，如果端點使用 WSDL 1.1 SOAP 1.x HTTP 繫結，並有替代的原則`wsap10:UsingAddressing`判斷提示，但沒有`cdp:CompositeDuplex`附加的判斷提示。</span><span class="sxs-lookup"><span data-stu-id="143a7-255">R3515: Request messages sent to an endpoint must have a `ReplyTo` header with the `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous`, or not have a `ReplyTo` header at all, if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap10:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

- <span data-ttu-id="143a7-256">R3516： 要求傳送至端點的訊息必須要有`ReplyTo`標頭`[address]`屬性等於`http://www.w3.org/2005/08/addressing/anonymous`如果端點使用 WSDL 1.1 SOAP 1.x HTTP 繫結，並有替代的原則`wsap:UsingAddressing`判斷提示，而且沒有`cdp:CompositeDuplex`連結的判斷提示。</span><span class="sxs-lookup"><span data-stu-id="143a7-256">R3516: Request messages sent to an endpoint must have a `ReplyTo` header with an `[address]` property equal to `http://www.w3.org/2005/08/addressing/anonymous` if the endpoint uses a WSDL 1.1 SOAP 1.x HTTP binding and has a policy alternative with `wsap:UsingAddressing` assertion and no `cdp:CompositeDuplex` assertion attached.</span></span>

<span data-ttu-id="143a7-257">WS-Addressing WSDL 規格會試圖描述類似的通訊協定繫結，藉由引入具有三種文字值 (必要項、選擇性和禁止) 的 `<wsaw:Anonymous/>` 項目，指出`wsa:ReplyTo` 標頭 (第 3.2 節) 上的需求。</span><span class="sxs-lookup"><span data-stu-id="143a7-257">The WS-addressing WSDL specification attempts to describe similar protocol bindings by introducing an element `<wsaw:Anonymous/>` with three textual values (required, optional, and prohibited) to indicate requirements on the `wsa:ReplyTo` header (section 3.2).</span></span> <span data-ttu-id="143a7-258">不巧的是，此類項目定義並無法特別當做 WS-Policy 內容的判斷提示使用，因為它需要網域專屬的延伸，以支援其他使用此類項目做為判斷提示的交集。</span><span class="sxs-lookup"><span data-stu-id="143a7-258">Unfortunately, such element definition is not particularly usable as an assertion in the context of WS-Policy, because it requires domain-specific extensions to support the intersection of alternatives using such an element as an assertion.</span></span> <span data-ttu-id="143a7-259">此類項目定義也指出了 `ReplyTo` 標頭的值，而非網路上的端點行為，如此將使其成為 HTTP 傳輸專屬的定義。</span><span class="sxs-lookup"><span data-stu-id="143a7-259">Such element definition also indicates the value of the `ReplyTo` header as opposed to the endpoint behavior on the wire, which makes it specific to HTTP transport.</span></span>

#### <a name="action-definition"></a><span data-ttu-id="143a7-260">動作定義</span><span class="sxs-lookup"><span data-stu-id="143a7-260">Action Definition</span></span>
<span data-ttu-id="143a7-261">WS-Addressing 2004/08 為 `wsa:Action` 項目定義了 `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` 屬性。</span><span class="sxs-lookup"><span data-stu-id="143a7-261">WS-Addressing 2004/08 defines a `wsa:Action` attribute for the `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements.</span></span> <span data-ttu-id="143a7-262">WS-Addressing 1.0 WSDL 繫結 (WS-ADDR10-WSDL) 定義了一個類似的屬性，即 `wsaw10:Action`。</span><span class="sxs-lookup"><span data-stu-id="143a7-262">WS-Addressing 1.0 WSDL Binding (WS-ADDR10-WSDL) defines a similar attribute, `wsaw10:Action`.</span></span>

<span data-ttu-id="143a7-263">兩者間的不同處就只是預設的動作模式語意，這些部分分別在 WS-ADDR 的第 3.3.2 節和 WS-ADDR10-WSDL 的第 4.4.4 節中描述。</span><span class="sxs-lookup"><span data-stu-id="143a7-263">The only difference between the two is the default Action pattern semantics described in section 3.3.2 of WS-ADDR and section 4.4.4 of WS-ADDR10-WSDL, respectively.</span></span>

<span data-ttu-id="143a7-264">很合理，有兩個端點共用相同`portType`（或合約，在 WCF 術語中），但使用不同的 Ws-addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="143a7-264">It is a reasonable to have two endpoints that share the same `portType` (or contract, in WCF terminology) but using different versions of WS-Addressing.</span></span> <span data-ttu-id="143a7-265">但考慮到該動作是由 `portType` 所定義，不應在實作 `portType` 的端點上變更，如此將難以支援兩種預設的動作模式。</span><span class="sxs-lookup"><span data-stu-id="143a7-265">But given that Action is defined by the `portType` and should not change across the endpoints that implement the `portType`, it becomes impossible to support both default action patterns.</span></span>

<span data-ttu-id="143a7-266">若要解決這個爭論，WCF 支援的單一版本`Action`屬性。</span><span class="sxs-lookup"><span data-stu-id="143a7-266">To resolve this controversy, WCF supports a single version of the `Action` attribute.</span></span>

<span data-ttu-id="143a7-267">B3521: WCF 會使用`wsaw10:Action`屬性`wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]`若要判斷 WS-ADDR10-WSDL 中定義的項目`Action`URI 對應的訊息，不論端點所使用的 Ws-addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="143a7-267">B3521: WCF uses the `wsaw10:Action` attribute on `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elements as defined in WS-ADDR10-WSDL to determine the `Action` URI for the corresponding messages irrespective of the WS-Addressing version used by the endpoint.</span></span>

#### <a name="use-endpoint-reference-inside-wsdl-port"></a><span data-ttu-id="143a7-268">使用 WSDL 連接埠內部的端點參考</span><span class="sxs-lookup"><span data-stu-id="143a7-268">Use Endpoint Reference Inside WSDL Port</span></span>
<span data-ttu-id="143a7-269">WS-ADDR10-WSDL 第 4.1 節將 `wsdl:port` 元素延伸為包含 `<wsa10:EndpointReference…/>` 子元素，以便使用 WS-Addressing 的詞彙描述端點。</span><span class="sxs-lookup"><span data-stu-id="143a7-269">WS-ADDR10-WSDL section 4.1 extends the `wsdl:port` element to include the `<wsa10:EndpointReference…/>` child element to describe the endpoint in WS-Addressing terms.</span></span> <span data-ttu-id="143a7-270">WCF 擴充上 Ws-addressing 2004/08，此公用程式可讓`<wsa:EndpointReference…/>`顯示為子項目`wsdl:port`。</span><span class="sxs-lookup"><span data-stu-id="143a7-270">WCF expands this utility on WS-Addressing 2004/08, allowing `<wsa:EndpointReference…/>` to appear as a child element of `wsdl:port`.</span></span>

- <span data-ttu-id="143a7-271">R3531：如果端點含有以 `<wsaw10:UsingAddressing/>`原則判斷提示取代之附加原則，則對應的 `wsdl:port` 項目可以包含一個子項目 `<wsa10:EndpointReference …/>`。</span><span class="sxs-lookup"><span data-stu-id="143a7-271">R3531: If an endpoint has an attached policy alternative with a `<wsaw10:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa10:EndpointReference …/>`.</span></span>

- <span data-ttu-id="143a7-272">R3532： 如果`wsdl:port`包含子元素`<wsa10:EndpointReference …/>`，則`wsa10:EndpointReference/wsa10:Address`子項目值必須符合的值`@address`屬性的同層級`wsdl:port` / `wsdl:location`項目。</span><span class="sxs-lookup"><span data-stu-id="143a7-272">R3532: If a `wsdl:port` contains a child element `<wsa10:EndpointReference …/>`, the `wsa10:EndpointReference/wsa10:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

- <span data-ttu-id="143a7-273">R3533：如果端點含有以 `<wsap:UsingAddressing/>` 原則判斷提示替代的附加原則，則對應的 `wsdl:port` 項目可以包含子項目 `<wsa:EndpointReference …/>`。</span><span class="sxs-lookup"><span data-stu-id="143a7-273">R3533: If an endpoint has an attached policy alternative with `<wsap:UsingAddressing/>` policy assertion, the corresponding `wsdl:port` element can contain a child element `<wsa:EndpointReference …/>`.</span></span>

- <span data-ttu-id="143a7-274">R3534： 如果`wsdl:port`包含子元素`<wsa:EndpointReference …/>`，則`wsa:EndpointReference/wsa:Address`子項目值必須符合的值`@address`屬性的同層級`wsdl:port` / `wsdl:location`項目。</span><span class="sxs-lookup"><span data-stu-id="143a7-274">R3534: If a `wsdl:port` contains a child element `<wsa:EndpointReference …/>`, the `wsa:EndpointReference/wsa:Address` child element value must match the value of the `@address` attribute of the sibling `wsdl:port`/`wsdl:location` element.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="143a7-275">與 WS-Security 組合</span><span class="sxs-lookup"><span data-stu-id="143a7-275">Composition with WS-Security</span></span>
<span data-ttu-id="143a7-276">根據 WS-ADDR 和 WS-ADDR10 的安全性考量章節，建議將所有定址訊息標頭與訊息本文一起簽署，以將其繫結在一起。</span><span class="sxs-lookup"><span data-stu-id="143a7-276">According to security consideration sections in WS-ADDR and WS-ADDR10, all addressing message headers are recommended to be signed together with the message body to bind them together.</span></span>

<span data-ttu-id="143a7-277">當使用 WS-Security 保護訊息完整性時，WS-Addressing 訊息標頭以及從參考參數或屬性 (或兩者) 產生的標頭必須與訊息本文一起簽署。</span><span class="sxs-lookup"><span data-stu-id="143a7-277">When WS-Security is used for message integrity protection, WS-Addressing message headers as well as headers resulted from reference parameters or properties (or both) must be signed together with the body of the message.</span></span>

### <a name="examples"></a><span data-ttu-id="143a7-278">範例</span><span class="sxs-lookup"><span data-stu-id="143a7-278">Examples</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="143a7-279">單向訊息</span><span class="sxs-lookup"><span data-stu-id="143a7-279">One-Way Message</span></span>
<span data-ttu-id="143a7-280">在這種情況下，傳送者會傳送單向訊息給接收者。</span><span class="sxs-lookup"><span data-stu-id="143a7-280">In this scenario, the sender sends a one-way message to the receiver.</span></span> <span data-ttu-id="143a7-281">此時會使用 SOAP 1.2、HTTP 1.1 和 W3C WS-Addressing 1.0。</span><span class="sxs-lookup"><span data-stu-id="143a7-281">SOAP 1.2, HTTP 1.1, and W3C WS-Addressing 1.0 are used.</span></span>

<span data-ttu-id="143a7-282">要求訊息結構：訊息標頭包含 `wsa10:To` 和 `wsa10:Action` 項目。</span><span class="sxs-lookup"><span data-stu-id="143a7-282">The Request Message Structure: The message headers include `wsa10:To` and `wsa10:Action` elements.</span></span> <span data-ttu-id="143a7-283">訊息本文包含來自應用程式命名空間的特定 `<app:Ping>` 項目。</span><span class="sxs-lookup"><span data-stu-id="143a7-283">The message body includes a specific `<app:Ping>` element from the application namespace.</span></span>

<span data-ttu-id="143a7-284">HTTP 標頭： POST 的目的地符合中的 URI`wsa10:To`項目。</span><span class="sxs-lookup"><span data-stu-id="143a7-284">HTTP Headers: The destination in POST matches the URI in the `wsa10:To` element.</span></span>

<span data-ttu-id="143a7-285">Content-Type 標頭具有 SOAP 1.2 所要求的 `application/soap+xml` 值。</span><span class="sxs-lookup"><span data-stu-id="143a7-285">The Content-Type header has the value of `application/soap+xml` as required by SOAP 1.2.</span></span> <span data-ttu-id="143a7-286">其中包含參數 `charset` 和 `action`。</span><span class="sxs-lookup"><span data-stu-id="143a7-286">Parameters `charset` and `action` are included.</span></span> <span data-ttu-id="143a7-287">Content-Type 標頭的 `action` 參數符合 `wsa10:Action` 訊息標頭的值。</span><span class="sxs-lookup"><span data-stu-id="143a7-287">The `action` parameter of the Content-Type header matches the value of the `wsa10:Action` message header.</span></span>

```
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay 
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

<span data-ttu-id="143a7-288">接收者會以空的 HTTP 回應和狀態 202 回應。</span><span class="sxs-lookup"><span data-stu-id="143a7-288">The receiver responds with an empty HTTP response and status 202.</span></span> <span data-ttu-id="143a7-289">以下為 HTTP 回應的範例：</span><span class="sxs-lookup"><span data-stu-id="143a7-289">An example of the HTTP response:</span></span>

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a><span data-ttu-id="143a7-290">SOAP 訊息傳輸最佳化機制</span><span class="sxs-lookup"><span data-stu-id="143a7-290">SOAP Message Transmission Optimization Mechanism</span></span>
<span data-ttu-id="143a7-291">本節會說明 HTTP SOAP MTOM 的 WCF 實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="143a7-291">This section describes the WCF implementation details for the HTTP SOAP MTOM.</span></span> <span data-ttu-id="143a7-292">MTOM 技術是類別的相同為傳統的 text/XML 編碼或 WCF 二進位編碼的 SOAP 訊息編碼機制。</span><span class="sxs-lookup"><span data-stu-id="143a7-292">MTOM technology is SOAP message encoding mechanism of the same class as traditional text/XML encoding or WCF Binary encoding.</span></span> <span data-ttu-id="143a7-293">MTOM 包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="143a7-293">MTOM includes the following:</span></span>

- <span data-ttu-id="143a7-294">由 [XOP] 描述的 XML 編碼和封裝機制，會將 XML 資訊項目最佳化，將包含了以 Base64 編碼的二進位資料分割為不同的二進位部分。</span><span class="sxs-lookup"><span data-stu-id="143a7-294">An XML encoding and packaging mechanism described by [XOP] that optimizes XML information items containing base64-encoded binary data into separate binary parts.</span></span>

- <span data-ttu-id="143a7-295">XOP 封裝 (Package) 的 MIME 封裝 (Encapsulation)，會將 XML Infoset 和每個 XOP 封裝的二進位部分序列化為不同的 MIME 部分。</span><span class="sxs-lookup"><span data-stu-id="143a7-295">A MIME encapsulation of the XOP package that serializes the XML Infoset and each binary part of the XOP package into a separate MIME part.</span></span>

- <span data-ttu-id="143a7-296">套用至 SOAP 1.x 封套的 MIME XOP 編碼。</span><span class="sxs-lookup"><span data-stu-id="143a7-296">A MIME XOP encoding applied to SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="143a7-297">HTTP 傳輸繫結。</span><span class="sxs-lookup"><span data-stu-id="143a7-297">An HTTP transport binding.</span></span>

<span data-ttu-id="143a7-298">可以搭配使用 WCF 非 HTTP 傳輸的 MTOM。</span><span class="sxs-lookup"><span data-stu-id="143a7-298">It is possible to use MTOM with non-HTTP transports with WCF.</span></span> <span data-ttu-id="143a7-299">不過，在本主題中，我們將專注在 HTTP 上。</span><span class="sxs-lookup"><span data-stu-id="143a7-299">However, in this topic we will focus on HTTP.</span></span>

<span data-ttu-id="143a7-300">MTOM 格式利用了大量的規格集，其中涵蓋了 MTOM 本身、XOP 和 MIME。</span><span class="sxs-lookup"><span data-stu-id="143a7-300">The MTOM format leverages a large set of specifications covering MTOM itself, XOP, and MIME.</span></span> <span data-ttu-id="143a7-301">此規格集的模組化使其稍微難以重新建構格式及處理語意的正確需求。</span><span class="sxs-lookup"><span data-stu-id="143a7-301">Modularity of this specification set makes it somewhat difficult to reconstruct exact requirements on the format and processing semantics.</span></span> <span data-ttu-id="143a7-302">本節將描述 MTOM HTTP 繫結的格式和處理需求。</span><span class="sxs-lookup"><span data-stu-id="143a7-302">This section describes the format and processing requirements for MTOM HTTP binding.</span></span>

### <a name="mtom-message-encoding"></a><span data-ttu-id="143a7-303">MTOM 訊息編碼</span><span class="sxs-lookup"><span data-stu-id="143a7-303">MTOM Message Encoding</span></span>

#### <a name="generating-mtom-messages"></a><span data-ttu-id="143a7-304">產生 MTOM 訊息</span><span class="sxs-lookup"><span data-stu-id="143a7-304">Generating MTOM messages</span></span>
<span data-ttu-id="143a7-305">[XOP] 第 3.1 節描述具有項目資訊項目之 XML 編碼的程序，這些資訊項目會在抽象定義的 XOP 封裝中包含 Base64 值。</span><span class="sxs-lookup"><span data-stu-id="143a7-305">The [XOP] section 3.1 describes the process of encoding XML with element information items that contain base64 values into an abstractly defined XOP package.</span></span>

<span data-ttu-id="143a7-306">下列步驟的順序即描述了 MTOM 專屬的編碼程序：</span><span class="sxs-lookup"><span data-stu-id="143a7-306">The following sequence of steps describes the MTOM-specific encoding process:</span></span>

1. <span data-ttu-id="143a7-307">確定 SOAP 封套已編碼包含任何項目資訊項目`[namespace name]`的`http://www.w3.org/2004/08/xop/include`並`[local name]`的`Include`。</span><span class="sxs-lookup"><span data-stu-id="143a7-307">Ensure that the SOAP Envelope to be encoded contains no element information item with a `[namespace name]` of `http://www.w3.org/2004/08/xop/include` and a `[local name]` of `Include`.</span></span>

2. <span data-ttu-id="143a7-308">建立空白的 MIME 封裝。</span><span class="sxs-lookup"><span data-stu-id="143a7-308">Create an empty MIME package.</span></span>

3. <span data-ttu-id="143a7-309">識別原始 XML Infoset 內要進行最佳化的項目資訊項目。</span><span class="sxs-lookup"><span data-stu-id="143a7-309">Identify within the Original XML Infoset the element information items to be optimized.</span></span> <span data-ttu-id="143a7-310">要進行最佳化的項目，如字元組成`[children]`的項目資訊項目必須是中的標準格式`xs:base64Binary`(請參閱 xsd-2、 3.2.16 base64Binary)，且不得包含任何空格字元，前面的內嵌，或下列非空白字元內容。</span><span class="sxs-lookup"><span data-stu-id="143a7-310">For the items to be optimized, the characters that make up the `[children]` of the element information item must be in the canonical form of `xs:base64Binary` (see XSD-2, 3.2.16 base64Binary) and must not contain any white-space characters preceding, inline with, or following the non-white-space content.</span></span>

4. <span data-ttu-id="143a7-311">建立 XOP SOAP 封套 (為原始 SOAP 封套的複本)，但具有在先前步驟中以 `xop:Include` 項目資訊項目建構取代而識別的每個項目資訊項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="143a7-311">Create an XOP SOAP Envelope that is a copy of the Original SOAP Envelope, but with the children of each element information item identified in the previous step replaced by an `xop:Include` element information item constructed as follows:</span></span>

    1. <span data-ttu-id="143a7-312">藉由將其視為 Base64 編碼的資料進行處理，將取代的字元轉換為二進位資料。</span><span class="sxs-lookup"><span data-stu-id="143a7-312">Transform the replaced characters into binary data by processing them as base64-encoded data.</span></span>

    2. <span data-ttu-id="143a7-313">產生唯一的 Content-ID 標頭值，滿足 R3133 和 R3134 的需求。</span><span class="sxs-lookup"><span data-stu-id="143a7-313">Generate a unique Content-ID header value that satisfies requirements R3133 and R3134.</span></span>

    3. <span data-ttu-id="143a7-314">產生具有二進位值的 Content-Transfer-Encoding MIME 標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-314">Generate a Content-Transfer-Encoding MIME header with the value binary.</span></span>

    4. <span data-ttu-id="143a7-315">如果已最佳化的項目資訊項目 (最近插入 `xop:Include` 項目資訊項目的 [parent]) 具有 `xmime:contentType` 屬性資訊項目，則產生一個具有 `xmime:contentType` 屬性值的 Content-Type MIME 標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-315">If the element information item being optimized (the [parent] of the newly inserted `xop:Include` element information item) has an `xmime:contentType` attribute information item, generate a Content-Type MIME header with the value of the `xmime:contentType` attribute.</span></span>

    5. <span data-ttu-id="143a7-316">產生新的二進位 MIME 部分，具有採用二進位資料形式之內容，這些資料是從處理為 Base64 的取代字元解碼而來、來自 4b 的 Content-ID 標頭、來自 4c 的 Content- Transfer-Encoding 標頭、若在步驟 4d 產生則為 Content-Type 標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-316">Generate a new binary MIME part with content formed by binary data decoded from the replaced characters processed as base64, Content-ID header from 4b, Content- Transfer-Encoding header from 4c, Content-Type header if generated in step 4d.</span></span>

    6. <span data-ttu-id="143a7-317">將 `href` 屬性加入至 `xop:Include` 項目，該項目具有 cid: uri 值，衍生自步驟 4b 中產生的 Content-ID 標頭值。</span><span class="sxs-lookup"><span data-stu-id="143a7-317">Add an `href` attribute to the `xop:Include` element with the value cid: uri derived from Content-ID header value generated in step 4b.</span></span> <span data-ttu-id="143a7-318">移除封閉 」\<"和">"字元、 URL 逸出的剩餘字串，並加上前置詞`cid:`。</span><span class="sxs-lookup"><span data-stu-id="143a7-318">Remove the enclosing "\<" and ">" characters, URL-escape the remaining string, and add the prefix `cid:`.</span></span> <span data-ttu-id="143a7-319">下列最小字元集為 RFC1738 和 RFC2396 逸出所需。</span><span class="sxs-lookup"><span data-stu-id="143a7-319">The following minimum character set is required to be escaped by RFC1738 and RFC2396.</span></span> <span data-ttu-id="143a7-320">其他可以逸出的字元。</span><span class="sxs-lookup"><span data-stu-id="143a7-320">Other characters can be escaped.</span></span>

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. <span data-ttu-id="143a7-321">建立根 MIME 部分，具有來自步驟 4 的 XOP SOAP 封套。</span><span class="sxs-lookup"><span data-stu-id="143a7-321">Create a root MIME part with the XOP SOAP Envelope from step 4.</span></span>

6. <span data-ttu-id="143a7-322">撰寫 HTTP 標頭，包括 HTTP Content-Type 標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-322">Write the HTTP headers, including the HTTP Content-Type header.</span></span>

7. <span data-ttu-id="143a7-323">撰寫 MIME 封裝。</span><span class="sxs-lookup"><span data-stu-id="143a7-323">Write the MIME package.</span></span>

#### <a name="processing-mtom-messages"></a><span data-ttu-id="143a7-324">處理 MTOM 訊息</span><span class="sxs-lookup"><span data-stu-id="143a7-324">Processing MTOM messages</span></span>
<span data-ttu-id="143a7-325">MTOM 訊息的處理正是如先前「產生 MTOM 訊息」一節所述的反向程序：</span><span class="sxs-lookup"><span data-stu-id="143a7-325">Processing of an MTOM message is the exact reverse of the process described in the preceding "Generating MTOM messages" section:</span></span>

1. <span data-ttu-id="143a7-326">確定根 MIME 部分具有 Content-Type `application/xop+xml`。</span><span class="sxs-lookup"><span data-stu-id="143a7-326">Ensure the root MIME part has the Content-Type `application/xop+xml`.</span></span>

2. <span data-ttu-id="143a7-327">藉由剖析封裝為 XML 文件的根 MIME 部分，以建構 SOAP 封套。</span><span class="sxs-lookup"><span data-stu-id="143a7-327">Construct a SOAP Envelope by parsing the root MIME part of the package as an XML document.</span></span> <span data-ttu-id="143a7-328">字元編碼是由根 MIME 部分的 Content-Type `charset` 參數所決定的。</span><span class="sxs-lookup"><span data-stu-id="143a7-328">Character encoding is determined by the `charset` parameter of the Content-Type of the root MIME part.</span></span>

3. <span data-ttu-id="143a7-329">對於已建構 SOAP 封套內的每個項目資訊項目，其中具有一個 `xop:Include` 項目資訊項目，做為其 [children] 屬性的唯一成員：</span><span class="sxs-lookup"><span data-stu-id="143a7-329">For each element information item in the constructed SOAP Envelope, which has, as the sole member of its [children] property, an `xop:Include` element information item:</span></span>

    1. <span data-ttu-id="143a7-330">移除 `cid:` 前置詞，並以 `@href` 項目的 `xop:Include` 屬性值解除所有 URI 逸出順序的逸出 (RFC 2396)。</span><span class="sxs-lookup"><span data-stu-id="143a7-330">Remove the `cid:` prefix and unescape all URI-escape sequences (RFC 2396) in the value of the `@href` attribute of the `xop:Include` element.</span></span> <span data-ttu-id="143a7-331">括住結果字串中的"\<"，">"。</span><span class="sxs-lookup"><span data-stu-id="143a7-331">Enclose the result string in "\<", ">".</span></span>

    2. <span data-ttu-id="143a7-332">找出具有 Content-ID 標頭值的 MIME 部分，其符合衍生自步驟 3a 的字串。</span><span class="sxs-lookup"><span data-stu-id="143a7-332">Locate the MIME part with the Content-ID header value that matches the string derived in step 3a.</span></span>

    3. <span data-ttu-id="143a7-333">取代 `xop:Include` 項目資訊項目，它出現在每個項目的 `children` 屬性中，具有代表標準 Base64 編碼的字元資訊項目 (請參閱 XSD-2、3.2.16 base64Binary)，這些項目是步驟 3b 內識別的 MIME 部分之實體主體 (實際上以從封裝部分重新建構的資料取代 `xop:Include` 項目資訊項目)。</span><span class="sxs-lookup"><span data-stu-id="143a7-333">Replace the `xop:Include` element information item that appears in the `children` property of each item with the character information items that represent the canonical base64 encoding (see XSD-2, 3.2.16 base64Binary) of the entity body of the MIME part identified in step 3b (effectively replace the `xop:Include` element information item with the data reconstructed from the package part).</span></span>

#### <a name="http-content-type-header"></a><span data-ttu-id="143a7-334">HTTP Content-Type 標頭</span><span class="sxs-lookup"><span data-stu-id="143a7-334">HTTP Content-Type Header</span></span>
<span data-ttu-id="143a7-335">下列是 WCF 釐清以 SOAP 1.x MTOM 編碼之訊息衍生自 MTOM 規格本身所述需求的 HTTP Content-type 標頭格式的清單，並衍生自 MTOM 和 RFC 2387。</span><span class="sxs-lookup"><span data-stu-id="143a7-335">The following is a list of WCF clarifications for the format of the HTTP Content-Type header of a SOAP 1.x MTOM-encoded message derived from requirements stated in the MTOM specification itself and are derived from MTOM and RFC 2387.</span></span>

- <span data-ttu-id="143a7-336">R4131：HTTP Content-Type 標頭必須具有多重/相關 (區分大小寫) 的值，以及其參數。</span><span class="sxs-lookup"><span data-stu-id="143a7-336">R4131: An HTTP Content-Type header must have the value of multipart/related (case-insensitive) and its parameters.</span></span> <span data-ttu-id="143a7-337">參數名稱是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="143a7-337">Parameter names are case-insensitive.</span></span> <span data-ttu-id="143a7-338">參數的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="143a7-338">Parameter order is not significant.</span></span>

- <span data-ttu-id="143a7-339">MIME 訊息之 Content-Type 標頭的完整巴克斯格式 (Backus-Naur Form，BNF) 列示於 RFC 2045 第 5.1 節中。</span><span class="sxs-lookup"><span data-stu-id="143a7-339">The full Backus-Naur Form (BNF) of the Content-Type header for MIME messages is listed in RFC 2045, section 5.1.</span></span>

- <span data-ttu-id="143a7-340">R4132：HTTP Content-Type 標頭必須具有含 `application/xop+xml` 值的型別參數，以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="143a7-340">R4132: An HTTP Content-Type header must have a type parameter with the value `application/xop+xml` enclosed in double quotation marks.</span></span>

<span data-ttu-id="143a7-341">雖然不是在 RFC 2387 中明確的需求使用雙引號，文字會遵守多重/相關媒體型別參數的所有最有可能包含保留的字元，例如 「\@"或"/"，因此需要雙引號標記。</span><span class="sxs-lookup"><span data-stu-id="143a7-341">While the requirement to use double quotation marks is not explicit in RFC 2387, the text observes that all of the multipart/related media type parameters most likely contain reserved characters like "\@" or "/" and therefore need double quotation marks.</span></span>

- <span data-ttu-id="143a7-342">R4133：HTTP Content-Type 標頭應該具有起始參數，其中具有包含 SOAP 1.x 封套之 MIME 部分的 Content-ID 標頭值，以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="143a7-342">R4133: An HTTP Content-Type header should have a start parameter with the value of the Content-ID header of the MIME part that contains the SOAP 1.x Envelope, enclosed in double quotation marks.</span></span> <span data-ttu-id="143a7-343">如果省略了起始參數，則第一個 MIME 部分必須包含 SOAP 1.x 封套。</span><span class="sxs-lookup"><span data-stu-id="143a7-343">If the start parameter is omitted, the first MIME part must contain the SOAP 1.x Envelope.</span></span>

- <span data-ttu-id="143a7-344">R4134：以 SOAP 1.1 MTOM 編碼之訊息的 HTTP Content-Type 標頭必須包含 start-info 參數，其具有 text/xml 的值，以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="143a7-344">R4134: An HTTP Content-Type header for a SOAP 1.1 MTOM encoded message must include the start-info parameter with the value of text/xml, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="143a7-345">R4135：以 SOAP 1.2 MTOM 編碼之訊息的 HTTP Content-Type 標頭必須包含 start-info 參數，其具有 `application/soap+xml` 值，以雙引號括住。</span><span class="sxs-lookup"><span data-stu-id="143a7-345">R4135: An HTTP Content-Type header for a SOAP 1.2 MTOM-encoded message must include the start-info parameter with the value of `application/soap+xml`, enclosed in double quotation marks.</span></span>

- <span data-ttu-id="143a7-346">R4136：以 SOAP 1.x MTOM 編碼之訊息的 HTTP Content-Type 標頭必須具有界限參數，其值 (以雙引號括住) 符合 RFC 2046 第 5.1.1 節內所定義的 MIME 界限 BNF 值。</span><span class="sxs-lookup"><span data-stu-id="143a7-346">R4136: HTTP Content-Type header for a SOAP 1.x MTOM-encoded message must have the boundary parameter with the value (enclosed in double quotation marks) that matches the MIME boundary BNF defined in RFC 2046, section 5.1.1</span></span>

    ```
    boundary := 0*69<bchars> bcharsnospace 
    bchars := bcharsnospace / " " 
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+" 
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     <span data-ttu-id="143a7-347">例如：</span><span class="sxs-lookup"><span data-stu-id="143a7-347">Examples:</span></span>

     <span data-ttu-id="143a7-348">正確</span><span class="sxs-lookup"><span data-stu-id="143a7-348">CORRECT</span></span>

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     <span data-ttu-id="143a7-349">正確</span><span class="sxs-lookup"><span data-stu-id="143a7-349">CORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     <span data-ttu-id="143a7-350">不正確</span><span class="sxs-lookup"><span data-stu-id="143a7-350">INCORRECT</span></span>

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1" 
    ```

#### <a name="infoset-mime-part"></a><span data-ttu-id="143a7-351">Infoset MIME 部分</span><span class="sxs-lookup"><span data-stu-id="143a7-351">Infoset MIME Part</span></span>
<span data-ttu-id="143a7-352">SOAP 1.x 封套會封裝為 XOP MIME 封裝的根部分，通常稱為 `infoset` 部分。</span><span class="sxs-lookup"><span data-stu-id="143a7-352">The SOAP 1.x Envelope is encapsulated as a root part of the XOP MIME package and is often called the `infoset` part.</span></span>

- <span data-ttu-id="143a7-353">R4141：SOAP 1.x 封套必須封裝為 XOP MIME 封裝的根部分，稱為 `infoset` 部分，並從 HTTP Content-Type 參考。</span><span class="sxs-lookup"><span data-stu-id="143a7-353">R4141: The SOAP 1.x Envelope must be encapsulated as a root part of the XOP MIME package, called the `infoset` part and referenced from the HTTP Content-Type.</span></span>

- <span data-ttu-id="143a7-354">R4142：SOAP `Infoset` 部分必須包含下列 MIME 標頭：`Content-ID`、`Content-Transfer-Encoding` 和 `Content-Type`。</span><span class="sxs-lookup"><span data-stu-id="143a7-354">R4142: The SOAP `Infoset` part must include the following MIME headers: `Content-ID`, `Content-Transfer-Encoding`, and `Content-Type`.</span></span>

<span data-ttu-id="143a7-355">Content-ID 標頭的格式在 RFC 2045 中定義為</span><span class="sxs-lookup"><span data-stu-id="143a7-355">The format of the Content-ID header is defined by RFC 2045 as</span></span>

```
"Content-ID" ":" msg-id
```

<span data-ttu-id="143a7-356">其中 `msg-id` 在 RFC 2822 (取代 RFC 822，在 RFC 2045 內參考) 中定義為：</span><span class="sxs-lookup"><span data-stu-id="143a7-356">where `msg-id` is defined in RFC 2822 (that supersedes RFC 822, referenced in RFC 2045) as:</span></span>

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

<span data-ttu-id="143a7-357">有效的電子郵件地址括住並 「\<"和">"。</span><span class="sxs-lookup"><span data-stu-id="143a7-357">and is effectively an email address enclosed within "\<" and  ">".</span></span> <span data-ttu-id="143a7-358">RFC 2822 內加入了 `[CFWS]` 前置和後置字元，用以帶出註解，且不應用於保留互通性。</span><span class="sxs-lookup"><span data-stu-id="143a7-358">The `[CFWS]` prefix and suffix were added in RFC 2822 to carry comments and should not be used to preserve interoperability.</span></span>

<span data-ttu-id="143a7-359">R4143：Infoset MIME 部分的 Content-ID 標頭值必須遵守 RFC 2822 實際執行的 `msg-id`，其中省略了 `[CFWS]` 前置和後置字元部分。</span><span class="sxs-lookup"><span data-stu-id="143a7-359">R4143: The value of the Content-ID header for the Infoset MIME part must follow `msg-id` production from RFC 2822 with the `[CFWS]` prefix and suffix parts omitted.</span></span>

<span data-ttu-id="143a7-360">許多 MIME 實作放寬需求括住的值"\<"和">"電子郵件地址，並用`absoluteURI`括住"\<"，">"除了電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="143a7-360">A number of MIME implementations relaxed requirements for the value enclosed within "\<" and ">" to be an email address and used `absoluteURI` enclosed in "\<" , ">" in addition to the email address.</span></span> <span data-ttu-id="143a7-361">這個版本的 WCF 會使用表單的 CONTENT-ID MIME 標頭的值：</span><span class="sxs-lookup"><span data-stu-id="143a7-361">This version of WCF uses values of the Content-ID MIME header of the form:</span></span>

```
Content-ID: <http://tempuri.org/0> 
```

<span data-ttu-id="143a7-362">R4144：MTOM 處理器應該接受符合下列較不嚴謹之 `msg-id` 的 Content-ID 標頭值。</span><span class="sxs-lookup"><span data-stu-id="143a7-362">R4144: MTOM processors should accept Content-ID header values that match the following relaxed `msg-id`.</span></span>

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

<span data-ttu-id="143a7-363">MIME (RFC 2045) 提供 Content-Transfer-Encoding 標頭，用於溝通 MIME 部分的內容編碼。</span><span class="sxs-lookup"><span data-stu-id="143a7-363">MIME (RFC 2045) provides the Content-Transfer-Encoding header to communicate encoding of the content of the MIME part.</span></span> <span data-ttu-id="143a7-364">Content-Transfer-Encoding 預設定義為 7 位元，不適用於大部分的 SOAP 訊息，因此需要使用 Content-Transfer-Encoding 標頭提供較佳的互通性：</span><span class="sxs-lookup"><span data-stu-id="143a7-364">The default defined for Content-Transfer-Encoding is 7-bit, which is not suitable for most SOAP messages, so the Content-Transfer-Encoding header is needed for greater interoperability:</span></span>

- <span data-ttu-id="143a7-365">R4145：SOAP Infoset 部分必須包含 Content-Transfer-Encoding 標頭。</span><span class="sxs-lookup"><span data-stu-id="143a7-365">R4145: The SOAP Infoset part must contain the Content-Transfer-Encoding header.</span></span>

- <span data-ttu-id="143a7-366">R4146：如果 SOAP 封套字元的編碼為 UTF-8，Content-Transfer-Encoding 標頭的值必須為 8 位元。</span><span class="sxs-lookup"><span data-stu-id="143a7-366">R4146: If the SOAP Envelope character encoding is UTF-8, the value of the Content-Transfer-Encoding header must be 8-bit.</span></span>

- <span data-ttu-id="143a7-367">R4147：如果 SOAP 封套的字元編碼為 UTF-16，則 Content-Transfer-Encoding 標頭的值必須為二進位值。</span><span class="sxs-lookup"><span data-stu-id="143a7-367">R4147: If the SOAP Envelope character encoding is UTF-16, the value of the Content-Transfer-Encoding header must be binary.</span></span>

- <span data-ttu-id="143a7-368">根據 [XOP] 第 5 節，</span><span class="sxs-lookup"><span data-stu-id="143a7-368">According to [XOP] section 5,</span></span>

- <span data-ttu-id="143a7-369">R4148: SOAP1.1 Infoset 部分必須包含 Content-type 標頭的媒體類型 application/xop + xml，且參數類型 ="text/xml"和字元集</span><span class="sxs-lookup"><span data-stu-id="143a7-369">R4148: SOAP1.1 Infoset part must contain Content-Type header with media type application/xop+xml and parameters type="text/xml" and charset</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- <span data-ttu-id="143a7-370">R4149: SOAP 1.2 Infoset 部分必須包含媒體類型的內容類型標頭`application/xop+xml`且參數類型 ="`application/soap+xml`"和`charset`。</span><span class="sxs-lookup"><span data-stu-id="143a7-370">R4149: The SOAP 1.2 Infoset part must contain the Content-Type header with media type `application/xop+xml` and parameters type="`application/soap+xml`" and `charset`.</span></span>

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     <span data-ttu-id="143a7-371">雖然 XOP 將 `charset` 的 `application/xop+xml` 參數定義為選擇性參數，您仍舊需要使用此參數為 `charset` 媒體類型的 `text/xml` 參數提供類似於 BP 1.1 需求的互通性。</span><span class="sxs-lookup"><span data-stu-id="143a7-371">While XOP defines the `charset` parameter for `application/xop+xml` to be optional, it is needed for interoperability similar to the BP 1.1 requirement on the `charset` parameter for the `text/xml` media type.</span></span>

- <span data-ttu-id="143a7-372">R41410：`type` 和 `charset` 參數必須存在於 SOAP 1.x Infoset 部分的 Content-Type 標頭上。</span><span class="sxs-lookup"><span data-stu-id="143a7-372">R41410: The `type` and `charset` parameters must be present on the Content-Type header of the SOAP 1.x Infoset part.</span></span>

#### <a name="wcf-endpoint-support-for-mtom"></a><span data-ttu-id="143a7-373">MTOM 的 WCF 端點支援</span><span class="sxs-lookup"><span data-stu-id="143a7-373">WCF Endpoint Support for MTOM</span></span>
<span data-ttu-id="143a7-374">MTOM 的目的是要對 SOAP 訊息進行編碼，以最佳化 Base64 編碼的資料。</span><span class="sxs-lookup"><span data-stu-id="143a7-374">The purpose of MTOM is to encode a SOAP message to optimize base64-encoded data.</span></span> <span data-ttu-id="143a7-375">以下為條件約束的清單：</span><span class="sxs-lookup"><span data-stu-id="143a7-375">The following is a list of constraints:</span></span>

- <span data-ttu-id="143a7-376">R4151：任何包含 Base64 編碼資料的項目資訊項目可能都已進行了最佳化。</span><span class="sxs-lookup"><span data-stu-id="143a7-376">R4151: Any element information item that contains base64-encoded data may be optimized.</span></span>

- <span data-ttu-id="143a7-377">B4152: WCF 最佳化項目資訊項目，其中包含 base64 編碼的資料，並能超過 1024 個位元組的長度。</span><span class="sxs-lookup"><span data-stu-id="143a7-377">B4152: WCF optimizes element information items that contain base64-encoded data and exceed 1024 bytes in length.</span></span>

<span data-ttu-id="143a7-378">設定為使用 MTOM 的 WCF 端點仍會一律傳送 MTOM 編碼的訊息。</span><span class="sxs-lookup"><span data-stu-id="143a7-378">A WCF endpoint configured to use MTOM will always send MTOM-encoded messages.</span></span> <span data-ttu-id="143a7-379">即使沒有任何部分滿足所要求的準則，訊息仍舊會以 MTOM 編碼 (序列化為 MIME 封裝，其中具有含 SOAP 封套的單一 MIME 部分)。</span><span class="sxs-lookup"><span data-stu-id="143a7-379">Even if no parts meet the required criteria, the message is still MTOM-encoded (serialized as a MIME package with a single MIME part containing the SOAP envelope).</span></span>

### <a name="ws-policy-assertion-for-mtom"></a><span data-ttu-id="143a7-380">MTOM 的 WS-Policy 判斷提示</span><span class="sxs-lookup"><span data-stu-id="143a7-380">WS-Policy Assertion for MTOM</span></span>
<span data-ttu-id="143a7-381">WCF 會使用下列原則判斷提示，指出 MTOM 使用量端點：</span><span class="sxs-lookup"><span data-stu-id="143a7-381">WCF uses the following policy assertion to indicate MTOM usage by endpoint:</span></span>

```xml
<wsoma:OptimizedMimeSerialization ... />
```

- <span data-ttu-id="143a7-382">R4211：之前的原則判斷提示具有端點原則主體，並指定所有傳送訊息和接收訊息的端點必須使用 MTOM 進行最佳化。</span><span class="sxs-lookup"><span data-stu-id="143a7-382">R4211: The preceding policy assertion has an Endpoint Policy Subject and specifies that all messages sent to and received from the endpoint must be optimized using MTOM.</span></span>

- <span data-ttu-id="143a7-383">B4212： 當設定為使用 MTOM 最佳化時，WCF 端點將 MTOM 原則判斷提示附加至對應的原則`wsdl:binding`。</span><span class="sxs-lookup"><span data-stu-id="143a7-383">B4212: When configured to use MTOM optimization, an WCF endpoint adds an MTOM Policy assertion to the policy attached to the corresponding `wsdl:binding`.</span></span>

### <a name="composition-with-ws-security"></a><span data-ttu-id="143a7-384">與 WS-Security 組合</span><span class="sxs-lookup"><span data-stu-id="143a7-384">Composition with WS-Security</span></span>
<span data-ttu-id="143a7-385">MTOM 是類似於編碼機制`text/xml`和 WCF 二進位 XML。</span><span class="sxs-lookup"><span data-stu-id="143a7-385">MTOM is an encoding mechanism that is similar to `text/xml` and WCF Binary XML.</span></span> <span data-ttu-id="143a7-386">MTOM 可與 WS-Security 和其他 WS-\* 通訊協定自然組合：使用 MTOM，可以使 WS-Security 保護的訊息最佳化。</span><span class="sxs-lookup"><span data-stu-id="143a7-386">MTOM offers natural composition with WS-Security and other WS-\* protocols: a message secured using WS-Security can be optimized using MTOM.</span></span>

### <a name="examples"></a><span data-ttu-id="143a7-387">範例</span><span class="sxs-lookup"><span data-stu-id="143a7-387">Examples</span></span>

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a><span data-ttu-id="143a7-388">使用 MTOM 進行編碼的 WCF SOAP 1.1 訊息</span><span class="sxs-lookup"><span data-stu-id="143a7-388">WCF SOAP 1.1 Message Encoded Using MTOM</span></span>

```
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a><span data-ttu-id="143a7-389">使用 MTOM 對 WCF Secure SOAP 1.2 訊息進行編碼</span><span class="sxs-lookup"><span data-stu-id="143a7-389">WCF Secure SOAP 1.2 Message Encoded Using MTOM</span></span>
<span data-ttu-id="143a7-390">在此範例中，訊息是以 MTOM 和 SOAP 1.2 進行編碼，並使用 WS-Security 予以保護。</span><span class="sxs-lookup"><span data-stu-id="143a7-390">In this example, a message is encoded using MTOM and SOAP 1.2 that is protected using WS-Security.</span></span> <span data-ttu-id="143a7-391">用於識別編碼的二進位部分是 `BinarySecurityToken`的內容，以及對應於已加密簽章和已加密主體之 `CipherValue` 的 `EncryptedData`。</span><span class="sxs-lookup"><span data-stu-id="143a7-391">The binary parts identified for encoding are the contents of the `BinarySecurityToken`, `CipherValue` of the `EncryptedData` corresponding to the encrypted signature and encrypted body.</span></span> <span data-ttu-id="143a7-392">請注意，`CipherValue`的`EncryptedKey`無法識別最佳化 wcf，因為其長度小於 1024 位元組。</span><span class="sxs-lookup"><span data-stu-id="143a7-392">Note that the `CipherValue` of the `EncryptedKey` was not identified for optimization by WCF, because its length is less then 1024 bytes.</span></span>

```
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml"; 
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```