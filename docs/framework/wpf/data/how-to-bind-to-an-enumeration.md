---
title: HOW TO：繫結至列舉
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
ms.openlocfilehash: db7b02a961c148bbdc31b05e7c71ea5b5d301c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586562"
---
# <a name="how-to-bind-to-an-enumeration"></a>HOW TO：繫結至列舉
此範例示範如何將繫結至繫結至列舉型別的 GetValues 方法來列舉型別。  
  
## <a name="example"></a>範例  
 在下列範例中，<xref:System.Windows.Controls.ListBox>顯示的清單<xref:System.Windows.HorizontalAlignment>透過資料繫結的列舉值。 <xref:System.Windows.Controls.ListBox>而<xref:System.Windows.Controls.Button>，您可以變更繫結<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>屬性值<xref:System.Windows.Controls.Button>選取中的值<xref:System.Windows.Controls.ListBox>。  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>另請參閱
- [繫結至方法](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)
- [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
