---
title: 如何：使用程式碼建立繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: 616487a16ebbe6e23fe067fb7ce72644aa3f919f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458855"
---
# <a name="how-to-create-a-binding-in-code"></a>如何：使用程式碼建立繫結
這個範例示範如何在程式碼中建立和設定 <xref:System.Windows.Data.Binding>。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.FrameworkElement> 類別和 <xref:System.Windows.FrameworkContentElement> 類別都會公開 `SetBinding` 方法。 如果您要系結的元素會繼承其中任一類別，您可以直接呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A> 方法。  
  
 下列範例會建立名為的類別，`MyData`，其中包含名為 `MyDataProperty`的屬性。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 下列範例顯示如何建立系結物件，以設定系結的來源。  此範例會使用 <xref:System.Windows.FrameworkElement.SetBinding%2A>，將 `myText`的 <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性（也就是 <xref:System.Windows.Controls.TextBlock> 控制項）系結至 `MyDataProperty`。  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 如需完整的程式碼範例，請參閱[僅限程式碼](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))系結範例。  
  
 您可以使用 <xref:System.Windows.Data.BindingOperations> 類別的 <xref:System.Windows.Data.BindingOperations.SetBinding%2A> 靜態方法，而不是呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A>。 下列範例會呼叫 <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType>，而不是將 `myText` 系結至 `myDataProperty`的 <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType>。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>請參閱

- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
