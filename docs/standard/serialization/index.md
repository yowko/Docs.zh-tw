---
title: .NET 的序列化
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 13ba804e76a64c6a0b32ba5a203258e76c209ff4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644904"
---
# <a name="serialization-in-net"></a><span data-ttu-id="5d878-102">.NET 的序列化</span><span class="sxs-lookup"><span data-stu-id="5d878-102">Serialization in .NET</span></span>
<span data-ttu-id="5d878-103">序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。</span><span class="sxs-lookup"><span data-stu-id="5d878-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="5d878-104">序列化的互補方法是還原序列化，它將資料流轉換成為物件。</span><span class="sxs-lookup"><span data-stu-id="5d878-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="5d878-105">將這些程序搭配在一起，可讓資料輕鬆地儲存與傳輸。</span><span class="sxs-lookup"><span data-stu-id="5d878-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="5d878-106">.NET 具有兩種序列化技術：</span><span class="sxs-lookup"><span data-stu-id="5d878-106">.NET features two serialization technologies:</span></span>  
  
- <span data-ttu-id="5d878-107">二進位序列化保留型別精確度，這對於在應用程式不同的引動過程之間，保留物件狀態相當實用。</span><span class="sxs-lookup"><span data-stu-id="5d878-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="5d878-108">例如，藉由將物件序列化至剪貼簿，就可在不同應用程式之間共用該物件。</span><span class="sxs-lookup"><span data-stu-id="5d878-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="5d878-109">您可以將物件序列化為資料流、序列化至磁碟、記憶體、在網路上序列化等等。</span><span class="sxs-lookup"><span data-stu-id="5d878-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="5d878-110">在遠端使用序列化從一台電腦或應用程式定義域，以「值」傳遞物件至他處。</span><span class="sxs-lookup"><span data-stu-id="5d878-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="5d878-111">XML 序列化程序僅對公用屬性與欄位進行序列化，並不保留型別精確度。</span><span class="sxs-lookup"><span data-stu-id="5d878-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="5d878-112">當您不想限制使用資料的應用程式，而能提供或使用資料時，這種做法就很有用。</span><span class="sxs-lookup"><span data-stu-id="5d878-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="5d878-113">因為 XML 為開放標準，因此是在 Web 上共用資料的很好選擇。</span><span class="sxs-lookup"><span data-stu-id="5d878-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="5d878-114">同樣是開放標準的 SOAP，也是一項很好的選擇。</span><span class="sxs-lookup"><span data-stu-id="5d878-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d878-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="5d878-115">In This Section</span></span>  
[<span data-ttu-id="5d878-116">序列化「如何」主題</span><span class="sxs-lookup"><span data-stu-id="5d878-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="5d878-117">列出本節中所含的 HOW TO 主題的連結。</span><span class="sxs-lookup"><span data-stu-id="5d878-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="5d878-118">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="5d878-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="5d878-119">說明 Common Language Runtime 中所含的二進位序列化機制。</span><span class="sxs-lookup"><span data-stu-id="5d878-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="5d878-120">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="5d878-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="5d878-121">說明 Common Language Runtime 中所含的 XML 和 SOAP 序列化機制。</span><span class="sxs-lookup"><span data-stu-id="5d878-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="5d878-122">序列化工具</span><span class="sxs-lookup"><span data-stu-id="5d878-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="5d878-123">這些工具可幫助開發序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d878-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="5d878-124">序列化範例</span><span class="sxs-lookup"><span data-stu-id="5d878-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="5d878-125">以下範例示範如何進行序列化。</span><span class="sxs-lookup"><span data-stu-id="5d878-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="5d878-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="5d878-126">Reference</span></span>
<span data-ttu-id="5d878-127"><xref:System.Runtime.Serialization> 包含類別，可以用來序列化和還原序列化物件。</span><span class="sxs-lookup"><span data-stu-id="5d878-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="5d878-128">包含可用來將物件序列化為 XML 格式之文件或資料流的類別。</span><span class="sxs-lookup"><span data-stu-id="5d878-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>