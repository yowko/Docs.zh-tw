---
title: 序列化-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053352"
---
# <a name="serialization-in-net"></a><span data-ttu-id="9a74c-102">.NET 的序列化</span><span class="sxs-lookup"><span data-stu-id="9a74c-102">Serialization in .NET</span></span>

<span data-ttu-id="9a74c-103">序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。</span><span class="sxs-lookup"><span data-stu-id="9a74c-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="9a74c-104">序列化的互補方法是還原序列化，它將資料流轉換成為物件。</span><span class="sxs-lookup"><span data-stu-id="9a74c-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="9a74c-105">這些程式一起允許儲存和傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="9a74c-105">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="9a74c-106">.NET 具備下列序列化技術：</span><span class="sxs-lookup"><span data-stu-id="9a74c-106">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="9a74c-107">[二進位序列化](binary-serialization.md)會保留型別精確度，這有助於在應用程式的不同調用之間保留物件的狀態。</span><span class="sxs-lookup"><span data-stu-id="9a74c-107">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="9a74c-108">例如，藉由將物件序列化至剪貼簿，就可在不同應用程式之間共用該物件。</span><span class="sxs-lookup"><span data-stu-id="9a74c-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="9a74c-109">您可以將物件序列化為資料流、序列化至磁碟、記憶體、在網路上序列化等等。</span><span class="sxs-lookup"><span data-stu-id="9a74c-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="9a74c-110">在遠端使用序列化從一台電腦或應用程式定義域，以「值」傳遞物件至他處。</span><span class="sxs-lookup"><span data-stu-id="9a74c-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="9a74c-111">[XML 和 SOAP 序列化](xml-and-soap-serialization.md)只會序列化公用屬性和欄位，不會保留型別精確度。</span><span class="sxs-lookup"><span data-stu-id="9a74c-111">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="9a74c-112">當您不想限制使用資料的應用程式，而能提供或使用資料時，這種做法就很有用。</span><span class="sxs-lookup"><span data-stu-id="9a74c-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="9a74c-113">因為 XML 為開放標準，因此是在 Web 上共用資料的很好選擇。</span><span class="sxs-lookup"><span data-stu-id="9a74c-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="9a74c-114">同樣是開放標準的 SOAP，也是一項很好的選擇。</span><span class="sxs-lookup"><span data-stu-id="9a74c-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="9a74c-115">[JSON 序列化](system-text-json-overview.md)只會序列化公用屬性，而且不會保留型別精確度。</span><span class="sxs-lookup"><span data-stu-id="9a74c-115">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="9a74c-116">JSON 是一種開放式標準，是在網路上共用資料的理想選擇。</span><span class="sxs-lookup"><span data-stu-id="9a74c-116">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="9a74c-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="9a74c-117">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="9a74c-118">包含類別，可以用來序列化和還原序列化物件。</span><span class="sxs-lookup"><span data-stu-id="9a74c-118">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="9a74c-119">包含可用來將物件序列化為 XML 格式之文件或資料流的類別。</span><span class="sxs-lookup"><span data-stu-id="9a74c-119">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="9a74c-120">包含可以用來將物件序列化為 JSON 格式檔或資料流程的類別。</span><span class="sxs-lookup"><span data-stu-id="9a74c-120">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
