---
title: "操作說明：繫結至方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c276e9da3eaaf786038a117532848364b03e9b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-method"></a>操作說明：繫結至方法
下列範例示範如何將繫結至方法，使用<xref:System.Windows.Data.ObjectDataProvider>。  
  
## <a name="example"></a>範例  
 在此範例中，`TemperatureScale` 是一個包含方法 `ConvertTemp` 的類別，它接受兩個參數 (一個是 `double` 類型，一個是 `enum` 類型 `TempType)`，並將指定的值從一個溫度單位轉換為另一個溫度單位。 在下列範例中，<xref:System.Windows.Data.ObjectDataProvider>用來具現化`TemperatureScale`物件。 `ConvertTemp` 方法是使用兩個指定的參數呼叫。  
  
 [!code-xaml[BindToMethod#WindowResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 現在，方法已經成為資源，就可以繫結至其結果。 在下列範例中，<xref:System.Windows.Controls.TextBox.Text%2A>屬性<xref:System.Windows.Controls.TextBox>和<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>的<xref:System.Windows.Controls.ComboBox>繫結至兩個方法的參數。 這可讓使用者指定要轉換的溫度及轉換前的溫度單位。 請注意，<xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>設`true`因為我們要繫結至<xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A>屬性<xref:System.Windows.Data.ObjectDataProvider>執行個體和不所包裝之物件的屬性<xref:System.Windows.Data.ObjectDataProvider>(`TemperatureScale`物件)。  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>的最後<xref:System.Windows.Controls.Label>時在使用者修改的內容更新<xref:System.Windows.Controls.TextBox>或選取範圍的<xref:System.Windows.Controls.ComboBox>。  
  
 [!code-xaml[BindToMethod#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 轉換器`DoubleToString`採用 double 值，並將它轉換成字串<xref:System.Windows.Data.IValueConverter.Convert%2A>方向 (從繫結來源至繫結的目標，這是<xref:System.Windows.Controls.TextBox.Text%2A>屬性)，並將轉換`string`至`double`中<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方向。  
  
 `InvalidationCharacterRule`是<xref:System.Windows.Controls.ValidationRule>，會檢查是否有無效的字元。 預設錯誤範本，也就是紅色框線周圍<xref:System.Windows.Controls.TextBox>，出現時輸入的值不是雙精度浮點數值通知使用者。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)  
 [繫結至列舉](../../../../docs/framework/wpf/data/how-to-bind-to-an-enumeration.md)
