---
title: HOW TO：指定繫結的方向
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 265271cee16d203d7652281c5416b93759e66d4b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378212"
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>HOW TO：指定繫結的方向
本範例顯示如何指定繫結只更新繫結目標 (目標) 屬性、繫結來源 (來源) 屬性，或同時更新目標屬性與來源屬性。  
  
## <a name="example"></a>範例  
 您使用<xref:System.Windows.Data.Binding.Mode%2A>屬性來指定繫結的方向。 下列列舉清單顯示繫結更新的可用選項：  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> 目標屬性或 [來源] 屬性變更時，請更新目標屬性。  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> [來源] 屬性變更時才會更新目標屬性。  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> 更新目標屬性，只有在應用程式啟動時或<xref:System.Windows.FrameworkElement.DataContext%2A>; 歷經變更。  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> 當目標屬性變更時，請更新來源屬性。  
  
-   <xref:System.Windows.Data.BindingMode.Default> 讓預設<xref:System.Windows.Data.Binding.Mode%2A>要使用的目標屬性的值。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Data.BindingMode> 列舉。  
  
 下列範例會示範如何設定 <xref:System.Windows.Data.Binding.Mode%2A> 屬性。  
  
 [!code-xaml[DirectionalBinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 若要偵測來源變更 (適用於<xref:System.Windows.Data.BindingMode.OneWay>並<xref:System.Windows.Data.BindingMode.TwoWay>繫結)，來源必須實作適合的屬性變更通知機制，例如<xref:System.ComponentModel.INotifyPropertyChanged>。 請參閱[實作屬性變更通知](how-to-implement-property-change-notification.md)如需範例的<xref:System.ComponentModel.INotifyPropertyChanged>實作。  
  
 針對<xref:System.Windows.Data.BindingMode.TwoWay>或是<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結，您可以設定來控制來源更新的時機<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性。 如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Data.Binding>
- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
