---
title: 推斷限制
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: e584d8c5fa9e8c4f659b57f8fe24b12339ae79d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639584"
---
# <a name="inference-limitations"></a><span data-ttu-id="6c583-102">推斷限制</span><span class="sxs-lookup"><span data-stu-id="6c583-102">Inference Limitations</span></span>
<span data-ttu-id="6c583-103">根據每份文件的 XML 項目，當您執行從 XML 推斷 <xref:System.Data.DataSet> 結構描述的處理序時，可能會得到不同的結構描述。</span><span class="sxs-lookup"><span data-stu-id="6c583-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="6c583-104">例如，請考量下列 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="6c583-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="6c583-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="6c583-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="6c583-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="6c583-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="6c583-107">針對 「 文件 1 」，推斷程序會產生**資料集**名為"DocumentElement 」 和名為"Element1，"因為 「 Element1 」 是重複的項目。</span><span class="sxs-lookup"><span data-stu-id="6c583-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="6c583-108">**資料集：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6c583-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="6c583-109">**資料表：** Element1</span><span class="sxs-lookup"><span data-stu-id="6c583-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="6c583-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="6c583-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="6c583-111">Text1</span><span class="sxs-lookup"><span data-stu-id="6c583-111">Text1</span></span>|  
|<span data-ttu-id="6c583-112">Text2</span><span class="sxs-lookup"><span data-stu-id="6c583-112">Text2</span></span>|  
  
 <span data-ttu-id="6c583-113">不過，針對 「 Document2"，推斷程序會產生**資料集**名為"NewDataSet"和名為"DocumentElement。 」</span><span class="sxs-lookup"><span data-stu-id="6c583-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="6c583-114">Element1 會被推斷為資料行，因為它沒有屬性和項目子系。</span><span class="sxs-lookup"><span data-stu-id="6c583-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="6c583-115">**資料集：** NewDataSet</span><span class="sxs-lookup"><span data-stu-id="6c583-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="6c583-116">**資料表：** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="6c583-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="6c583-117">Element1</span><span class="sxs-lookup"><span data-stu-id="6c583-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="6c583-118">Text1</span><span class="sxs-lookup"><span data-stu-id="6c583-118">Text1</span></span>|  
  
 <span data-ttu-id="6c583-119">這兩份 XML 文件原本可能意圖要產生相同的結構描述，但是根據每份文件包含的項目，推斷程序產生了相當不同的結果。</span><span class="sxs-lookup"><span data-stu-id="6c583-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="6c583-120">若要避免從 XML 文件產生結構描述時，可能會發生不一致，我們建議您明確指定載入時，使用 XML 結構描述定義語言 (XSD) 或 XML 資料精簡 (XDR) 結構描述**資料集**從XML。</span><span class="sxs-lookup"><span data-stu-id="6c583-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="6c583-121">如需有關明確指定**資料集**結構描述與 XML 結構描述，請參閱[衍生的資料集關聯式結構從 XML 結構描述 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="6c583-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c583-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c583-122">See also</span></span>
- [<span data-ttu-id="6c583-123">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="6c583-123">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="6c583-124">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="6c583-124">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [<span data-ttu-id="6c583-125">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="6c583-125">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="6c583-126">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="6c583-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [<span data-ttu-id="6c583-127">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="6c583-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="6c583-128">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6c583-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
