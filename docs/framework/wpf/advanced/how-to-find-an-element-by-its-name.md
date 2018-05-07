---
title: 如何：依名稱尋找項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: e2d176c9334c0a1d4c10819e0dc9f2c408e41d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-an-element-by-its-name"></a>如何：依名稱尋找項目
這個範例說明如何使用<xref:System.Windows.FrameworkElement.FindName%2A>方法來尋找項目由其<xref:System.Windows.FrameworkElement.Name%2A>值。  
  
## <a name="example"></a>範例  
 在此範例中，若要尋找特定的項目依其名稱的方法會寫入成為按鈕的事件處理常式。 `stackPanel` 是<xref:System.Windows.FrameworkElement.Name%2A>根的<xref:System.Windows.FrameworkElement>正在搜尋範例方法然後以視覺方式表示找到的項目透過將轉型成<xref:System.Windows.Controls.TextBlock>和變更其中一個<xref:System.Windows.Controls.TextBlock>可見[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]屬性。  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
