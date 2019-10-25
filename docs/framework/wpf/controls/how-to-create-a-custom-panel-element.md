---
title: 如何：建立自訂面板項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799141"
---
# <a name="how-to-create-a-custom-panel-element"></a>如何：建立自訂面板項目
## <a name="example"></a>範例  
 這個範例會示範如何覆寫 <xref:System.Windows.Controls.Panel> 專案的預設版面配置行為，並建立衍生自 <xref:System.Windows.Controls.Panel>的自訂配置元素。  
  
 這個範例會定義一個稱為 `PlotPanel`的簡單自訂 <xref:System.Windows.Controls.Panel> 專案，這會根據兩個硬式編碼的 x 和 y 座標來放置子項目。 在此範例中，`x` 和 `y` 都設定為 `50`;因此，所有子專案都位於 x 和 y 軸的該位置。  
  
 若要執行自訂 <xref:System.Windows.Controls.Panel> 行為，此範例會使用 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法。 每個方法都會傳回位置和呈現子專案所需的 <xref:System.Windows.Size> 資料。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Controls.Panel>
- [面板概觀](panels-overview.md)
