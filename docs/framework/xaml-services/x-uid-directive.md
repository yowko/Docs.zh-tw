---
title: "x:Uid 指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: "12"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9abd4a1851ce21a1858f51ff4ce42998c20639e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xuid-directive"></a>x:Uid 指示詞
提供唯一的識別項的標記項目。 在許多案例中，這個唯一識別碼使用 XAML 當地語系化程序和工具。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`identifier`|手動建立或自動產生字串應該是唯一的檔案中時，它會經過解譯`x:Uid`取用者。|  
  
## <a name="remarks"></a>備註  
 在 [MS-XAML]，`x:Uid`定義為指示詞。 如需詳細資訊，請參閱[ \[MS-XAML\]區段 5.3.6](http://go.microsoft.com/fwlink/?LinkId=114525)。  
  
 `x:Uid`是從離散`x:Name`同時由於所述的 XAML 當地語系化案例，以及可用來當地語系化的識別項的程式設計模型影響上沒有任何相依性`x:Name`。 此外，`x:Name`由 XAML 名稱範圍; 不過，`x:Uid`不由任何 XAML 語言定義的概念唯一性的強制執行。 XAML 處理器的廣泛的意義上 （不屬於當地語系化程序的處理器） 不應該用來強制執行唯一性的`x:Uid`值。 該項責任的概念上的建立者的值。 期望的唯一性的`x:Uid`單一 XAML 來源內的值是合理的值，例如專用的全球化程序或工具的取用者。 典型的唯一性的模型是`x:Uid`值內是唯一代表 XAML XML 編碼的檔案。  
  
 具有特定的 XAML 結構描述相當了解工具可以選擇將套用`x:Uid`僅適用於在標記中的文字字串值會遇到的情況下，而不是 true 可當地語系化的字串。  
  
 架構可以指定特定的屬性，其為別名的物件模型中`x:Uid`藉由套用屬性<xref:System.Windows.Markup.UidPropertyAttribute>定義的型別。 如果架構指定特定的屬性，不能同時指定`x:Uid`和別名成員相同的物件。 如果兩個`x:Uid`和指定的別名成員、.NET Framework XAML 服務 API 通常會擲回<xref:System.Xaml.XamlDuplicateMemberException>這個情況。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 如需有關角色`x:Uid`WPF 當地語系化程序在和 BAML 形式的 XAML，請參閱[WPF 的全球化](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)或<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [WPF 的全球化](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
