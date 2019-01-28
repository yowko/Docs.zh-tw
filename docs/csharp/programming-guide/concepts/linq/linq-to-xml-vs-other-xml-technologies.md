---
title: LINQ to XML 比較其他 XML 技術的比較
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 8e2a6b11e450890373de449c0a55839460b97566
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648648"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML 比較其他 XML 技術之比較
這個主題會比較 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 與下列 XML 技術：<xref:System.Xml.XmlReader>、XSLT、MSXML 和 XmlLite。 這個資訊可以協助您決定要使用的技術。  
  
 若要比較 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 與文件物件模型 (DOM)，請參閱 [LINQ to XML 與DOM (C#) 之比較](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)。  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML 比較XmlReader  
 <xref:System.Xml.XmlReader> 是一個快速、順向、非快取的剖析器。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 會在 <xref:System.Xml.XmlReader> 頂端實作，而且它們會緊密整合。 不過，您也可以單獨使用 <xref:System.Xml.XmlReader>。  
  
 例如，假設您要建置每秒將會剖析數百個 XML 文件的 Web 服務，而且這些文件的結構相同，表示您只需要撰寫一個程式碼實作，就可以剖析 XML。 在這個情況下，您可能想要單獨使用 <xref:System.Xml.XmlReader>。  
  
 相較之下，如果您要建置剖析許多較小 XML 文件的系統，而且每個文件都不同，您可能就會想要利用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 所提供的生產力提升功能。  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML 比較XSLT  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 和 XSLT 都提供大量的 XML 文件轉換功能。 XSLT 是一種以規則為基礎的宣告式方法。 高級的 XSLT 程式設計人員會以功能性程式設計方式，撰寫強調沒有狀態 (Stateless) 方法的 XSLT。 您可以使用實作時沒有副作用的純虛擬函式來撰寫轉換。 許多開發人員不熟悉這個以規則為基礎或功能性方法，而且學習起來可能既困難又耗時。  
  
 XSLT 可以是非常有產能的系統，可產生高效能的應用程式。 例如，有些大型的網路公司會使用 XSLT，根據已經從各種資料存放區提取的 XML 產生 HTML。 Managed XSLT 引擎會將 XSLT 編譯為 CLR 程式碼，而且在某些案例中的效能，甚至比原始 XSLT 引擎更好。  
  
 不過，XSLT 不會使用許多開發人員已經具備的 C# 和 Visual Basic 知識。 它需要開發人員以不同而且複雜的程式設計語言撰寫程式碼。 使用兩個非整合式開發系統 (例如，C# (或 Visual Basic) 和 XSLT) 會使軟體系統難以開發與維護。  
  
 在您熟練 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查詢運算式後，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 轉換即可成為功能強大且易於使用的技術。 基本上，您可以形成自己的 XML 文件，方法是，使用功能結構、從各種來源納入資料、動態建構 <xref:System.Xml.Linq.XElement> 物件，然後將全部組合成一個新的 XML 樹狀結構。 轉換可以產生全新的文件。 在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中進行建構轉換是相當容易與直覺化的作業，並會產生可讀的程式碼。 這會降低開發與維護的成本。  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 並不是要取代 XSLT。 XSLT 仍然是複雜的文件中心 XML 轉換的最佳工具選擇，特別是在沒有正確定義文件結構時。  
  
 XSLT 具有做為全球資訊網協會 (W3C) 標準的優點。 如果您的需求為只使用標準的技術，XSLT 可能更合適。  
  
 XSLT 是 XML，因此可以用程式設計方式操作。  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML 比較MSXML  
 MSXML 是 COM 架構的技術，用於處理 Microsoft Windows 隨附的 XML。 MSXML 會提供 DOM 的原始實作 (包含對於 XPath 和 XSLT 的支援)， 同時也包含 SAX2 非快取的事件型剖析器。  
  
 MSXML 運作良好、在大部分的案例中預設是安全的，而且可以在 Internet Explorer 中存取，以便在 AJAX 型的應用程式中執行用戶端的 XML 處理。 從支援 COM (包括 C++、JavaScript 和 Visual Basic 6.0) 的任何程式設計語言都可以使用 MSXML。  
  
 根據 Common Language Runtime (CLR)，不建議將 MSXML 用於 Managed 程式碼中。  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML 比較XmlLite  
 XmlLite 是一個非快取、順向、提取的剖析器。 開發人員主要會使用 XmlLite 搭配 C++。 不建議開發人員使用 XmlLite 搭配 Managed 程式碼。  
  
 XmlLite 的主要優點在於它是一個快速的輕量型 XML 剖析器，在大部分的案例中是安全的。 其威脅表面區域非常小。 如果您必須剖析不受信任的文件，而且您想要防止諸如阻絕服務或洩漏資料等攻擊，XmlLite 可能是一個相當好的選擇。  
  
 XmlLite 不會與 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 整合在一起。 因此不會提供程式設計人員生產力提升功能，這種功能是 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 背後的驅動力量。  
  
## <a name="see-also"></a>另請參閱

- [使用者入門 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
