---
title: XML LINQ to XML 的功能性轉換
description: 瞭解修改 XML 檔的純功能性轉換方法，以及它與程式化方法有何不同。
ms.date: 07/20/2015
ms.assetid: 0ccb9251-38d7-44e3-9b84-1b5fe25e4b59
ms.openlocfilehash: b23288e013a4104b21523e17e1f266a9f712c451
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552138"
---
# <a name="functional-transformation-of-xml-linq-to-xml"></a>XML (LINQ to XML) 的功能性轉換

本文將討論用來修改 XML 檔的純功能性轉換方法，並將它與程式化方法形成對比。

## <a name="modifying-an-xml-document"></a>修改 XML 檔

XML 程式設計人員其中一個最常見的工做為，將 XML 從一個組織結構轉換為另一個組織結構。 XML 文件的組織結構就是文件的結構，其中包括：

- 以文件表示的階層。
- 項目和屬性名稱。
- 項目和屬性的資料型別。

一般而言，將 XML 從一個組織結構轉換為另一個組織結構最有效的方法是，純功能性轉換的方法。 以此種方法，程式設計人員的主要工做為建立適用於整個 XML 文件 (或者一或多個嚴格定義的程式碼) 的轉換。 在論證上，功能性轉換對程式碼而言是最簡單的 (在程式設計人員熟悉方法之後)，它會產生最容易維護的程式碼，而且通常比替代方法更精簡。

### <a name="xml-functional-transformational-technologies"></a>XML 功能轉換技術

Microsoft 提供兩個可用於 XML 文件的功能性轉換技術：XSLT 和 LINQ to XML。 在 <xref:System.Xml.Xsl> Managed 命名空間與 MSXML 的原始 COM 實作中支援 XSLT。 雖然 XSLT 是強大的管理 XML 文件技術，但是它需要特殊領域的專業知識，也就是 XSLT 語言及其支援的 API。

LINQ to XML 在 C# 或 Visual Basic 程式碼中，提供以明確而且強大的方式撰寫純功能性轉換之程式碼所需的工具。 例如，LINQ to XML 文件中的許多範例都使用純功能性方法。 此外，在 [教學課程：操作 WordprocessingML 檔中的內容](xml-shape-wordprocessingml-documents.md) 教學課程中，我們使用 LINQ to XML 以功能性方法操作 Microsoft Word 檔中的資訊。

如需更完整的 LINQ to XML 與其他 Microsoft XML 技術的比較，請參閱 [LINQ to XML 與其他 xml 技術](linq-xml-vs-xml-technologies.md)的比較。

當來源文件具有不規則的結構時，XSLT 是文件中心轉換的建議工具。 不過，LINQ to XML 也可以執行文件中心的轉換。 如需詳細資訊，請參閱 [如何使用批註來轉換 XSLT 樣式的 LINQ to XML 樹狀](use-annotations-transform-linq-xml-trees-xslt-style.md)結構。

## <a name="see-also"></a>另請參閱

- [純功能性轉換簡介](introduction-pure-functional-transformations.md)
- [教學課程：操作 WordprocessingML 檔中的內容](xml-shape-wordprocessingml-documents.md)
- [LINQ to XML 與其他 XML 技術的比較](linq-xml-vs-xml-technologies.md)
