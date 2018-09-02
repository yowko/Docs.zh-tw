---
title: 資料集結構描述推斷程序摘要
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 1583d5232a3dd483bbe2a6fa0b1bc8a3ae6a659f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395819"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="0c501-102">資料集結構描述推斷程序摘要</span><span class="sxs-lookup"><span data-stu-id="0c501-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="0c501-103">推斷程序首先會決定要將 XML 文件的哪個項目推斷為資料表，</span><span class="sxs-lookup"><span data-stu-id="0c501-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="0c501-104">再從剩餘的 XML 決定這些資料表的資料行，</span><span class="sxs-lookup"><span data-stu-id="0c501-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="0c501-105">若為巢狀資料表，推斷程序會產生巢狀的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。</span><span class="sxs-lookup"><span data-stu-id="0c501-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="0c501-106">下列為推斷規則的簡明摘要：</span><span class="sxs-lookup"><span data-stu-id="0c501-106">Following is a brief summary of inference rules:</span></span>  
  
-   <span data-ttu-id="0c501-107">具有屬性的項目會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="0c501-107">Elements that have attributes are inferred as tables.</span></span>  
  
-   <span data-ttu-id="0c501-108">具有項目子系的項目會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="0c501-108">Elements that have child elements are inferred as tables.</span></span>  
  
-   <span data-ttu-id="0c501-109">重複的項目會推斷為單一資料表。</span><span class="sxs-lookup"><span data-stu-id="0c501-109">Elements that repeat are inferred as a single table.</span></span>  
  
-   <span data-ttu-id="0c501-110">如果文件或根項目沒有可被推斷為資料行的屬性和子項目，則該項目將被推斷為 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="0c501-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="0c501-111">否則，該文件項目就會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="0c501-111">Otherwise, the document element is inferred as a table.</span></span>  
  
-   <span data-ttu-id="0c501-112">屬性會推斷為資料行。</span><span class="sxs-lookup"><span data-stu-id="0c501-112">Attributes are inferred as columns.</span></span>  
  
-   <span data-ttu-id="0c501-113">沒有屬性或項目子系且不重複的項目，會推斷為資料行。</span><span class="sxs-lookup"><span data-stu-id="0c501-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
-   <span data-ttu-id="0c501-114">會推斷為巢狀資料表也被推斷其他項目中的項目做為資料表、 巢狀**DataRelation**建立兩個資料表之間。</span><span class="sxs-lookup"><span data-stu-id="0c501-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="0c501-115">新的主要索引鍵資料行名為**TableName_Id**加入兩個資料表，並使用**DataRelation**。</span><span class="sxs-lookup"><span data-stu-id="0c501-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="0c501-116">A **ForeignKeyConstraint**會使用兩個資料表之間建立**TableName_Id**資料行。</span><span class="sxs-lookup"><span data-stu-id="0c501-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
-   <span data-ttu-id="0c501-117">針對項目，會推斷為資料表，並可包含文字，但不有任何子項目，新的資料行名為**TableName_Text**建立每個元素的文字。</span><span class="sxs-lookup"><span data-stu-id="0c501-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="0c501-118">如果項目是推斷為資料表且同時具有文字和項目子系，則會忽略文字。</span><span class="sxs-lookup"><span data-stu-id="0c501-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c501-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c501-119">See Also</span></span>  
 [<span data-ttu-id="0c501-120">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="0c501-120">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="0c501-121">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="0c501-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="0c501-122">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="0c501-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [<span data-ttu-id="0c501-123">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="0c501-123">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="0c501-124">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="0c501-124">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="0c501-125">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="0c501-125">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
