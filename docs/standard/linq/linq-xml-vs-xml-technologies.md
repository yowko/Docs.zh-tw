---
title: LINQ to XML 與其他 XML 技術的比較
description: 瞭解 LINQ to XML 與 XSLT、MSXML 和 XmlLite 的比較，以提供更好的技術選擇。
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: ac118543bd1101e50edfcf99a609a715b885bfbd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552268"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML 與其他 XML 技術的比較

本文將比較 LINQ to XML 與下列 XML 技術： <xref:System.Xml.XmlReader> 、XSLT、MSXML 和 XmlLite。 此資訊可協助您決定要使用的技術。

如需 LINQ to XML 與檔物件模型 (DOM) 的比較，請參閱 [LINQ to XML 與 dom](linq-xml-vs-dom.md)的比較。

## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML 與 XmlReader 之比較

<xref:System.Xml.XmlReader> 是一個快速、順向、非快取的剖析器。

LINQ to XML 會在之上執行 <xref:System.Xml.XmlReader> ，而且它們會緊密整合。 不過，您也可以 <xref:System.Xml.XmlReader> 直接使用。

例如，假設您要建立一個會每秒剖析數百個 XML 檔的 Web 服務，而且檔具有相同的結構，這表示您只需要撰寫程式碼的其中一個程式碼，就可以剖析 XML。 在此情況下，您可能會想要 <xref:System.Xml.XmlReader> 直接使用。

相反地，如果您要建立剖析許多較小 XML 檔的系統，而且每個檔都不同，您可能會想要利用 LINQ to XML 所提供的產能改善功能。

## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML 與 XSLT 之比較

LINQ to XML 和 XSLT 都提供大量的 XML 檔轉換功能。 XSLT 是一種以規則為基礎的宣告式方法。 高級的 XSLT 程式設計人員會以功能性程式設計方式，撰寫強調沒有狀態 (Stateless) 方法的 XSLT。 您可以使用實作時沒有副作用的純虛擬函式來撰寫轉換。 許多開發人員不熟悉這個以規則為基礎或功能性方法，而且學習起來可能既困難又耗時。

XSLT 可以是產生高效能應用程式的生產系統。 例如，某些大型的網路公司會使用 XSLT，從 XML 產生 HTML，並從不同類型的資料存放區提取。 Managed XSLT 引擎會將 XSLT 編譯為 common language runtime (CLR) 程式碼，在某些情況下執行的效果更優於原生 XSLT 引擎。

不過，XSLT 無法利用許多開發人員所擁有的 c # 和 Visual Basic 知識。 它需要開發人員以不同而且複雜的程式設計語言撰寫程式碼。 使用兩個非整合式開發系統 (例如，C# (或 Visual Basic) 和 XSLT) 會使軟體系統難以開發與維護。

在您 LINQ to XML 查詢運算式之後，LINQ to XML 轉換是很容易使用的強大技術。 基本上，您可以形成自己的 XML 文件，方法是，使用功能結構、從各種來源納入資料、動態建構 <xref:System.Xml.Linq.XElement> 物件，然後將全部組合成一個新的 XML 樹狀結構。 轉換可以產生全新的文件。 在 LINQ to XML 中建立轉換相當簡單且直覺化，而且產生的程式碼是可讀取的。 這會降低開發與維護的成本。

LINQ to XML 不適合取代 XSLT。 XSLT 仍然是複雜且以檔為主的 XML 轉換所選擇的工具，特別是當檔的結構未妥善定義時。

XSLT 具有做為全球資訊網協會 (W3C) 標準的優點。 如果您的需求為只使用標準的技術，XSLT 可能更合適。

XSLT 是 XML，因此可以用程式設計的方式操作。

## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML 與 MSXML 之比較

MSXML 是以 COM 為基礎的技術，用於處理 Microsoft Windows 隨附的 XML。 MSXML 會提供 DOM 的原始實作 (包含對於 XPath 和 XSLT 的支援)， 同時也包含 SAX2 非快取的事件型剖析器。

MSXML 的執行效果很好，在大部分的情況下預設是安全的，而且可以在 Internet Explorer 中存取，以在 AJAX 樣式的應用程式中進行用戶端 XML 處理。 從支援 COM (包括 C++、JavaScript 和 Visual Basic 6.0) 的任何程式設計語言都可以使用 MSXML。

不建議在以 CLR 為基礎的 managed 程式碼中使用 MSXML。

## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML 與 XmlLite 之比較

XmlLite 是一個非快取、順向、提取的剖析器。 開發人員主要會使用 XmlLite 搭配 C++。 開發人員不建議將 XmlLite 與 managed 程式碼搭配使用。

XmlLite 的主要優點是，它是輕量、快速的 XML 剖析器，在大部分的情況下都是安全的。 它的威脅表面區域很小。 如果您必須剖析不受信任的文件，而且您想要防止諸如阻絕服務或洩漏資料等攻擊，XmlLite 可能是一個相當好的選擇。

XmlLite 未與 (LINQ) 的語言整合式查詢整合。 它不會讓程式設計人員的產能改善成為 LINQ 背後的動機。

## <a name="see-also"></a>另請參閱

- [LINQ to XML 總覽](linq-xml-overview.md)
