---
title: "如何：建立和使用 GridLengthConverter 物件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 300916ec102682e1d886d43fbe70eeaf088d6454
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>如何：建立和使用 GridLengthConverter 物件
## <a name="example"></a>範例  
 下列範例示範如何建立和使用的執行個體<xref:System.Windows.GridLengthConverter>。 此範例會定義自訂的方法呼叫`changeCol`，哪個階段<xref:System.Windows.Controls.ListBoxItem>至<xref:System.Windows.GridLengthConverter>將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Windows.GridLength>。 轉換的值再傳遞的值為<xref:System.Windows.Controls.ColumnDefinition.Width%2A>屬性<xref:System.Windows.Controls.ColumnDefinition>項目。  
  
 此範例也會定義自訂第二種方法，呼叫`changeColVal`。 這個自訂的方法會將轉換<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>的<xref:System.Windows.Controls.Slider>至<xref:System.String>，以及傳回值，然後傳遞<xref:System.Windows.Controls.ColumnDefinition>為<xref:System.Windows.Controls.ColumnDefinition.Width%2A>的項目。  
  
 請注意，個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案會定義的內容<xref:System.Windows.Controls.ListBoxItem>。  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
