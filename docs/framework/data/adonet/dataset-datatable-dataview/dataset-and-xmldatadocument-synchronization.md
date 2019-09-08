---
title: 資料集和 XmlDataDocument 同步處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: e76e81153cb7d074fe975744c6b6041ee04be90f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785423"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="4e32d-102">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="4e32d-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="4e32d-103">ADO.NET <xref:System.Data.DataSet> 提供資料的關聯式表示。</span><span class="sxs-lookup"><span data-stu-id="4e32d-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="4e32d-104">若要存取階層式資料，可以使用 .NET Framework 中提供的 XML 類別。</span><span class="sxs-lookup"><span data-stu-id="4e32d-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="4e32d-105">過去，這兩個資料表示一直是分開使用；</span><span class="sxs-lookup"><span data-stu-id="4e32d-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="4e32d-106">不過，.NET Framework 會分別透過**DataSet**物件和<xref:System.Xml.XmlDataDocument>物件，啟用即時、同步存取關聯式和階層式的資料標記法。</span><span class="sxs-lookup"><span data-stu-id="4e32d-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="4e32d-107">當**資料集**與**XmlDataDocument**同步處理時，這兩個物件都會使用單一資料集。</span><span class="sxs-lookup"><span data-stu-id="4e32d-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="4e32d-108">這表示，如果對**資料集**進行變更，變更就會反映在**XmlDataDocument**中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4e32d-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="4e32d-109">**資料集**和**XmlDataDocument**之間的關聯性可讓單一應用程式（使用單一資料集）存取以**資料集**為基礎的整個服務套件（例如 Web form 和），以建立極大的彈性。Windows Forms 控制項和 Visual Studio .NET 設計工具），以及 XML 服務的套件，包括可延伸樣式表語言（XSL）、XSL 轉換（XSLT）和 XML 路徑語言（XPath）。</span><span class="sxs-lookup"><span data-stu-id="4e32d-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="4e32d-110">您不用替應用程式選擇要將哪一組服務當成目標，因為這兩個服務都可以使用。</span><span class="sxs-lookup"><span data-stu-id="4e32d-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="4e32d-111">有數種方式可讓您將**資料集**與**XmlDataDocument**同步處理。</span><span class="sxs-lookup"><span data-stu-id="4e32d-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="4e32d-112">您可以：</span><span class="sxs-lookup"><span data-stu-id="4e32d-112">You can:</span></span>  
  
- <span data-ttu-id="4e32d-113">使用架構（也就是關聯式結構）和資料填入資料**集**，然後將它與新的**XmlDataDocument**同步處理。</span><span class="sxs-lookup"><span data-stu-id="4e32d-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="4e32d-114">如此便能提供現有關聯式資料的階層式檢視。</span><span class="sxs-lookup"><span data-stu-id="4e32d-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="4e32d-115">例如：</span><span class="sxs-lookup"><span data-stu-id="4e32d-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="4e32d-116">僅以架構填入**資料集**（例如強型別**資料集**），將它與**XmlDataDocument**同步處理，然後從 XML 檔載入**XmlDataDocument** 。</span><span class="sxs-lookup"><span data-stu-id="4e32d-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="4e32d-117">如此能提供現有階層式資料的關聯式檢視。</span><span class="sxs-lookup"><span data-stu-id="4e32d-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="4e32d-118">DataSet 架構中的資料表名稱和**資料**行名稱，必須與您想要同步處理的 XML 元素名稱相符。</span><span class="sxs-lookup"><span data-stu-id="4e32d-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="4e32d-119">這項比對是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="4e32d-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="4e32d-120">請注意，**資料集**的架構只需要符合您想要在關聯式視圖中公開的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="4e32d-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="4e32d-121">如此，您可能會有非常大的 XML 文件，但文件中可能會有非常小的關聯式「視窗」。</span><span class="sxs-lookup"><span data-stu-id="4e32d-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="4e32d-122">即使**資料集**只公開其中的一小部分， **XmlDataDocument**還是會保留整個 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="4e32d-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="4e32d-123">（如需這項工作的詳細範例，請參閱[同步處理資料集與 XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md)）。</span><span class="sxs-lookup"><span data-stu-id="4e32d-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="4e32d-124">下列程式碼範例示範如何建立**資料集**並填入其架構，然後將它與**XmlDataDocument**同步處理的步驟。</span><span class="sxs-lookup"><span data-stu-id="4e32d-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="4e32d-125">請注意，**資料集**架構只需要符合您想要使用**資料集**公開之**XmlDataDocument**中的元素。</span><span class="sxs-lookup"><span data-stu-id="4e32d-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="4e32d-126">如果**XmlDataDocument**與包含資料的**DataSet**同步處理，您就無法載入它。</span><span class="sxs-lookup"><span data-stu-id="4e32d-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="4e32d-127">且會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4e32d-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="4e32d-128">建立新的**XmlDataDocument** ，並從 XML 檔載入它，然後使用**XmlDataDocument**的**DataSet**屬性來存取資料的關聯式視圖。</span><span class="sxs-lookup"><span data-stu-id="4e32d-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="4e32d-129">您必須先設定**資料集**的架構，才能使用**資料集**來查看**XmlDataDocument**中的任何資料。</span><span class="sxs-lookup"><span data-stu-id="4e32d-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="4e32d-130">同樣地，DataSet 架構中的資料表名稱和**資料**行名稱，必須與您想要與之同步處理的 XML 元素名稱相符。</span><span class="sxs-lookup"><span data-stu-id="4e32d-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="4e32d-131">這項比對是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="4e32d-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="4e32d-132">下列程式碼範例顯示如何在**XmlDataDocument**中存取資料的關聯式視圖。</span><span class="sxs-lookup"><span data-stu-id="4e32d-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="4e32d-133">將**XmlDataDocument**與**資料集**同步處理的另一個優點是，會保留 XML 檔的精確度。</span><span class="sxs-lookup"><span data-stu-id="4e32d-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="4e32d-134">如果資料**集**是使用**ReadXml**從 xml 檔填入，則在使用**WriteXml**將資料寫回為 xml 檔時，可能會與原始 XML 檔有相當大的差異。</span><span class="sxs-lookup"><span data-stu-id="4e32d-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="4e32d-135">這是因為**資料集**不會維護 XML 檔中的格式，例如空白字元或階層式資訊，例如元素順序。</span><span class="sxs-lookup"><span data-stu-id="4e32d-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="4e32d-136">**DataSet**也不包含 XML 檔中已忽略的元素，因為它們不符合**資料集**的架構。</span><span class="sxs-lookup"><span data-stu-id="4e32d-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="4e32d-137">同步處理**XmlDataDocument**與**資料集**，可讓原始 XML 檔的格式設定和階層式元素結構在**XmlDataDocument**中維護，而**資料集**只包含資料和適用于**資料集**的架構資訊。</span><span class="sxs-lookup"><span data-stu-id="4e32d-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="4e32d-138">將**資料集**與**XmlDataDocument**同步處理時，結果可能會根據您<xref:System.Data.DataRelation>的物件是否已嵌套而有所不同。</span><span class="sxs-lookup"><span data-stu-id="4e32d-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="4e32d-139">如需詳細資訊，請參閱 <<c0>嵌套 datarelation。</span><span class="sxs-lookup"><span data-stu-id="4e32d-139">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e32d-140">本節內容</span><span class="sxs-lookup"><span data-stu-id="4e32d-140">In This Section</span></span>  
 [<span data-ttu-id="4e32d-141">使用 XmlDataDocument 同步處理資料集</span><span class="sxs-lookup"><span data-stu-id="4e32d-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="4e32d-142">示範如何使用**XmlDataDocument**來同步處理強型別**資料集**與最少的架構。</span><span class="sxs-lookup"><span data-stu-id="4e32d-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="4e32d-143">對資料集執行 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="4e32d-143">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="4e32d-144">示範對**資料集**的內容執行 XPath 查詢。</span><span class="sxs-lookup"><span data-stu-id="4e32d-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="4e32d-145">將 XSLT 轉換套用至資料集</span><span class="sxs-lookup"><span data-stu-id="4e32d-145">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="4e32d-146">示範如何將 XSLT 轉換套用至**資料集**的內容。</span><span class="sxs-lookup"><span data-stu-id="4e32d-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4e32d-147">相關章節</span><span class="sxs-lookup"><span data-stu-id="4e32d-147">Related Sections</span></span>  
 [<span data-ttu-id="4e32d-148">在 DataSet 中使用 XML</span><span class="sxs-lookup"><span data-stu-id="4e32d-148">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="4e32d-149">描述**資料集**如何與 xml 做為資料來源互動，包括將**資料集**的內容載入和保存為 xml 資料。</span><span class="sxs-lookup"><span data-stu-id="4e32d-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="4e32d-150">巢狀 DataRelation</span><span class="sxs-lookup"><span data-stu-id="4e32d-150">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="4e32d-151">討論將**資料集**的內容表示為 XML 資料時，嵌套**DataRelation**物件的重要性，並描述如何建立這些關聯性。</span><span class="sxs-lookup"><span data-stu-id="4e32d-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="4e32d-152">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="4e32d-152">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="4e32d-153">描述**資料集**以及如何使用它來管理應用程式資料，以及與資料來源互動，包括關係資料庫和 XML。</span><span class="sxs-lookup"><span data-stu-id="4e32d-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="4e32d-154">包含**XmlDataDocument**類別的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="4e32d-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e32d-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e32d-155">See also</span></span>

- [<span data-ttu-id="4e32d-156">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="4e32d-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
