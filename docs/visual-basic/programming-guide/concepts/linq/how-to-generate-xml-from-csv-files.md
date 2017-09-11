---
title: "如何︰ 從 CSV 檔案 (Visual Basic) 中產生 XML |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: fe4dbc87-7b0d-40bf-88c3-5d706ee89a4d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: a36818659adbeef13e2468170360aba090ecc1cb
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---
# <a name="how-to-generate-xml-from-csv-files-visual-basic"></a><span data-ttu-id="353bd-102">如何︰ 從 CSV 檔案 (Visual Basic) 中產生 XML</span><span class="sxs-lookup"><span data-stu-id="353bd-102">How to: Generate XML from CSV Files (Visual Basic)</span></span>
<span data-ttu-id="353bd-103">此範例顯示如何使用 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] 和 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，從以逗號分隔的 (CSV) 檔案產生 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="353bd-103">This example shows how to use [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] and [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] to generate an XML file from a comma-separated value (CSV) file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="353bd-104">範例</span><span class="sxs-lookup"><span data-stu-id="353bd-104">Example</span></span>  
 <span data-ttu-id="353bd-105">下列程式碼會在字串的陣列上執行 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="353bd-105">The following code performs a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query on an array of strings.</span></span>  
  
```vb  
      ' Create the text file.  
Dim csvString As String = "GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA" & vbCrLf & _  
    "HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA" & vbCrLf & _  
    "LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA" & vbCrLf & _  
    "LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA"  
File.WriteAllText("cust.csv", csvString)  
  
' Read into an array of strings.  
Dim source As String() = File.ReadAllLines("cust.csv")  
Dim cust As XElement = _  
    <Root>  
        <%= From strs In source _  
            Let fields = Split(strs, ",") _  
            Select _  
            <Customer CustomerID=<%= fields(0) %>>  
                <CompanyName><%= fields(1) %></CompanyName>  
                <ContactName><%= fields(2) %></ContactName>  
                <ContactTitle><%= fields(3) %></ContactTitle>  
                <Phone><%= fields(4) %></Phone>  
                <FullAddress>  
                    <Address><%= fields(5) %></Address>  
                    <City><%= fields(6) %></City>  
                    <Region><%= fields(7) %></Region>  
                    <PostalCode><%= fields(8) %></PostalCode>  
                    <Country><%= fields(9) %></Country>  
                </FullAddress>  
            </Customer> _  
        %>  
    </Root>  
Console.WriteLine(cust)  
```  
  
 <span data-ttu-id="353bd-106">此程式碼會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="353bd-106">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="353bd-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="353bd-107">See Also</span></span>  
 [<span data-ttu-id="353bd-108">投影和轉換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="353bd-108">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

