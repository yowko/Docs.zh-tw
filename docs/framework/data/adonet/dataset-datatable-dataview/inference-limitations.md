---
title: 推斷限制
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 4e0f63776162b60c9333ba47be58ea78a9b6805d
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204827"
---
# <a name="inference-limitations"></a><span data-ttu-id="4773e-102">推斷限制</span><span class="sxs-lookup"><span data-stu-id="4773e-102">Inference Limitations</span></span>
<span data-ttu-id="4773e-103">根據每份文件的 XML 項目，當您執行從 XML 推斷 <xref:System.Data.DataSet> 結構描述的處理序時，可能會得到不同的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4773e-103">The process of inferring a <xref:System.Data.DataSet> schema from XML can result in different schemas depending on the XML elements in each document.</span></span> <span data-ttu-id="4773e-104">例如，請考量下列 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="4773e-104">For example, consider the following XML documents.</span></span>  
  
 <span data-ttu-id="4773e-105">Document1:</span><span class="sxs-lookup"><span data-stu-id="4773e-105">Document1:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4773e-106">Document2:</span><span class="sxs-lookup"><span data-stu-id="4773e-106">Document2:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="4773e-107">對於 "Document1", 推斷程式會產生名為 "DocumentElement" 的**資料集**, 以及名為 "Element1" 的資料表, 因為 "Element1" 是重複的元素。</span><span class="sxs-lookup"><span data-stu-id="4773e-107">For "Document1," the inference process produces a **DataSet** named "DocumentElement" and a table named "Element1," because "Element1" is a repeating element.</span></span>  
  
 <span data-ttu-id="4773e-108">**集中**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4773e-108">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="4773e-109">**目錄**Element1</span><span class="sxs-lookup"><span data-stu-id="4773e-109">**Table:** Element1</span></span>  
  
|<span data-ttu-id="4773e-110">Element1_Text</span><span class="sxs-lookup"><span data-stu-id="4773e-110">Element1_Text</span></span>|  
|--------------------|  
|<span data-ttu-id="4773e-111">Text1</span><span class="sxs-lookup"><span data-stu-id="4773e-111">Text1</span></span>|  
|<span data-ttu-id="4773e-112">Text2</span><span class="sxs-lookup"><span data-stu-id="4773e-112">Text2</span></span>|  
  
 <span data-ttu-id="4773e-113">不過, 針對 "Document2.docx", 推斷程式會產生名為 "NewDataSet" 的**資料集**, 以及名為 "DocumentElement" 的資料表。</span><span class="sxs-lookup"><span data-stu-id="4773e-113">However, for "Document2," the inference process produces a **DataSet** named "NewDataSet" and a table named "DocumentElement."</span></span> <span data-ttu-id="4773e-114">Element1 會被推斷為資料行，因為它沒有屬性和項目子系。</span><span class="sxs-lookup"><span data-stu-id="4773e-114">"Element1" is inferred as a column because it has no attributes and no child elements.</span></span>  
  
 <span data-ttu-id="4773e-115">**集中**NewDataSet</span><span class="sxs-lookup"><span data-stu-id="4773e-115">**DataSet:** NewDataSet</span></span>  
  
 <span data-ttu-id="4773e-116">**目錄**DocumentElement</span><span class="sxs-lookup"><span data-stu-id="4773e-116">**Table:** DocumentElement</span></span>  
  
|<span data-ttu-id="4773e-117">Element1</span><span class="sxs-lookup"><span data-stu-id="4773e-117">Element1</span></span>|  
|--------------|  
|<span data-ttu-id="4773e-118">Text1</span><span class="sxs-lookup"><span data-stu-id="4773e-118">Text1</span></span>|  
  
 <span data-ttu-id="4773e-119">這兩份 XML 文件原本可能意圖要產生相同的結構描述，但是根據每份文件包含的項目，推斷程序產生了相當不同的結果。</span><span class="sxs-lookup"><span data-stu-id="4773e-119">These two XML documents may have been intended to produce the same schema, but the inference process produces very different results based on the elements contained in each document.</span></span>  
  
 <span data-ttu-id="4773e-120">若要避免從 XML 檔產生架構時可能發生的不一致, 我們建議您在從 XML 載入**資料集**時, 使用 xml 架構定義語言 (XSD) 或 Xml 資料精簡 (XDR) 明確地指定架構。</span><span class="sxs-lookup"><span data-stu-id="4773e-120">To avoid the discrepancies that can occur when generating schema from an XML document, we recommend that you explicitly specify a schema using XML Schema definition language (XSD) or XML-Data Reduced (XDR) when loading a **DataSet** from XML.</span></span> <span data-ttu-id="4773e-121">如需明確指定具有 XML 架構之**資料集**架構的詳細資訊, 請參閱[從 XML 架構 (XSD) 衍生資料集關聯式結構](deriving-dataset-relational-structure-from-xml-schema-xsd.md)。</span><span class="sxs-lookup"><span data-stu-id="4773e-121">For more information about explicitly specifying a **DataSet** schema with XML Schema, see [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4773e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4773e-122">See also</span></span>

- [<span data-ttu-id="4773e-123">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="4773e-123">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="4773e-124">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="4773e-124">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="4773e-125">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="4773e-125">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="4773e-126">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="4773e-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="4773e-127">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="4773e-127">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="4773e-128">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="4773e-128">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
