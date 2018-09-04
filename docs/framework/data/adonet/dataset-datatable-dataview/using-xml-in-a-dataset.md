---
title: 在資料集中使用 XML
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: cbdc6135a819e2141426f432d163cd49a7b78ac4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43489873"
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="d7210-102">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="d7210-102">Using XML in a DataSet</span></span>
<span data-ttu-id="d7210-103">透過 ADO.NET，您可以從 XML 資料流或文件填滿 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="d7210-103">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="d7210-104">您可以使用 XML 資料流或文件，為 <xref:System.Data.DataSet> 提供資料、結構描述資訊或同時提供這兩者。</span><span class="sxs-lookup"><span data-stu-id="d7210-104">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="d7210-105">由 XML 資料流或文件提供的資訊，可與 <xref:System.Data.DataSet> 中的現有資料或結構描述資訊結合。</span><span class="sxs-lookup"><span data-stu-id="d7210-105">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="d7210-106">ADO.NET 也可讓您建立 <xref:System.Data.DataSet> 的 XML 表示 (可具備或不具備其結構描述)，以便透過 HTTP 將 <xref:System.Data.DataSet> 傳輸給另一個應用程式或啟用 XML 的平台使用。</span><span class="sxs-lookup"><span data-stu-id="d7210-106">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="d7210-107">在 <xref:System.Data.DataSet> 的 XML 表示中，資料是以 XML 撰寫的；而結構描述如果是內嵌在表示中，則是以 XML 結構描述定義語言 (XSD) 所撰寫。</span><span class="sxs-lookup"><span data-stu-id="d7210-107">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="d7210-108">XML 和 XML 結構描述可讓您用方便的格式將 <xref:System.Data.DataSet> 的內容傳輸給遠端用戶端，也可以從遠端用戶端傳出。</span><span class="sxs-lookup"><span data-stu-id="d7210-108">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7210-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="d7210-109">In This Section</span></span>  
 [<span data-ttu-id="d7210-110">DiffGram</span><span class="sxs-lookup"><span data-stu-id="d7210-110">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 <span data-ttu-id="d7210-111">提供 DiffGram 的詳細資訊，這是用來讀取和寫入 <xref:System.Data.DataSet> 內容的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="d7210-111">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d7210-112">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="d7210-112">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 <span data-ttu-id="d7210-113">討論從 XML 文件載入 <xref:System.Data.DataSet> 內容時，需要考慮的不同選項。</span><span class="sxs-lookup"><span data-stu-id="d7210-113">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="d7210-114">將資料集內容當作 XML 資料寫入</span><span class="sxs-lookup"><span data-stu-id="d7210-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="d7210-115">討論如何將 <xref:System.Data.DataSet> 的內容產生為 XML 資料，以及您可以使用的不同 XML 格式選項。</span><span class="sxs-lookup"><span data-stu-id="d7210-115">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="d7210-116">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="d7210-116">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="d7210-117">討論可從 XML 載入 <xref:System.Data.DataSet> 之結構描述的 <xref:System.Data.DataSet> 方法。</span><span class="sxs-lookup"><span data-stu-id="d7210-117">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="d7210-118">將資料集結構描述資訊當作 XSD 寫入</span><span class="sxs-lookup"><span data-stu-id="d7210-118">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="d7210-119">討論 XML 結構描述的使用方式，以及如何從 <xref:System.Data.DataSet> 產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="d7210-119">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d7210-120">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="d7210-120">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="d7210-121">討論 .NET Framework 中有哪些可用功能可同步存取單一資料集的關聯式和階層式檢視，以及如何在 <xref:System.Data.DataSet> 與 <xref:System.Xml.XmlDataDocument> 之間建立同步關係。</span><span class="sxs-lookup"><span data-stu-id="d7210-121">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="d7210-122">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="d7210-122">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="d7210-123">討論將 <xref:System.Data.DataRelation> 的內容表示為 XML 資料時，巢狀 <xref:System.Data.DataSet> 物件的重要性，並描述如何建立這些關聯性。</span><span class="sxs-lookup"><span data-stu-id="d7210-123">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="d7210-124">從 XML 結構描述 (XSD) 衍生資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="d7210-124">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d7210-125">說明從 XML 結構描述中建立的 <xref:System.Data.DataSet> 之關聯式結構 (或結構描述)。</span><span class="sxs-lookup"><span data-stu-id="d7210-125">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="d7210-126">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="d7210-126">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="d7210-127">說明從 XML 項目推斷時所建立的 <xref:System.Data.DataSet> 關聯式結構或結構描述。</span><span class="sxs-lookup"><span data-stu-id="d7210-127">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7210-128">相關章節</span><span class="sxs-lookup"><span data-stu-id="d7210-128">Related Sections</span></span>  
 [<span data-ttu-id="d7210-129">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="d7210-129">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="d7210-130">說明 ADO.NET 的架構和元件，以及如何使用它們來存取現有資料來源和管理應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="d7210-130">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7210-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7210-131">See Also</span></span>  
 [<span data-ttu-id="d7210-132">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="d7210-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="d7210-133">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d7210-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
