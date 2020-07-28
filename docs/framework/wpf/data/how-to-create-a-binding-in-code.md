---
title: 如何：使用程式碼建立繫結
description: 瞭解如何藉由直接呼叫 SetBinding 方法，在 Windows Presentation Foundation 應用程式的程式碼中建立系結。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], creating
- data binding [WPF], creating
ms.assetid: 1a606db9-cf5f-42ed-a1c5-9e4722ec77a0
ms.openlocfilehash: aa2a29f4c1262d8ac54641b856c297b284b23a38
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165813"
---
# <a name="how-to-create-a-binding-in-code"></a>如何：使用程式碼建立繫結
這個範例示範如何在程式碼中建立和設定 <xref:System.Windows.Data.Binding> 。  
  
## <a name="example"></a>範例  
 <xref:System.Windows.FrameworkElement>類別和 <xref:System.Windows.FrameworkContentElement> 類別都公開 `SetBinding` 方法。 如果您要系結的元素會繼承其中任一類別，您可以直接呼叫 <xref:System.Windows.FrameworkElement.SetBinding%2A> 方法。  
  
 下列範例會建立名為的類別， `MyData` 其中包含名為的屬性 `MyDataProperty` 。  
  
 [!code-csharp[CodeOnlyBinding#DataObject](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/MyData.cs#dataobject)]
 [!code-vb[CodeOnlyBinding#DataObject](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/MyData.vb#dataobject)]  
  
 下列範例顯示如何建立系結物件，以設定系結的來源。  此範例會使用，將的 <xref:System.Windows.FrameworkElement.SetBinding%2A> <xref:System.Windows.Controls.TextBlock.Text%2A> 屬性 `myText` （即 <xref:System.Windows.Controls.TextBlock> 控制項）系結至 `MyDataProperty` 。  
  
 [!code-csharp[CodeOnlyBinding#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#1)]
 [!code-vb[CodeOnlyBinding#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#1)]  
  
 如需完整的程式碼範例，請參閱[僅限程式碼](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771500(v=vs.90))系結範例。  
  
 <xref:System.Windows.FrameworkElement.SetBinding%2A>您可以使用類別的靜態方法，而不是呼叫 <xref:System.Windows.Data.BindingOperations.SetBinding%2A> <xref:System.Windows.Data.BindingOperations> 。 下列範例會呼叫， <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=nameWithType> 而不是系結 <xref:System.Windows.FrameworkElement.SetBinding%2A?displayProperty=nameWithType> `myText` 至 `myDataProperty` 。  
  
 [!code-csharp[CodeOnlyBinding#BOSetBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#bosetbinding)]
 [!code-vb[CodeOnlyBinding#BOSetBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#bosetbinding)]  
  
## <a name="see-also"></a>另請參閱

- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [操作說明主題](data-binding-how-to-topics.md)
