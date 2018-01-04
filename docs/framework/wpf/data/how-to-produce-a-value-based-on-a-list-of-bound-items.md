---
title: "操作說明：根據繫結項目的清單產生值"
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
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3987690a1acb180ee22fa02e399accd9c5d481d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a>操作說明：根據繫結項目的清單產生值
<xref:System.Windows.Data.MultiBinding>可讓您將繫結目標屬性繫結至來源屬性的清單，然後再套用邏輯，以產生使用給定的輸入值。 這個範例示範如何使用<xref:System.Windows.Data.MultiBinding>。  
  
## <a name="example"></a>範例  
 在下列範例中，`NameListData` 參考 `PersonName` 物件的集合，這些物件都包含兩個屬性：`firstName` 和 `lastName`。 下列範例會產生<xref:System.Windows.Controls.TextBlock>它會顯示第一個具有姓氏個人的第一個和最後一個名稱。  
  
 [!code-xaml[MultiBinding#Resources1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 為了解姓氏-名字格式是如何產生，我們一起看看 `NameConverter` 的實作：  
  
 [!code-csharp[MultiBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 `NameConverter` 會實作 <xref:System.Windows.Data.IMultiValueConverter> 介面。 `NameConverter` 會從個別繫結取得值，然後將這些值儲存在 values 物件陣列中。 順序<xref:System.Windows.Data.Binding>項目會出現在<xref:System.Windows.Data.MultiBinding>項目是儲存在陣列中的這些值的順序。 值<xref:System.Windows.Data.MultiBinding.ConverterParameter%2A>屬性的參數引數由參考<xref:System.Windows.Data.MultiBinding.Converter%2A>方法，用於執行參數來判斷如何格式化名稱在參數上。  
  
## <a name="see-also"></a>請參閱  
 [轉換繫結的資料](../../../../docs/framework/wpf/data/how-to-convert-bound-data.md)  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
