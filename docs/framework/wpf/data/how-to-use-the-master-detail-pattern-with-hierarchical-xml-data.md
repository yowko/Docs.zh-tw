---
title: 如何：使用含階層式 XML 資料的主從式模式
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: eb8dbdd8-5871-42bb-a16b-04e655fea677
ms.openlocfilehash: 0fe42d57fcaf4acee09340fdb3f5df73d7291566
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733422"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-xml-data"></a>如何：使用含階層式 XML 資料的主從式模式
這個範例示範如何使用 XML 資料來執行主版詳細案例。  
  
## <a name="example"></a>範例  
 這個範例是[使用具有階層式資料的主版詳細模式](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)中所討論之範例的 XML 資料版本。 在此範例中，資料來自 `League.xml`的檔案。 請注意第三個 <xref:System.Windows.Controls.ListBox> 控制項如何藉由系結至其 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> 屬性來追蹤第二個 <xref:System.Windows.Controls.ListBox> 中的選取範圍變更。  
  
 [!code-xaml[MasterDetailXml#HowTo1](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto1)]  
[!code-xaml[MasterDetailXml#HowTo2](~/samples/snippets/csharp/VS_Snippets_Wpf/MasterDetailXml/CS/Window1.xaml#howto2)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.HierarchicalDataTemplate>
- [「如何」主題](data-binding-how-to-topics.md)
