---
title: 當地語系化屬性和註解
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 7cfcc9fa4dc3bc1450febb39500b7d96f92beac6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547263"
---
# <a name="localization-attributes-and-comments"></a>當地語系化屬性和註解
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 當地語系化註解是 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 原始程式碼內的屬性，並由開發人員提供以提供當地語系化的規則和提示。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 當地語系化註解包含兩組資訊︰可當地語系化屬性和自由格式當地語系化註解。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 當地語系化 API 使用可當地語系化屬性來指出要當地語系化的資源。 自由格式註解是應用程式作者想要包含的任何資訊。  
  

  
<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>當地語系化註解  
 如果標記應用程式作者具有 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 中特定項目的需求 (例如，文字長度、字型家族或字型大小的條件約束)，則可以透過 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 程式碼中的註解將這項資訊傳達給當地語系化人員。 將註解新增至原始程式碼的程序如下︰  
  
1.  應用程式開發人員會將當地語系化註解新增至 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 原始程式碼。  
  
2.  在建置過程，您可以於 .proj 檔案中指定是否要保留組件中的自由格式當地語系化註解、去除註解的一部分，或去除所有註解。 去除的註解會放在不同的檔案中。 您可以使用 `LocalizationDirectivesToLocFile` 標記來指定選項，例如︰  
  
     `<LocalizationDirectivesToLocFile>` <值> `</LocalizationDirectivesToLocFile>`  
  
3.  可以指派的值如下︰  
  
    -   **None** - 註解和屬性會保留在組件內，而且不會產生個別檔案。  
  
    -   **CommentsOnly** - 只去除組件中的註解，並將它們放在個別 LocFile 中。  
  
    -   **All** - 去除組件中的註解和屬性，並將它們放在個別 LocFile 中。  
  
4.  從 [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] 擷取可當地語系化的資源時，[!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] 當地語系化 API 會接受可當地語系化屬性。  
  
5.  稍後，只包含自由格式註解的當地語系化註解檔案會併入當地語系化程序。  
  
 下列範例示範如何將當地語系化註解新增至 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 檔案。  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 在先前的範例中，Localization.Attributes 區段包含當地語系化屬性，而 Localization.Comments 區段包含自由格式註解。 下列各表顯示屬性和註解和其對當地語系化人員的意義。  
  
|當地語系化屬性|意義|  
|-----------------------------|-------------|  
|$Content (無法修改的可讀取文字)|無法修改 TextBlock 項目的內容。 當地語系化人員無法變更 "Microsoft" 這個字。 當地語系化人員可以看到內容 (可讀取)。 內容的分類為文字。|  
|FontFamily (無法修改的可讀取)|無法變更 TextBlock 項目的字型家族屬性，但當地語系化人員可以看到它。|  
  
|當地語系化自由格式註解|意義|  
|--------------------------------------|-------------|  
|$Content (商標)|應用程式作者會告知當地語系化人員：TextBlock 項目中的內容是商標。|  
|FontSize (商標字型大小)|應用程式作者指出字型大小屬性應該遵循標準商標大小。|  
  
### <a name="localizability-attributes"></a>可當地語系化屬性  
 Localization.Attributes 中的資訊包含配對的清單︰目標值名稱和相關聯的可當地語系化值。 目標名稱可以是屬性名稱或特殊 $Content 名稱。 如果這是屬性名稱，則目標值是屬性的值。 如果是 $Content，則目標值是項目的內容。  
  
 屬性有三種類型：  
  
-   **分類**. 這指定是否應該可以從當地語系化人員工具修改值。 請參閱 <xref:System.Windows.LocalizabilityAttribute.Category%2A>。  
  
-   **可讀性**. 這指定當地語系化人員工具是否應該讀取 (和顯示) 值。 請參閱 <xref:System.Windows.LocalizabilityAttribute.Readability%2A>。  
  
-   **可修改性**. 這指定當地語系化人員工具是否允許修改值。 請參閱 <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>。  
  
 這些屬性可以依任何順序指定，並以空格分隔。 如果指定重複屬性，則最後一個屬性會覆寫先前的屬性。 例如，Localization.Attributes = "Unmodifiable Modifiable" 會將「可修改性」設定為「可修改」，因為它是最後一個值。  
  
 可修改性和可讀性一看就懂。 分類屬性提供預先定義的分類，以在翻譯文字時協助當地語系化人員。 文字、標籤和標題這類分類會將如何翻譯文字的資訊提供給當地語系化人員。 也會有特殊分類︰無、繼承、略過和 NeverLocalize。  
  
 下表顯示特殊分類的意義。  
  
|分類|意義|  
|--------------|-------------|  
|無|目標值沒有已定義的分類。|  
|繼承|目標值會從其父代繼承其分類。|  
|Ignore|會略過當地語系化程序中的目標值。 略過只會影響目前值。 它不會影響子節點。|  
|NeverLocalize|無法當地語系化目前值。 項目的子系會繼承此分類。|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>當地語系化註解  
 Localization.Comments 包含有關目標值的自由格式字串。 應用程式開發人員可以新增資訊，提供當地語系化人員如何翻譯應用程式文字的提示。 註解的格式可以是用 "()" 括住的任何字串。 使用 '\\' 來逸出字元。  
  
## <a name="see-also"></a>另請參閱  
 [WPF 的全球化](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [使用自動版面配置建立按鈕](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [針對自動版面配置使用方格](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)  
 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)
