---
title: "當地語系化屬性和註解 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "當地語系化, 屬性"
  - "當地語系化, 註解"
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 當地語系化屬性和註解
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 當地語系化註解是 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 原始程式碼內的屬性 \(Property\)，由開發人員提供做為當地語系化的規則及提示之用。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 當地語系化註解包含兩組資訊：可當地語系化屬性 \(Attribute\) 和自由格式的當地語系化註解。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 當地語系化 API 會使用可當地語系化屬性 \(Attribute\) 指出要當地語系化的資源。  自由格式註解則可以是應用程式作者想要包含的任何資訊。  
  
   
  
<a name="Localizer_Comments_"></a>   
## 當地語系化註解  
 如果標記 \(Markup\) 應用程式作者對 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 中的特定項目有特殊需求，例如文字長度、字型系列或字型大小等限制，他們可以在 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 程式碼中使用註解將這些資訊傳達給當地語系化人員。  將註解加入至原始程式碼的程序如下：  
  
1.  應用程式開發人員將當地語系化元件加入至 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 原始程式碼。  
  
2.  在建置程序期間，您可以在 .proj 檔案中指定是要保留組件中的自由格式當地語系化註解、拿掉部分註解，還是拿掉所有註解。  拿掉的註解會放置於個別的檔案中。  您可以使用 `LocalizationDirectivesToLocFile` 標記 \(Tag\) 指定您的選擇，例如：  
  
     `<LocalizationDirectivesToLocFile>` *value* `</LocalizationDirectivesToLocFile>`  
  
3.  可以指派的值有：  
  
    -   **None** \- 保留組件內的註解和屬性 \(Attribute\)，而且不會產生個別檔案。  
  
    -   **CommentsOnly** \- 只從組件拿掉註解並將其放置在個別的 LocFile 中。  
  
    -   **All** \- 從組件拿掉註解和屬性 \(Attribute\)，並且將這兩者放置在個別的 LocFile 中。  
  
4.  從 [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] 擷取可當地語系化的資源時，[!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)] 當地語系化 API 會遵守可當地語系化屬性 \(Attribute\)。  
  
5.  只包含自由格式註解的當地語系化註解檔稍後會併入至當地語系化程序。  
  
 下列範例會顯示如何將當地語系化註解加入至 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 檔案中。  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 在上一個範例中，Localization.Attributes 區段包含當地語系化屬性 \(Attribute\)，而 Localization.Comments 區段則包含自由格式註解。  下表會顯示屬性 \(Attribute\) 和註解及其對於當地語系化人員的意義。  
  
|當地語系化屬性|意義|  
|-------------|--------|  
|$Content \(Unmodifiable Readable Text\)|TextBlock 項目的內容無法修改。  當地語系化人員不能變更 "Microsoft" 這個字。  當地語系化人員可以看見 \(Readable\) 內容。  內容的分類是文字。|  
|FontFamily \(Unmodifiable Readable\)|TextBlock 項目的字型系列屬性 \(Property\) 無法修改，但是當地語系化人員看得見。|  
  
|當地語系化自由格式註解|意義|  
|-----------------|--------|  
|$Content \(Trademark\)|應用程式作者告訴當地語系化人員 TextBlock 項目的內容是商標。|  
|FontSize \(Trademark font size\)|應用程式作者指出字型大小屬性 \(Property\) 應遵循標準商標大小。|  
  
### 可當地語系化屬性  
 Localization.Attributes 中的資訊包含下列配對的清單：目標值名稱和關聯的可當地語系化值。  目標名稱可以是屬性 \(Property\) 名稱或特殊的 $Content 名稱。  如果是屬性 \(Property\) 名稱，則目標值就是屬性 \(Property\) 的值。  如果是 $Content，目標值就是項目的內容。  
  
 屬性 \(Attribute\) 可分三種類型：  
  
-   **Category**：  指定是否可以使用當地語系化工具修改值。  請參閱 <xref:System.Windows.LocalizabilityAttribute.Category%2A>。  
  
-   **Readability**：  指定當地語系化工具是否應該讀取 \(及顯示\) 值。  請參閱 <xref:System.Windows.LocalizabilityAttribute.Readability%2A>。  
  
-   **Modifiability**：  指定當地語系化工具是否允許修改值。  請參閱 <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>。  
  
 這些屬性 \(Attribute\) 可以依任意順序指定，以空格隔開。  如果指定重複的屬性，後面的屬性 \(Attribute\) 會覆寫前一個屬性 \(Attribute\)。  例如，Localization.Attributes \= "Unmodifiable Modifiable" 會將 Modifiability 設為 Modifiable，因為它是最後一個值。  
  
 Modifiability 和 Readability 是給機器看的。  Category 屬性 \(Attribute\) 則提供預先定義的分類來協助當地語系化人員翻譯文字。  例如 Text、Label 及 Title 分類讓當地語系化人員知道該如何翻譯文字。  還有其他特殊的分類：None、Inherit、Ignore 和 NeverLocalize。  
  
 下表顯示這些特殊分類的意義。  
  
|分類|意義|  
|--------|--------|  
|None|目標值沒有定義的分類。|  
|Inherit|目標值要從其父代 \(Parent\) 繼承分類。|  
|Ignore|在當地語系化程序中忽略目標值。  Ignore 只會影響目前的值，  不會影響子節點。|  
|NeverLocalize|目前值無法當地語系化。  這個分類會由項目的子系繼承。|  
  
<a name="Localization_Comments"></a>   
## 當地語系化註解  
 Localization.Comments 含有關於目標值的自由格式字串。  應用程式開發人員可以加入資訊以提示當地語系化人員該如何翻譯應用程式文字。  註解的格式可以是以 "\(\)" 括住的任意字串。  逸出字元是 '\\'。  
  
## 請參閱  
 [WPF 的全球化](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)   
 [使用自動配置建立按鈕](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)   
 [針對自動配置使用格線](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)   
 [將應用程式當地語系化](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)