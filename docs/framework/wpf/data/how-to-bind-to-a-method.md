---
title: 操作說明：繫結至方法
description: 請遵循此範例來瞭解如何在 Windows Presentation Foundation （WPF）中系結至物件的方法。
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619594"
---
# <a name="how-to-bind-to-a-method"></a>操作說明：繫結至方法
下列範例顯示如何使用系結至方法 <xref:System.Windows.Data.ObjectDataProvider> 。  
  
## <a name="example"></a>範例  
 在此範例中，`TemperatureScale` 是一個包含方法 `ConvertTemp` 的類別，它接受兩個參數 (一個是 `double` 類型，一個是 `enum` 類型 `TempType)`，並將指定的值從一個溫度單位轉換為另一個溫度單位。 在下列範例中， <xref:System.Windows.Data.ObjectDataProvider> 會使用來具現化 `TemperatureScale` 物件。 `ConvertTemp` 方法是使用兩個指定的參數呼叫。  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 現在，方法已經成為資源，就可以繫結至其結果。 在下列範例中，的 <xref:System.Windows.Controls.TextBox.Text%2A> 和的屬性 <xref:System.Windows.Controls.TextBox> 會系結 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> 至方法的兩個參數。 這可讓使用者指定要轉換的溫度及轉換前的溫度單位。 請注意， <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> 設定為， `true` 因為我們系結至 <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> 實例的屬性 <xref:System.Windows.Data.ObjectDataProvider> ，而不是 <xref:System.Windows.Data.ObjectDataProvider> （物件）所包裝之物件的屬性 `TemperatureScale` 。  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Label> 當使用者修改的內容 <xref:System.Windows.Controls.TextBox> 或的選取專案時，最後一次更新的 <xref:System.Windows.Controls.ComboBox> 。  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 轉換器 `DoubleToString` 會採用雙精度浮點數，並將其轉換成 <xref:System.Windows.Data.IValueConverter.Convert%2A> 方向的字串（從系結來源到系結目標，也就是 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性），並將轉換成 `string` 方向的 `double` <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 。  
  
 `InvalidationCharacterRule`是 <xref:System.Windows.Controls.ValidationRule> ，它會檢查是否有不正確字元。 預設錯誤範本是周圍的紅色框線 <xref:System.Windows.Controls.TextBox> ，當輸入值不是雙精度值時，就會通知使用者。  
  
## <a name="see-also"></a>另請參閱

- [操作說明主題](data-binding-how-to-topics.md)
- [系結至列舉](how-to-bind-to-an-enumeration.md)
