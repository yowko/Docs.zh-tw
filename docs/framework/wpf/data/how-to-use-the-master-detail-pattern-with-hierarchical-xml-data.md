---
title: HOW TO：使用含階層式 XML 資料的主從式模式
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 2b1ed34fe363f44a3a9eb80dc56d721868329717
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378102"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>HOW TO：使用含階層式 XML 資料的主從式模式
此範例示範如何實作主從式案例[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]資料。  
  
## <a name="example"></a>範例  
 此範例中是[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]中所討論的範例資料版本[使用含階層式資料的主從式模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)。 在此範例中的資料是從檔案`League.xml`。 請注意如何第三個<xref:System.Windows.Controls.ListBox>控制項中第二個追蹤選取範圍變更<xref:System.Windows.Controls.ListBox>繫結至其<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>屬性。  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.HierarchicalDataTemplate>
- [HOW-TO 主題](data-binding-how-to-topics.md)
