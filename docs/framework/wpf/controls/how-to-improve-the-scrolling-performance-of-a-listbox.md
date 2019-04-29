---
title: HOW TO：改善 ListBox 的捲動效能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: a9d1ca1d8ac2ef830984408f3052eb0ed0987c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770860"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>HOW TO：改善 ListBox 的捲動效能
如果<xref:System.Windows.Controls.ListBox>包含許多項目，當使用者捲動時，使用者介面回應可能會很慢<xref:System.Windows.Controls.ListBox>藉由使用滑鼠滾輪，或拖曳捲軸捲動方塊。 您可以改善效能<xref:System.Windows.Controls.ListBox>當使用者捲動藉由設定`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>。  
  
## <a name="example"></a>範例  
  
## <a name="description"></a>描述  
下列範例會建立<xref:System.Windows.Controls.ListBox>，並設定`VirtualizingStackPanel.VirtualizationMode`; 附加屬性<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>改善捲動期間的效能。  
  
## <a name="code"></a>程式碼  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 下列範例會顯示先前的範例使用的資料。  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
