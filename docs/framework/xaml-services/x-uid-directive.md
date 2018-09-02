---
title: x:Uid 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 7075f8258e617d2d13d4585fdd5fb7aefaa50664
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452621"
---
# <a name="xuid-directive"></a>x:Uid 指示詞
提供標記項目的唯一識別碼。 在許多情況下，這個唯一識別碼使用 XAML 的當地語系化程序和工具。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`identifier`|手動建立或自動產生的字串應該是唯一的檔案中時則會解譯由`x:Uid`取用者。|  
  
## <a name="remarks"></a>備註  
 在 [MS-XAML]`x:Uid`定義為指示詞。 如需詳細資訊，請參閱 < [ \[MS XAML\]一節 5.3.6](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
 `x:Uid` 是從離散`x:Name`同時因為指定的 XAML 當地語系化案例使用於當地語系化的識別項的程式設計模型含意上沒有任何相依性`x:Name`。 此外，`x:Name`受到的 XAML 名稱範圍; 不過，`x:Uid`不會受到唯一性強制執行的任何 XAML 定義的語言概念。 廣泛了 （不屬於當地語系化程序的處理器） 中的 XAML 處理器不會強制執行唯一性`x:Uid`值。 該責任在概念上是在值的建立者。 唯一性的期望值`x:Uid`單一 XAML 來源內的值是相當合理的值，例如專用的全球化處理流程或工具的取用者。 典型的唯一性的模型是`x:Uid`值是唯一的 XML 編碼表示 XAML 檔案中。  
  
 有了特定的 XAML 結構描述的工具可以選擇將套用`x:Uid`僅適用於為 true，則可當地語系化的字串，而不是文字字串值，在標記中遇到的所有案例。  
  
 架構可以為的別名，其物件模型中指定特定的屬性`x:Uid`藉由將屬性套用<xref:System.Windows.Markup.UidPropertyAttribute>成定義的型別。 如果一種架構指定特定的屬性，它無效，無法同時指定`x:Uid`和別名化成員相同的物件。 如果兩個`x:Uid`並指定別名化成員，.NET Framework XAML 服務 API 通常會擲回<xref:System.Xaml.XamlDuplicateMemberException>在此情況下。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 如需有關所扮演的角色`x:Uid`在 WPF 當地語系化程序和 BAML 形式的 XAML，請參閱[WPF 的全球化](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)或 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
 <xref:Microsoft.Build.Tasks.Windows.UidManager>  
 [WPF 的全球化](../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
