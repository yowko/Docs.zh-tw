---
title: "資料集和 XmlDataDocument 同步處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: acc68fd36d2887e5e951f9ba5adc20e8cfd87fd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="a723e-102">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="a723e-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="a723e-103">ADO.NET <xref:System.Data.DataSet> 提供資料的關聯式表示。</span><span class="sxs-lookup"><span data-stu-id="a723e-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="a723e-104">若要存取階層式資料，可以使用 .NET Framework 中提供的 XML 類別。</span><span class="sxs-lookup"><span data-stu-id="a723e-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="a723e-105">過去，這兩個資料表示一直是分開使用；</span><span class="sxs-lookup"><span data-stu-id="a723e-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="a723e-106">不過，.NET Framework 會啟用即時、 同步存取資料的關聯式及階層式表示**資料集**物件和<xref:System.Xml.XmlDataDocument>分別物件。</span><span class="sxs-lookup"><span data-stu-id="a723e-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="a723e-107">當**資料集**與同步處理**XmlDataDocument**，這兩個物件正在使用同一組資料。</span><span class="sxs-lookup"><span data-stu-id="a723e-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="a723e-108">這表示，如果變更**資料集**，此變更會反映在**XmlDataDocument**，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a723e-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="a723e-109">之間的關聯性**資料集**和**XmlDataDocument**允許單一應用程式，來存取建置服務的整個套件使用同一組資料，建立更多的彈性周圍**資料集**（例如 Web Form 和 Windows Form 控制項和 Visual Studio.NET 設計工具），以及 XML 服務，包括可延伸樣式表語言 (XSL)、 XSL 轉換 (XSLT) 和 XML 路徑的套件語言 (XPath)。</span><span class="sxs-lookup"><span data-stu-id="a723e-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="a723e-110">您不用替應用程式選擇要將哪一組服務當成目標，因為這兩個服務都可以使用。</span><span class="sxs-lookup"><span data-stu-id="a723e-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="a723e-111">有數種方法，您可以同步處理**資料集**與**XmlDataDocument**。</span><span class="sxs-lookup"><span data-stu-id="a723e-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="a723e-112">您可以：</span><span class="sxs-lookup"><span data-stu-id="a723e-112">You can:</span></span>  
  
-   <span data-ttu-id="a723e-113">填入**資料集**與結構描述 （也就是關聯式結構） 和資料，然後將其與新同步**XmlDataDocument**。</span><span class="sxs-lookup"><span data-stu-id="a723e-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="a723e-114">如此便能提供現有關聯式資料的階層式檢視。</span><span class="sxs-lookup"><span data-stu-id="a723e-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="a723e-115">例如: </span><span class="sxs-lookup"><span data-stu-id="a723e-115">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   <span data-ttu-id="a723e-116">填入**資料集**只含結構描述 (例如強型別**資料集**)，其與同步**XmlDataDocument**，然後載入**XmlDataDocument**從 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a723e-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="a723e-117">如此能提供現有階層式資料的關聯式檢視。</span><span class="sxs-lookup"><span data-stu-id="a723e-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="a723e-118">資料表名稱和資料行名稱，在您**資料集**結構描述必須符合您想要與一起同步處理的 XML 項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="a723e-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="a723e-119">這項比對是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="a723e-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="a723e-120">請注意，結構描述的**資料集**只需要以符合您要公開在關聯式檢視中的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="a723e-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="a723e-121">如此，您可能會有非常大的 XML 文件，但文件中可能會有非常小的關聯式「視窗」。</span><span class="sxs-lookup"><span data-stu-id="a723e-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="a723e-122">**XmlDataDocument**會保留整個 XML 文件時，即使**資料集**只公開它的一小部分。</span><span class="sxs-lookup"><span data-stu-id="a723e-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="a723e-123">(如這個詳細的範例，請參閱[將 DataSet 與 XmlDataDocument 同步處理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)。)</span><span class="sxs-lookup"><span data-stu-id="a723e-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="a723e-124">下列程式碼範例顯示建立步驟**資料集**並填入其結構描述，然後同步處理其與**XmlDataDocument**。</span><span class="sxs-lookup"><span data-stu-id="a723e-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="a723e-125">請注意，**資料集**結構描述只需符合的項目**XmlDataDocument**您想要使用公開 （expose）**資料集**。</span><span class="sxs-lookup"><span data-stu-id="a723e-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="a723e-126">無法載入**XmlDataDocument**如果與同步處理**資料集**，其中包含資料。</span><span class="sxs-lookup"><span data-stu-id="a723e-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="a723e-127">且會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a723e-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="a723e-128">建立新**XmlDataDocument**並載入從 XML 文件，並再存取使用資料的關聯式檢視**資料集**屬性**XmlDataDocument**。</span><span class="sxs-lookup"><span data-stu-id="a723e-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="a723e-129">您需要設定的結構描述**資料集**才能檢視中資料的任何**XmlDataDocument**使用**資料集**。</span><span class="sxs-lookup"><span data-stu-id="a723e-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="a723e-130">同樣地，資料表名稱和資料行名稱在您**資料集**結構描述必須符合您想要與一起同步處理的 XML 項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="a723e-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="a723e-131">這項比對是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="a723e-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="a723e-132">下列程式碼範例示範如何存取資料的關聯式檢視**XmlDataDocument**。</span><span class="sxs-lookup"><span data-stu-id="a723e-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="a723e-133">同步處理的另一個好處**XmlDataDocument**與**資料集**是保留的 XML 文件精確度。</span><span class="sxs-lookup"><span data-stu-id="a723e-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="a723e-134">如果**資料集**填入從 XML 文件使用**ReadXml**，當資料寫回為 XML 文件使用**WriteXml**可能大幅不同從原始的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a723e-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="a723e-135">這是因為**資料集**不會維護格式，例如空白字元或階層的資訊，例如從 XML 文件的項目順序。</span><span class="sxs-lookup"><span data-stu-id="a723e-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="a723e-136">**資料集**也不包含從 XML 文件被忽略，因為它們不符合的結構描述的項目**資料集**。</span><span class="sxs-lookup"><span data-stu-id="a723e-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="a723e-137">同步處理**XmlDataDocument**與**資料集**允許保留在原始的 XML 文件的格式和階層式項目結構**XmlDataDocument**，雖然**資料集**只包含資料和結構描述的資訊適用於**資料集**。</span><span class="sxs-lookup"><span data-stu-id="a723e-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="a723e-138">同步處理時**資料集**與**XmlDataDocument**，結果可能不同，就不會根據您<xref:System.Data.DataRelation>巢狀物件。</span><span class="sxs-lookup"><span data-stu-id="a723e-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="a723e-139">如需詳細資訊，請參閱[巢狀 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="a723e-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a723e-140">本節內容</span><span class="sxs-lookup"><span data-stu-id="a723e-140">In This Section</span></span>  
 [<span data-ttu-id="a723e-141">使用 XmlDataDocument 同步處理資料集</span><span class="sxs-lookup"><span data-stu-id="a723e-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="a723e-142">示範如何同步處理的強型別**資料集**，具有最少的結構描述與**XmlDataDocument**。</span><span class="sxs-lookup"><span data-stu-id="a723e-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="a723e-143">對資料集執行 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="a723e-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="a723e-144">執行 XPath 查詢的內容將示範**資料集**。</span><span class="sxs-lookup"><span data-stu-id="a723e-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="a723e-145">將 XSLT 轉換套用至資料集</span><span class="sxs-lookup"><span data-stu-id="a723e-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="a723e-146">示範如何將 XSLT 轉換套用至內容**資料集**。</span><span class="sxs-lookup"><span data-stu-id="a723e-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a723e-147">相關章節</span><span class="sxs-lookup"><span data-stu-id="a723e-147">Related Sections</span></span>  
 [<span data-ttu-id="a723e-148">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="a723e-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="a723e-149">描述如何**資料集**XML 當成資料來源，包括載入和保存的內容互動**資料集**為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="a723e-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="a723e-150">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="a723e-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="a723e-151">討論的重要性巢狀**DataRelation**物件代表的內容時**資料集**為 XML 資料，並說明如何建立這些關聯性。</span><span class="sxs-lookup"><span data-stu-id="a723e-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="a723e-152">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="a723e-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="a723e-153">描述**資料集**以及如何使用它來管理應用程式資料，並包括關聯式資料庫和 XML 資料來源互動。</span><span class="sxs-lookup"><span data-stu-id="a723e-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="a723e-154">包含的相關參考資訊**XmlDataDocument**類別。</span><span class="sxs-lookup"><span data-stu-id="a723e-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a723e-155">請參閱</span><span class="sxs-lookup"><span data-stu-id="a723e-155">See Also</span></span>  
 [<span data-ttu-id="a723e-156">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="a723e-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
