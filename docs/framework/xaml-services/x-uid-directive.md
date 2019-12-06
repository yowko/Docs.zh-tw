---
title: x:Uid 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 32cfd9ab0cf6037c731b619e81a7504ac92d5fb9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837177"
---
# <a name="xuid-directive"></a>x:Uid 指示詞
提供標記元素的唯一識別碼。 在許多情況下，XAML 當地語系化進程和工具會使用這個唯一識別碼。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`identifier`|手動建立或自動產生的字串，在由 `x:Uid` 取用者解讀時，它在檔案中應該是唯一的。|  
  
## <a name="remarks"></a>備註  
 在 [MS-XAML] 中，`x:Uid` 會定義為指示詞。 如需詳細資訊，請參閱[\[MS-XAML\] 區段 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。  
  
 `x:Uid` 與 `x:Name` 的不同之處在于，這兩者都是因為所述的 XAML 當地語系化案例，因此用於當地語系化的識別碼與 `x:Name`的程式設計模型含意沒有相依性。 此外，`x:Name` 是由 XAML 名稱範圍所控制;不過，`x:Uid` 不受任何 XAML 語言定義的唯一性強制概念所規範。 XAML 處理器的廣泛意義（不屬於當地語系化進程的處理器）不應該強制執行 `x:Uid` 值的唯一性。 這項責任在概念上是在值的建立者上。 在單一 XAML 來源中，`x:Uid` 值的唯一性，對於值的取用者而言是合理的，例如專用的全球化處理常式或工具。 一般的唯一性模型是，在代表 XAML 的 XML 編碼檔案中，`x:Uid` 值是唯一的。  
  
 對於特定 XAML 架構具有重要知識的工具，可以選擇僅針對真正可當地語系化的字串套用 `x:Uid`，而不是針對在標記中遇到文字字串值的所有情況。  
  
 架構可以將屬性 <xref:System.Windows.Markup.UidPropertyAttribute> 套用至定義類型，藉此指定物件模型中的特定屬性，使其成為 `x:Uid` 的別名。 如果架構指定特定屬性，則在相同物件上同時指定 `x:Uid` 和別名成員是不正確。 如果同時指定 `x:Uid` 和別名成員，則 .NET Framework XAML 服務 API 通常會在此情況下擲回 <xref:System.Xaml.XamlDuplicateMemberException>。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 如需 WPF 當地語系化程式中的 `x:Uid` 角色和 BAML 形式 XAML 的詳細資訊，請參閱 WPF 或 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> 的[全球化](../wpf/advanced/globalization-for-wpf.md)  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF 的全球化](../wpf/advanced/globalization-for-wpf.md)
