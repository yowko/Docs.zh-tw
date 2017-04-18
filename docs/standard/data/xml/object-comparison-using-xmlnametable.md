---
title: "使用 XmlNameTable 進行物件比較 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 使用 XmlNameTable 進行物件比較
建立 **XmlDocuments** 時，會為此文件特別建立一個名稱表。  當 XML 載入文件，或新項目或屬性建立時，屬性和項目名稱會放入 **XmlNameTable**。  您也可以使用另一個文件中現有的 **NameTable** 來建立 **XmlDocument**。  當 **XmlDocuments** 是以使用 **XmlNameTable** 參數的建構函式建立時，文件可以存取已經儲存在 **XmlNameTable** 中的節點名稱、命名空間和前置詞。  無論名稱表是以何種名稱載入，一旦名稱儲存在表格後，就可以快速地透過物件比較來比較名稱，而不需要進行字串比較。  字串也可以使用 [NameTable.Add 方法](frlrfSystemXmlNameTableClassAddTopic)加入至名稱表。  下列程式碼範例將說明要建立的名稱表，以及要加入表格的字串 **MyString**。  之後，**XmlDocument** 會透過此表格來建立，並且 **Myfile.xml** 中的項目和屬性名稱也會加入至現有的名稱表。  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 下列程式碼範例顯示文件的建立，並且會將兩個新項目加入至文件，這兩個新項目也會加入至文件名稱表，以及名稱上的物件比較。  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 上述在兩個文件之間傳遞的名稱表是相同類型的文件要重複處理 \(例如在電子商務網站上排序文件\) 情況下的典型案例，它會依據 XML 結構描述定義語言 \(XSD\) 描述結構或文件類型定義 \(DTD\)，而且相同的字串會重複。  當多重文件中出現相同的項目名稱時，使用相同的名稱表可以改善效能。  
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)