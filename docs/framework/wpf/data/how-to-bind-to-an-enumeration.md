---
title: 如何：繫結至列舉
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: 93f33e497fd7acb81c55f86bf38737d4e7d79bf2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454448"
---
# <a name="how-to-bind-to-an-enumeration"></a>如何：繫結至列舉
這個範例示範如何系結至列舉的 GetValues 方法，以系結至列舉。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Controls.ListBox> 會透過資料系結顯示 <xref:System.Windows.HorizontalAlignment> 列舉值的清單。 <xref:System.Windows.Controls.ListBox> 和 <xref:System.Windows.Controls.Button> 系結，讓您可以藉由選取 <xref:System.Windows.Controls.ListBox>中的值來變更 <xref:System.Windows.Controls.Button> 的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 屬性值。  
  
 [!code-xaml[BindToEnum#BindToEnum](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>請參閱

- [繫結至方法](how-to-bind-to-a-method.md)
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
