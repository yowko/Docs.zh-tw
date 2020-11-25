---
title: XML 結構描述物件模型 (SOM)
ms.date: 03/30/2017
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: b2af024f9821401b1380347580cc0dc5aeb21c3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733018"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="5766b-102">XML 結構描述物件模型 (SOM)</span><span class="sxs-lookup"><span data-stu-id="5766b-102">XML Schema Object Model (SOM)</span></span>

<span data-ttu-id="5766b-103">XML 結構描述是一種功能強大且複雜的工具，其用於在相容 XML 文件中建立及驗證結構。</span><span class="sxs-lookup"><span data-stu-id="5766b-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="5766b-104">與關聯式資料庫中的資料模型化相似，結構描述提供一種定義 XML 文件結構的方法，即指定可在文件中使用的項目，以及為了對該指定結構描述有效，這些項目必須遵循的結構及型別。</span><span class="sxs-lookup"><span data-stu-id="5766b-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="5766b-105">結構描述物件模型 (SOM) 在 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中提供了一組類別，可讓您從檔案讀取結構描述，或以程式設計方式建立記憶體中結構描述。</span><span class="sxs-lookup"><span data-stu-id="5766b-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="5766b-106">然後，可以周遊、編輯、編譯及驗證結構描述，或將其寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="5766b-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5766b-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="5766b-107">In This Section</span></span>  

 [<span data-ttu-id="5766b-108">XML 結構描述物件模型概觀</span><span class="sxs-lookup"><span data-stu-id="5766b-108">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)  
 <span data-ttu-id="5766b-109">說明結構描述物件模型 (SOM) 及其提供的功能及類別。</span><span class="sxs-lookup"><span data-stu-id="5766b-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="5766b-110">讀取及寫入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="5766b-110">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="5766b-111">說明如何在檔案或其他來源中讀取及寫入 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="5766b-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="5766b-112">建置 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="5766b-112">Building XML Schemas</span></span>](building-xml-schemas.md)  
 <span data-ttu-id="5766b-113">說明如何使用 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空間中的類別，以建置記憶體中 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="5766b-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="5766b-114">周遊 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="5766b-114">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)  
 <span data-ttu-id="5766b-115">說明如何周遊 XML 結構描述，以存取儲存於 SOM 中的項目、屬性及型別。</span><span class="sxs-lookup"><span data-stu-id="5766b-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="5766b-116">編輯 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="5766b-116">Editing XML Schemas</span></span>](editing-xml-schemas.md)  
 <span data-ttu-id="5766b-117">說明如何編輯 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="5766b-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="5766b-118">併入或匯入 XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="5766b-118">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)  
 <span data-ttu-id="5766b-119">說明如何納入或匯入其他 XML 結構描述，以補充進行納入或匯入之結構描述的結構。</span><span class="sxs-lookup"><span data-stu-id="5766b-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>
