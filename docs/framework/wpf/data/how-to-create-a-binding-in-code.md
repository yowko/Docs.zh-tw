---
title: HOW TO：使用程式碼建立繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 57ec845c5c9a5bddb801428b9ecde035a97cf447
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089259"
---
# <a name="how-to-create-a-binding-in-code"></a>HOW TO：使用程式碼建立繫結
此範例示範如何建立並設定<xref:System.Windows.Data.Binding>在程式碼中。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.FrameworkElement>類別和<xref:System.Windows.FrameworkContentElement>類別兩者公開`SetBinding`方法。 如果您要繫結項目繼承這些類別其中一種方法，您可以呼叫<xref:System.Windows.FrameworkElement.SetBinding%2A>直接方法。  
  
 下列範例會建立名為類別`MyData`，其中包含一個名為屬性`MyDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 下列範例示範如何建立繫結物件，以設定繫結的來源。  此範例會使用<xref:System.Windows.FrameworkElement.SetBinding%2A>繫結<xref:System.Windows.Controls.TextBlock.Text%2A>屬性`myText`，即<xref:System.Windows.Controls.TextBlock>控制項，為`MyDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 如需完整的程式碼範例，請參閱[僅適用程式碼的繫結範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))。  
  
 而不是呼叫<xref:System.Windows.FrameworkElement.SetBinding%2A>，您可以使用<xref:System.Windows.Data.BindingOperations.SetBinding%2A>靜態方法<xref:System.Windows.Data.BindingOperations>類別。 下列範例中，會呼叫<xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>而非<xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>繫結`myText`至`myDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>另請參閱

- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
