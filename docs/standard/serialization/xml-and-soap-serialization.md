---
title: XML 和 SOAP 序列化
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: dcb2ed1703473be582a12f430d2e051d8a420230
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588381"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="258e5-102">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="258e5-102">XML and SOAP serialization</span></span>

<span data-ttu-id="258e5-103">XML 序列化會將物件的公用欄位和屬性，以及方法的參數和傳回值，轉換（序列化）為符合特定 XML 架構定義語言（XSD）檔的 XML 資料流程。</span><span class="sxs-lookup"><span data-stu-id="258e5-103">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="258e5-104">XML 序列化會產生強型別 (Strongly Typed) 類別，其中包含的公用屬性和欄位都轉換為序列格式 (此例為 XML) 以進行儲存或傳輸。</span><span class="sxs-lookup"><span data-stu-id="258e5-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="258e5-105">因為 XML 為開放標準，無論是何種平台，XML 資料流都可依需要由任何應用程式處理。</span><span class="sxs-lookup"><span data-stu-id="258e5-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="258e5-106">例如，使用 ASP.NET 建立的 XML Web 服務以 <xref:System.Xml.Serialization.XmlSerializer> 類別建立 XML 資料流，在網際網路或內部網路的 XML Web 服務應用程式之間傳遞資料。</span><span class="sxs-lookup"><span data-stu-id="258e5-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="258e5-107">相反地，還原序列化採用這樣的 XML 資料流並重建物件。</span><span class="sxs-lookup"><span data-stu-id="258e5-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="258e5-108">XML 序列化也可用來將物件序列化為與 SOAP 規格相符的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="258e5-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="258e5-109">SOAP 是以 XML 為基礎的通訊協定，特別設計來傳輸使用 XML 的程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="258e5-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="258e5-110">若要序列化或還原序列化物件，請使用 <xref:System.Xml.Serialization.XmlSerializer> 類別。</span><span class="sxs-lookup"><span data-stu-id="258e5-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="258e5-111">若要建立要序列化的類別，請使用 XML 結構描述定義工具。</span><span class="sxs-lookup"><span data-stu-id="258e5-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="258e5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="258e5-112">See also</span></span>

- [<span data-ttu-id="258e5-113">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="258e5-113">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="258e5-114">[使用 ASP.NET 和 XML Web Service 用戶端所建立的 XML Web 服務](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="258e5-114">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
