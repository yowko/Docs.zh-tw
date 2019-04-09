---
title: HOW TO：繫結至方法
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 6cdad46fd6d9ef3bc4ce1a13fedb6ff1d639d93e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123236"
---
# <a name="how-to-bind-to-a-method"></a>HOW TO：繫結至方法
下列範例示範如何將繫結至方法，使用<xref:System.Windows.Data.ObjectDataProvider>。  
  
## <a name="example"></a>範例  
 在此範例中，`TemperatureScale` 是一個包含方法 `ConvertTemp` 的類別，它接受兩個參數 (一個是 `double` 類型，一個是 `enum` 類型 `TempType)`，並將指定的值從一個溫度單位轉換為另一個溫度單位。 在下列範例中，<xref:System.Windows.Data.ObjectDataProvider>用以具現化`TemperatureScale`物件。 `ConvertTemp` 方法是使用兩個指定的參數呼叫。  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 現在，方法已經成為資源，就可以繫結至其結果。 在下列範例中，<xref:System.Windows.Controls.TextBox.Text%2A>的屬性<xref:System.Windows.Controls.TextBox>並<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>的<xref:System.Windows.Controls.ComboBox>繫結至方法的兩個參數。 這可讓使用者指定要轉換的溫度及轉換前的溫度單位。 請注意，<xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>設定為`true`因為我們要繫結<xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A>屬性<xref:System.Windows.Data.ObjectDataProvider>執行個體而不是屬性的物件所包裝<xref:System.Windows.Data.ObjectDataProvider>(`TemperatureScale`物件)。  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>的最後<xref:System.Windows.Controls.Label>當使用者修改的內容時，更新<xref:System.Windows.Controls.TextBox>或選取<xref:System.Windows.Controls.ComboBox>。  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 轉換器`DoubleToString`會採用雙精度浮點數，並將它轉換成的字串<xref:System.Windows.Data.IValueConverter.Convert%2A>方向 (繫結來源中要繫結目標，即<xref:System.Windows.Controls.TextBox.Text%2A>屬性)，並將轉換`string`來`double`在<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方向。  
  
 `InvalidationCharacterRule`是<xref:System.Windows.Controls.ValidationRule>，以檢查無效的字元。 預設錯誤樣板，也就是紅色框線四周<xref:System.Windows.Controls.TextBox>，會出現時輸入的值不是雙精度浮點數值，通知使用者。  
  
## <a name="see-also"></a>另請參閱

- [HOW TO 主題](data-binding-how-to-topics.md)
- [繫結至列舉](how-to-bind-to-an-enumeration.md)
