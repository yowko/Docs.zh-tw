---
title: 如何：繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
ms.openlocfilehash: 070f67f30613d4522a48e08fd1c208fbe5887525
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920116"
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a>如何：繫結至 XML 查詢結果的 XDocument、XElement 或 LINQ

這個範例示範如何使用 <xref:System.Xml.Linq.XDocument>將 XML 資料系結至 <xref:System.Windows.Controls.ItemsControl>。

## <a name="example"></a>範例

下列 XAML 程式碼會定義 <xref:System.Windows.Controls.ItemsControl>，並包含 `http://planetsNS` XML 命名空間中 `Planet` 類型資料的資料範本。 佔用命名空間的 XML 資料類型必須將命名空間放在大括號中，而如果它出現在 XAML 標記延伸可能出現的位置，則必須在命名空間前面加上大括號逸出序列。 此程式碼會系結至與 <xref:System.Xml.Linq.XElement> 類別的 <xref:System.Xml.Linq.XContainer.Element%2A> 和 <xref:System.Xml.Linq.XElement.Attribute%2A> 方法對應的動態屬性。 動態屬性可以讓 XAML 繫結至共用方法名稱的動態屬性。 若要深入瞭解，請參閱[LINQ to XML 動態屬性](linq-to-xml-dynamic-properties.md)。 請注意，XML 的預設命名空間宣告不適用於屬性名稱。

[!code-xaml[XLinqExample#StackPanelResources](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]
[!code-xaml[XLinqExample#ItemsControl](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]

下列C#程式碼會呼叫<xref:System.Xml.Linq.XDocument.Load%2A>，並將堆疊面板資料內容設定為`http://planetsNS`XML 命名空間中名為`SolarSystemPlanets`之專案的所有子項目。

[!code-csharp[XLinqExample#LoadDCFromFile](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
[!code-vb[XLinqExample#LoadDCFromFile](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]

XML 資料可以使用 <xref:System.Windows.Data.ObjectDataProvider>儲存為 XAML 資源。 如需完整範例，請參閱[l2dbform.xaml。](l2dbform-xaml-source-code.md) 下列範例顯示程式碼如何將資料內容設定為物件資源。

[!code-csharp[XLinqExample#LoadDCFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
[!code-vb[XLinqExample#LoadDCFromXAML](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]

對應至 <xref:System.Xml.Linq.XContainer.Element%2A> 和 <xref:System.Xml.Linq.XElement.Attribute%2A> 的動態屬性可在 XAML 中提供彈性。 您的程式碼也可以繫結至 LINQ for XML 查詢的結果。 此範例會繫結至依照元素值排序的查詢結果。

[!code-csharp[XLinqExample#BindToResults](~/samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
[!code-vb[XLinqExample#BindToResults](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]

## <a name="see-also"></a>請參閱

- [繫結來源概觀](binding-sources-overview.md)
- [WPF 資料繫結與 LINQ to XML 概觀](wpf-data-binding-with-linq-to-xml-overview.md)
- [使用 LINQ to XML 的 WPF 資料繫結範例](linq-to-xml-data-binding-sample.md)
- [LINQ to XML 動態屬性](linq-to-xml-dynamic-properties.md)
