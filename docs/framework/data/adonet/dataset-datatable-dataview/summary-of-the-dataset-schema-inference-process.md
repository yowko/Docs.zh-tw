---
title: 資料集結構描述推斷程序摘要
ms.date: 03/30/2017
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
ms.openlocfilehash: 8d517487b96aa7f204ea9f25d326500db7df413a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198505"
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="acc7e-102">資料集結構描述推斷程序摘要</span><span class="sxs-lookup"><span data-stu-id="acc7e-102">Summary of the DataSet Schema Inference Process</span></span>

<span data-ttu-id="acc7e-103">推斷程序首先會決定要將 XML 文件的哪個項目推斷為資料表，</span><span class="sxs-lookup"><span data-stu-id="acc7e-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="acc7e-104">再從剩餘的 XML 決定這些資料表的資料行，</span><span class="sxs-lookup"><span data-stu-id="acc7e-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="acc7e-105">若為巢狀資料表，推斷程序會產生巢狀的 <xref:System.Data.DataRelation> 和 <xref:System.Data.ForeignKeyConstraint> 物件。</span><span class="sxs-lookup"><span data-stu-id="acc7e-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="acc7e-106">以下是推斷規則的簡短摘要：</span><span class="sxs-lookup"><span data-stu-id="acc7e-106">The following is a brief summary of inference rules:</span></span>  
  
- <span data-ttu-id="acc7e-107">具有屬性的項目會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="acc7e-107">Elements that have attributes are inferred as tables.</span></span>  
  
- <span data-ttu-id="acc7e-108">具有項目子系的項目會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="acc7e-108">Elements that have child elements are inferred as tables.</span></span>  
  
- <span data-ttu-id="acc7e-109">重複的項目會推斷為單一資料表。</span><span class="sxs-lookup"><span data-stu-id="acc7e-109">Elements that repeat are inferred as a single table.</span></span>  
  
- <span data-ttu-id="acc7e-110">如果文件或根項目沒有可被推斷為資料行的屬性和子項目，則該項目將被推斷為 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="acc7e-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="acc7e-111">否則，該文件項目就會推斷為資料表。</span><span class="sxs-lookup"><span data-stu-id="acc7e-111">Otherwise, the document element is inferred as a table.</span></span>  
  
- <span data-ttu-id="acc7e-112">屬性會推斷為資料行。</span><span class="sxs-lookup"><span data-stu-id="acc7e-112">Attributes are inferred as columns.</span></span>  
  
- <span data-ttu-id="acc7e-113">沒有屬性或項目子系且不重複的項目，會推斷為資料行。</span><span class="sxs-lookup"><span data-stu-id="acc7e-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
- <span data-ttu-id="acc7e-114">針對在其他專案（也會推斷為數據表）中推斷為嵌套資料表的專案，會在這兩個數據表之間建立嵌套 **DataRelation** 。</span><span class="sxs-lookup"><span data-stu-id="acc7e-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="acc7e-115">名為 **TableName_Id** 的新主鍵資料行，會加入至這兩個數據表，而且 **DataRelation**所使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="acc7e-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="acc7e-116">使用**TableName_Id**資料行，在兩個數據表之間建立**ForeignKeyConstraint** 。</span><span class="sxs-lookup"><span data-stu-id="acc7e-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
- <span data-ttu-id="acc7e-117">對於推斷為數據表且包含文字但沒有子專案的專案，會針對每個元素的文字建立名為 **TableName_Text** 的新資料行。</span><span class="sxs-lookup"><span data-stu-id="acc7e-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="acc7e-118">如果項目是推斷為資料表且同時具有文字和項目子系，則會忽略文字。</span><span class="sxs-lookup"><span data-stu-id="acc7e-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc7e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acc7e-119">See also</span></span>

- [<span data-ttu-id="acc7e-120">從 XML 推斷資料集關聯式結構</span><span class="sxs-lookup"><span data-stu-id="acc7e-120">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="acc7e-121">從 XML 載入資料集</span><span class="sxs-lookup"><span data-stu-id="acc7e-121">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="acc7e-122">從 XML 載入資料集結構描述資訊</span><span class="sxs-lookup"><span data-stu-id="acc7e-122">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="acc7e-123">在資料集中使用 XML</span><span class="sxs-lookup"><span data-stu-id="acc7e-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="acc7e-124">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="acc7e-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- <span data-ttu-id="acc7e-125">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="acc7e-125">[ADO.NET Overview](../ado-net-overview.md)</span></span>
