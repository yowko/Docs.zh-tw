---
title: 如何：從 CSV 檔案產生 XML (C#)
ms.date: 07/20/2015
ms.assetid: 57b9ccde-f983-4a21-ae61-70ecede30307
ms.openlocfilehash: 71fc10d4b48737a816532fa16f4e621c81050ab3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-generate-xml-from-csv-files-c"></a><span data-ttu-id="3fa9a-102">如何：從 CSV 檔案產生 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa9a-102">How to: Generate XML from CSV Files (C#)</span></span>
<span data-ttu-id="3fa9a-103">此範例顯示如何使用 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]，從以逗號分隔的 (CSV) 檔案產生 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="3fa9a-103">This example shows how to use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to generate an XML file from a comma-separated value (CSV) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fa9a-104">範例</span><span class="sxs-lookup"><span data-stu-id="3fa9a-104">Example</span></span>  
 <span data-ttu-id="3fa9a-105">下列程式碼會在字串的陣列上執行 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="3fa9a-105">The following code performs a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query on an array of strings.</span></span>  
  
 <span data-ttu-id="3fa9a-106">此查詢使用 `let` 子句，將每個字串分割為欄位的陣列。</span><span class="sxs-lookup"><span data-stu-id="3fa9a-106">The query uses the `let` clause to split each string into an array of fields.</span></span>  
  
```csharp  
// Create the text file.  
string csvString = @"GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA";  
File.WriteAllText("cust.csv", csvString);  
  
// Read into an array of strings.  
string[] source = File.ReadAllLines("cust.csv");  
XElement cust = new XElement("Root",  
    from str in source  
    let fields = str.Split(',')  
    select new XElement("Customer",  
        new XAttribute("CustomerID", fields[0]),  
        new XElement("CompanyName", fields[1]),  
        new XElement("ContactName", fields[2]),  
        new XElement("ContactTitle", fields[3]),  
        new XElement("Phone", fields[4]),  
        new XElement("FullAddress",  
            new XElement("Address", fields[5]),  
            new XElement("City", fields[6]),  
            new XElement("Region", fields[7]),  
            new XElement("PostalCode", fields[8]),  
            new XElement("Country", fields[9])  
        )  
    )  
);  
Console.WriteLine(cust);  
```  
  
 <span data-ttu-id="3fa9a-107">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="3fa9a-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="LAZYK">  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(509) 555-7969</Phone>  
    <FullAddress>  
      <Address>12 Orchestra Terrace</Address>  
      <City>Walla Walla</City>  
      <Region>WA</Region>  
      <PostalCode>99362</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
  <Customer CustomerID="LETSS">  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <ContactTitle>Owner</ContactTitle>  
    <Phone>(415) 555-5938</Phone>  
    <FullAddress>  
      <Address>87 Polk St. Suite 5</Address>  
      <City>San Francisco</City>  
      <Region>CA</Region>  
      <PostalCode>94117</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
  </Customer>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fa9a-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="3fa9a-108">See Also</span></span>  
 [<span data-ttu-id="3fa9a-109">投影和轉換 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="3fa9a-109">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
