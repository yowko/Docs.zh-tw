---
title: 操作說明：指定繫結的方向
ms.date: 03/30/2017
helpviewer_keywords:
- direction of binding [WPF]
- binding direction [WPF]
- data binding [WPF], direction of binding
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
ms.openlocfilehash: 100130f3dc099d1cf1f216c841e7e1dc1d083f39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-direction-of-the-binding"></a>操作說明：指定繫結的方向
本範例顯示如何指定繫結只更新繫結目標 (目標) 屬性、繫結來源 (來源) 屬性，或同時更新目標屬性與來源屬性。  
  
## <a name="example"></a>範例  
 您使用<xref:System.Windows.Data.Binding.Mode%2A>屬性來指定繫結的方向。 下列列舉清單顯示繫結更新的可用選項：  
  
-   <xref:System.Windows.Data.BindingMode.TwoWay> 更新目標屬性，只要將目標屬性或 [來源] 屬性變更。  
  
-   <xref:System.Windows.Data.BindingMode.OneWay> [來源] 屬性變更時才會更新目標屬性。  
  
-   <xref:System.Windows.Data.BindingMode.OneTime> 只有在應用程式啟動或時，更新目標屬性<xref:System.Windows.FrameworkElement.DataContext%2A>進行的變更。  
  
-   <xref:System.Windows.Data.BindingMode.OneWayToSource> [來源] 屬性變更時，更新的目標屬性。  
  
-   <xref:System.Windows.Data.BindingMode.Default> 讓預設<xref:System.Windows.Data.Binding.Mode%2A>要使用的目標屬性的值。  
  
 如需詳細資訊，請參閱 <xref:System.Windows.Data.BindingMode> 列舉。  
  
 下列範例會示範如何設定 <xref:System.Windows.Data.Binding.Mode%2A> 屬性。  
  
 [!code-xaml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 若要偵測來源的變更 (適用於<xref:System.Windows.Data.BindingMode.OneWay>和<xref:System.Windows.Data.BindingMode.TwoWay>繫結)，來源必須實作適當的屬性變更通知機制這類<xref:System.ComponentModel.INotifyPropertyChanged>。 請參閱[實作屬性變更告知](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)的範例，<xref:System.ComponentModel.INotifyPropertyChanged>實作。  
  
 如<xref:System.Windows.Data.BindingMode.TwoWay>或<xref:System.Windows.Data.BindingMode.OneWayToSource>繫結，您可以設定來控制來源更新的時機<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>屬性。 如需詳細資訊，請參閱 <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Data.Binding>  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
