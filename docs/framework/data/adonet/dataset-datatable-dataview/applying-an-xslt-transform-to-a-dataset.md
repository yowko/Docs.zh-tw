---
title: 將 XSLT 轉換套用至 DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 09f2e4ee-1d08-4ba8-8936-83394fee319d
ms.openlocfilehash: 3f066f29b99ade6e92a263110fed8079208567b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151490"
---
# <a name="applying-an-xslt-transform-to-a-dataset"></a><span data-ttu-id="6ae86-102">將 XSLT 轉換套用至 DataSet</span><span class="sxs-lookup"><span data-stu-id="6ae86-102">Applying an XSLT Transform to a DataSet</span></span>

<span data-ttu-id="6ae86-103">的**WriteXml**方法<xref:System.Data.DataSet>使您能夠將**資料集**的內容寫入 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="6ae86-103">The **WriteXml** method of the <xref:System.Data.DataSet> enables you to write the contents of a **DataSet** as XML data.</span></span> <span data-ttu-id="6ae86-104">接下來，通用工作會使用 XML 轉換 (XSLT)，將這個 XML 轉換為另一種格式。</span><span class="sxs-lookup"><span data-stu-id="6ae86-104">A common task is to then transform that XML to another format using XSL transformations (XSLT).</span></span> <span data-ttu-id="6ae86-105">但是，將**資料集**與 同步<xref:System.Xml.XmlDataDocument>資料集使您能夠將 XSLT 樣式表應用於**DataSet**的內容，而無需首先使用**WriteXml**將**資料集**的內容寫入 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="6ae86-105">However, synchronizing a **DataSet** with an <xref:System.Xml.XmlDataDocument> enables you to apply an XSLT stylesheet to the contents of a **DataSet** without having to first write the contents of the **DataSet** as XML data using **WriteXml**.</span></span>  
  
 <span data-ttu-id="6ae86-106">下面的示例使用表和關係填充**DataSet，** 將**資料集**與**XmlDataDocument**同步，並使用 XSLT 樣式表將**DataSet**的一部分寫入 HTML 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ae86-106">The following example populates a **DataSet** with tables and relationships, synchronizes the **DataSet** with an **XmlDataDocument**, and writes a portion of the **DataSet** as an HTML file using an XSLT stylesheet.</span></span> <span data-ttu-id="6ae86-107">以下是 XSLT 樣式表的內容：</span><span class="sxs-lookup"><span data-stu-id="6ae86-107">The following are the contents of the XSLT stylesheet:</span></span>
  
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
  
 <span data-ttu-id="6ae86-108">以下代碼填充**DataSet**並應用 XSLT 樣式表。</span><span class="sxs-lookup"><span data-stu-id="6ae86-108">The following code fills the **DataSet** and applies the XSLT style sheet.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ae86-109">如果要將 XSLT 樣式表應用於包含關係的**DataSet，** 則如果為每個嵌套關係將<xref:System.Data.DataRelation>的**嵌套**屬性設置為**true，** 則實現最佳性能。</span><span class="sxs-lookup"><span data-stu-id="6ae86-109">If you are applying an XSLT style sheet to a **DataSet** that contains relations, you achieve best performance if you set the **Nested** property of the <xref:System.Data.DataRelation> to **true** for each nested relation.</span></span> <span data-ttu-id="6ae86-110">這樣您就可以使用一般由上往下執行的 XSLT 樣式表，而不使用增強效能的 XPath 位置軸 (例如，樣式表中之前和之後同層級節點測試運算式)，來巡覽階層並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="6ae86-110">This allows you to use XSLT style sheets that implement natural top-down processing to navigate the hierarchy and transform the data, as opposed to using performance-intensive XPath location axes (for example, preceding-sibling and following-sibling in style sheet node test expressions) to navigate it.</span></span> <span data-ttu-id="6ae86-111">有關嵌套關係的詳細資訊，請參閱[嵌套資料關係](nesting-datarelations.md)。</span><span class="sxs-lookup"><span data-stu-id="6ae86-111">For more information on nested relations, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ae86-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ae86-112">See also</span></span>

- [<span data-ttu-id="6ae86-113">資料集和 XmlDataDocument 同步處理</span><span class="sxs-lookup"><span data-stu-id="6ae86-113">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- <span data-ttu-id="6ae86-114">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="6ae86-114">[ADO.NET Overview](../ado-net-overview.md)</span></span>
