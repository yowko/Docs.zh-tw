---
title: 作法：指定繫結的方向
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 023cd42ad5fb321e7ffa65f08673cb4145f49af4
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817904"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>作法：指定系結的方向

本範例顯示如何指定繫結只更新繫結目標 (目標) 屬性、繫結來源 (來源) 屬性，或同時更新目標屬性與來源屬性。  
  
## <a name="example"></a>範例  
 您可以使用<xref:System.Windows.Data.Binding.Mode%2A?displayProperty=nameWithType>屬性來指定系結的方向。 以下是可用來系結更新的選項:  
  
- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>每當目標屬性或來源屬性變更時, 就會更新目標屬性或屬性。  
  
- <xref:System.Windows.Data.BindingMode.OneWay?displayProperty=nameWithType>只有當 source 屬性變更時, 才會更新目標屬性。  
  
- <xref:System.Windows.Data.BindingMode.OneTime?displayProperty=nameWithType>只有在應用程式啟動或進行變更時<xref:System.Windows.FrameworkElement.DataContext%2A> , 才會更新目標屬性。  
  
- <xref:System.Windows.Data.BindingMode.OneWayToSource?displayProperty=nameWithType>當目標屬性變更時, 更新 source 屬性。  
  
- <xref:System.Windows.Data.BindingMode.Default?displayProperty=nameWithType>會使用目標<xref:System.Windows.Data.Binding.Mode%2A>屬性的預設值。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Data.BindingMode> 列舉。  
  
 下列範例會示範如何設定 <xref:System.Windows.Data.Binding.Mode%2A> 屬性。  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 若要偵測來源變更 (適用<xref:System.Windows.Data.BindingMode.OneWay>于<xref:System.Windows.Data.BindingMode.TwoWay>和系結), 來源必須執行適當的屬性<xref:System.ComponentModel.INotifyPropertyChanged>變更通知機制, 例如。 如需<xref:System.ComponentModel.INotifyPropertyChanged>執行的範例, 請參閱[執行屬性變更通知](how-to-implement-property-change-notification.md)。  
  
 針對<xref:System.Windows.Data.BindingMode.TwoWay> <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>或<xref:System.Windows.Data.BindingMode.OneWayToSource>系結, 您可以藉由設定屬性來控制來源更新的時間。 如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.Binding>
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
