---
title: HOW TO：依名稱尋找項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: 7405f9ba8db5d4db0ce35ca250f13e456685f39b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351038"
---
# <a name="how-to-find-an-element-by-its-name"></a>HOW TO：依名稱尋找項目
此範例說明如何使用<xref:System.Windows.FrameworkElement.FindName%2A>方法來尋找項目由其<xref:System.Windows.FrameworkElement.Name%2A>值。  
  
## <a name="example"></a>範例  
 在此範例中，會以按鈕的事件處理常式寫入方法來依名稱尋找特定的項目。 `stackPanel` 是<xref:System.Windows.FrameworkElement.Name%2A>的根目錄<xref:System.Windows.FrameworkElement>所搜尋範例方法然後以視覺方式表示找到的項目轉換成<xref:System.Windows.Controls.TextBlock>和變更的其中一個<xref:System.Windows.Controls.TextBlock>可見[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]屬性。  
  
 [!code-csharp[FEFindName#Find](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
