---
title: 如何：置放 Grid 的子項目
description: 瞭解如何使用在 Windows Presentation Foundation 方格上定義的 get 和 set 方法，來定位子項目。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: 926d223097dd21dd0292c9523903b4be8aba8ba9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167393"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>如何：置放 Grid 的子項目
這個範例示範如何使用在上定義的 get 和 set 方法 <xref:System.Windows.Controls.Grid> 來定位子專案。  
  
## <a name="example"></a>範例  
 下列範例 <xref:System.Windows.Controls.Grid> `grid1` 會定義具有三個數據行和三個數據列的父元素（）。 子 <xref:System.Windows.Shapes.Rectangle> 元素（ `rect1` ）會加入至資料 <xref:System.Windows.Controls.Grid> 行位置零、資料列位置零。 <xref:System.Windows.Controls.Button>元素代表可以呼叫的方法，以重新放置 <xref:System.Windows.Shapes.Rectangle> 中的專案 <xref:System.Windows.Controls.Grid> 。 當使用者按一下按鈕時，就會啟用相關的方法。  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 下列程式碼後置範例會處理按鈕 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件引發的方法。 這個範例會將這些方法呼叫寫入 <xref:System.Windows.Controls.TextBlock> 使用相關 get 方法的元素，以將新的屬性值輸出為字串。  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 完成的結果如下所示！

 ![螢幕擷取畫面顯示具有兩個數據行的 WPF 使用者介面，右側有 3 x 3 個方格，而左邊有按鈕可在方格的資料行和資料列之間移動彩色矩形](././media/grid-methods-sample.png)
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Grid>
- [面板概觀](panels-overview.md)
