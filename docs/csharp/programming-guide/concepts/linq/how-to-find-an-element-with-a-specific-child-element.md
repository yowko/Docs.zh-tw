---
title: '如何尋找具有特定子專案的元素（c #）'
description: 瞭解如何尋找具有特定子專案的元素。 請參閱程式碼範例和其他資源。
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301706"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>如何尋找具有特定子專案的元素（c #）
本主題顯示如何利用特定的值尋找具有子項目的特定項目。  
  
## <a name="example"></a>範例  
 此範例會利用 "Examp2.EXE" 這個值，尋找具有 `Test` 子項目的 `CommandLine` 項目。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：測試組態 (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md)。  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 此程式碼會產生下列輸出：  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a>範例  
 下列範例顯示命名空間中之 XML 的相同查詢。 如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。  
  
 此範例使用下列 XML 文件︰[範例 XML 檔：命名空間中的測試組態](./sample-xml-file-test-configuration-in-a-namespace1.md)。  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 此程式碼會產生下列輸出：  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [標準查詢運算子概觀 (C#)](./standard-query-operators-overview.md)
- [投射作業 (C#)](./projection-operations.md)
