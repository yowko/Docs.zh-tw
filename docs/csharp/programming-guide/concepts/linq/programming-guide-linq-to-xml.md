---
title: 程式設計手冊 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
ms.openlocfilehash: acb8271ad9ea338d31516c35bae46593a5fd2f78
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199043"
---
# <a name="programming-guide-linq-to-xml-c"></a>程式設計手冊 (LINQ to XML) (C#)
本節提供使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 進行程式設計的概念性和使用說明資訊。  
  
## <a name="who-should-read-this-documentation"></a>本文件的對象  
 本文件的對象為已經了解 C# 以及部分 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 基本概念的開發人員。  
  
 本文件的目標在於讓各種開發人員容易使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可讓 XML 程式設計更為容易。 您不需要是專業開發人員就可以使用本文件。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 大量依賴泛型類別。 因此，了解泛型類別的用法非常重要。 此外，如果您熟悉宣告為參數化型別的委派，也很有幫助。 如果您不熟悉 C# 泛型類別，請參閱[泛型類別](../../../../csharp/programming-guide/generics/generic-classes.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|描述|  
|-----------|-----------------|  
|[LINQ to XML 程式設計概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 類別的概觀，以及關於其中三個最重要類別的詳細資訊：<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XDocument>。|  
|[建立 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|提供有關使用 XML 樹狀的概念性與工作型資訊。 您可以使用功能結構，或從字串或檔案剖析 XML 文字，藉以建立 XML 樹狀結構。 您也可以使用 <xref:System.Xml.XmlReader> 來填入 XML 樹狀結構。|  
|[處理 XML 命名空間 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|提供有關建立使用命名空間之 XML 樹狀的詳細資訊。|  
|[序列化 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|描述多個序列化 XML 樹狀的方法，並提供要使用哪個方法的指引。|  
|[LINQ to XML 座標軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|列舉並描述 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 座標軸方法，您必須在撰寫 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢之前了解這些方法。|  
|[查詢 XML 樹狀結構 (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|提供查詢 XML 樹狀的常見範例。|  
|[修改 XML 樹狀結構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|如同文件物件模型 (DOM)，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 可讓您就地修改 XML 樹狀結構。|  
|[進階 LINQ to XML 程式設計 (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|提供附註、事件、串流以及其他進階案例的相關資訊。|  
|[LINQ to XML 安全性 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|描述與 LINQ to XML 相關聯的安全性問題，並提供一些減少暴露其安全性的指引。|  
|[範例 XML 文件 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|包含本文件中的許多範例所使用的 XML 範例文件。|  
  
## <a name="see-also"></a>請參閱

- [使用者入門 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
- [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
