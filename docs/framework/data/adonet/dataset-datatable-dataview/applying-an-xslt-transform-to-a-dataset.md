---
title: 將 XSLT 轉換套用至 DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 5b3aca6a71f88762084934d0d9c7cea15b5366c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072593"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="b6bf4-102">將 XSLT 轉換套用至 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6bf4-102">Applying an XSLT Transform to a DataSet</span></span>
<span data-ttu-id="b6bf4-103">**WriteXml**方法<xref:System.Data.DataSet>可讓您的內容寫入**DataSet**為 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-103">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="b6bf4-104">接下來，通用工作會使用 XML 轉換 (XSLT)，將這個 XML 轉換為另一種格式。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-104">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="b6bf4-105">不過，同步處理**資料集**具有<xref:System.Xml.XmlDataDocument>可讓您套用 XSLT 樣式表的內容**DataSet**而不必先寫入的內容**資料集**做為 XML 資料使用**WriteXml**。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-105">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="b6bf4-106">下列範例會填入**資料集**與資料表和關聯性，同步處理**資料集**具有**XmlDataDocument**，並將寫入一部分**資料集**為 HTML 檔案中使用的 XSLT 樣式表。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-106">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="b6bf4-107">下列為 XSLT 樣式表的內容。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-107">Following are the contents of the XSLT stylesheet.</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
<xsl:template match="CustomerOrders">  
  <HTML>  
  <STYLE>  
  BODY {font-family:verdana;font-size:9pt}  
  TD   {font-size:8pt}  
  </STYLE>  
    <BODY>  
    <TABLE BORDER="1">  
      <xsl:apply-templates select="Customers"/>  
    </TABLE>  
    </BODY>  
  </HTML>  
</xsl:template>  
  
<xsl:template match="Customers">  
    <TR><TD>  
      <xsl:value-of select="ContactName"/>, <xsl:value-of select="Phone"/><BR/>  
    </TD></TR>  
      <xsl:apply-templates select="Orders"/>  
</xsl:template>  
  
<xsl:template match="Orders">  
  <TABLE BORDER="1">  
    <TR><TD valign="top"><B>Order:</B></TD><TD valign="top"><xsl:value-of select="OrderID"/></TD></TR>  
    <TR><TD valign="top"><B>Date:</B></TD><TD valign="top"><xsl:value-of select="OrderDate"/></TD></TR>  
    <TR><TD valign="top"><B>Ship To:</B></TD>  
        <TD valign="top"><xsl:value-of select="ShipName"/><BR/>  
        <xsl:value-of select="ShipAddress"/><BR/>  
        <xsl:value-of select="ShipCity"/>, <xsl:value-of select="ShipRegion"/>  <xsl:value-of select="ShipPostalCode"/><BR/>  
        <xsl:value-of select="ShipCountry"/></TD></TR>  
  </TABLE>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
 <span data-ttu-id="b6bf4-108">下列程式碼會填入**資料集**並套用 XSLT 樣式表。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-108">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6bf4-109">如果您要套用至 XSLT 樣式表**資料集**，其中包含的關聯，即可達到最佳效能，如果您將設定**巢狀**屬性<xref:System.Data.DataRelation>至**true**每個巢狀關聯性。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-109">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="b6bf4-110">這樣您就可以使用一般由上往下執行的 XSLT 樣式表，而不使用增強效能的 XPath 位置軸 (例如，樣式表中之前和之後同層級節點測試運算式)，來巡覽階層並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-110">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="b6bf4-111">如需有關巢狀關聯的詳細資訊，請參閱[巢狀 Datarelation](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="b6bf4-111">For more information on nested relations, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)   
  
Dim xslTran As XslTransform = New XslTransform  
xslTran.Load("transform.xsl")  
  
Dim writer As XmlTextWriter = New XmlTextWriter( _  
  "xslt_output.html", System.Text.Encoding.UTF8)  
  
xslTran.Transform(xmlDoc, Nothing, writer)  
writer.Close()  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
connection.Open();  
  
DataSet custDS = new DataSet("CustomerDataSet");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(custDS, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(custDS, "Orders");  
  
connection.Close();  
  
custDS.Relations.Add("CustOrders",  
  custDS.Tables["Customers"].Columns["CustomerID"],  
                     custDS.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(custDS);   
  
XslTransform xslTran = new XslTransform();  
xslTran.Load("transform.xsl");  
  
XmlTextWriter writer = new XmlTextWriter("xslt_output.html",   
  System.Text.Encoding.UTF8);  
  
xslTran.Transform(xmlDoc, null, writer);  
writer.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6bf4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6bf4-112">See also</span></span>

- [<span data-ttu-id="b6bf4-113">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="b6bf4-113">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="b6bf4-114">ADO.NET Managed 提供者和DataSet開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b6bf4-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
