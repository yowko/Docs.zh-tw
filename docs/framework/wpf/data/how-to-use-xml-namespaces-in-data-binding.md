---
title: 操作說明：在資料繫結中使用 XML 命名空間
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740583"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>操作說明：在資料繫結中使用 XML 命名空間
## <a name="example"></a>範例
 這個範例示範如何處理 XML 系結來源中指定的命名空間。

 如果您的 XML 資料具有下列 XML 命名空間定義：

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 您可以使用 <xref:System.Windows.Data.XmlNamespaceMapping> 元素，將命名空間對應至 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>，如下列範例所示。 然後，您可以使用 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 來參考 XML 命名空間。 此範例中的 <xref:System.Windows.Controls.ListBox> 會顯示每個*專案*的*標題*和*dc： date* 。

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 請注意，您指定的 <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> 不一定要與 XML 來源中使用的相同。如果 XML 來源中的前置詞變更，則您的對應仍可運作。

 在此特定範例中，XML 資料來自 web 服務，但 <xref:System.Windows.Data.XmlNamespaceMapping> 元素也適用于內嵌檔案中的內嵌 XML 或 XML 資料。

## <a name="see-also"></a>請參閱

- [使用 XMLDataProvider 和 XPath 查詢繫結至 XML 資料](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
