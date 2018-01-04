---
title: "屬性值繼承"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eac3e03cfc0ca8bbb6f61f1bc6663c67fd6303f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="property-value-inheritance"></a>屬性值繼承
屬性值繼承是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統的功能。 屬性值繼承可讓元素樹狀結構中的子元素，在將它設定於最接近之父元素中的任一處時，可從父元素中取得特殊屬性的值，並繼承該值。 父元素可能也會透過屬性值繼承來取得它的值，因此，系統有可能會不停地遞迴到頁面根元素。 屬性值繼承不是預設的屬性系統行為；屬性必須使用特殊的中繼資料值來建立，才能讓該屬性起始子元素上的屬性值繼承。  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>屬性值繼承是內含項目繼承  
 「繼承」在此處做為一個詞彙，它不完全等同於類型內容中的繼承概念，且為一般物件導向程式設計，其中衍生的類別會繼承來自其基底類別的成員定義。 該繼承的意義也適用於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]︰定義於各種基底類別中的屬性 (Property) 均會在衍生的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 類別用來做為元素時，公開為其屬性 (Attribute)，並公開為程式碼的成員。 屬性值繼承特別是關於屬性值如何根據元素樹狀結構內的父/子關聯性，從某一個元素繼承至另一個元素。 當您在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中定義應用程式，於其他元素內巢串元素時，幾乎可以直接看見該元素樹狀結構。 物件的樹狀結構也可以透過程式設計方式，將物件新增至其他物件的指定集合來建立，而屬性值繼承會在執行階段，於完成的樹狀結構中以相同方式來運作。  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>屬性值繼承的實際應用程式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] 包含數個已啟用屬性繼承的屬性。 一般而言，適用於這些屬性的案例是它們所包含的屬性適合在每個頁面上只設定該屬性一次，但該屬性也是其中一個基底元素類別的成員，因此，也會存在於大多數的子元素中。 例如，<xref:System.Windows.FrameworkElement.FlowDirection%2A>方向流動內容屬性會控制應呈現，並在頁面上排列。 一般而言，您會想要以一致性方式在所有子元素中處理文字流動的概念。 如果使用者或環境動作基於某些因素而在元素樹狀結構的某些層級中重設流動方向，則通常應該全部重設。 當<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性繼承，此值需要只設定或重設一次層級包含簡報所需的應用程式中的每一頁的項目樹狀目錄中。 甚至連初始的預設值也將以這種方式繼承。 屬性值繼承模型仍可讓個別的元素在故意混合流動方向的罕見情況下重設值。  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>讓自訂屬性成為可繼承  
 藉由變更自訂屬性的中繼資料，您也可以讓自己的自訂屬性成為可繼承。 但請注意，將屬性指定為可繼承有一些效能考量。 假如該屬性沒有已建立的本機值，或是透過樣式、範本或資料繫結取得的值，可繼承的屬性就會為邏輯樹狀結構中的所有子元素提供其指派的屬性值。  
  
 若要讓參與值的屬性成為可繼承，請建立自訂的附加屬性，如[註冊附加屬性](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)中所述。 註冊此屬性與中繼資料 (<xref:System.Windows.FrameworkPropertyMetadata>)，並指定該中繼資料內的 [選項] 設定中的"Inherits"選項。 也請確定屬性具有已建立的預設值，因為該值現在將會繼承。 儘管您已將屬性註冊為附加，但您可能也想要針對擁有者類型上的 get/set 存取建立屬性「包裝函式」，就像您針對「非附加的」相依性屬性所做的一樣。 之後，請可繼承的屬性可以設定使用 direct 內容包裝函式上的擁有者型別或衍生型別，或它可以設定任何使用附加的屬性語法<xref:System.Windows.DependencyObject>。  
  
 附加的屬性在概念上類似全域屬性。您可以檢查任何值<xref:System.Windows.DependencyObject>並取得有效的結果。 附加屬性的典型案例子項目上設定屬性值，而這種情況下所討論的屬性是附加的屬性是一律以隱含方式存為每個項目附加屬性的更有效率 (<xref:System.Windows.DependencyObject>) 樹狀目錄中。  
  
> [!NOTE]
>  雖然屬性值繼承似乎適用於非附加的相依性屬性，但在執行階段的樹狀結構中，透過特定元素界限的非附加屬性繼承行為是未定義的。 一律使用<xref:System.Windows.DependencyProperty.RegisterAttached%2A>註冊屬性，指定<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>中繼資料中。  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>跨樹狀結構界限繼承屬性值  
 屬性繼承的運作方式是周遊元素的樹狀結構。 此樹狀結構通常會與邏輯樹狀結構平行。 不過，每當您加入 WPF 核心層級物件定義的項目樹狀結構，例如在標記中<xref:System.Windows.Media.Brush>，您已建立不連續的邏輯樹狀結構。 True 的邏輯樹狀結構不會在概念上延伸透過<xref:System.Windows.Media.Brush>，因為邏輯樹狀結構是 WPF 架構層級的概念。 您可以查看這反映在結果中的方法時<xref:System.Windows.LogicalTreeHelper>。 不過，屬性值繼承可以差距邏輯樹狀結構中，而且只要可繼承的屬性已註冊為附加的屬性並沒有刻意繼承封鎖界限，則仍然可以傳遞，透過繼承的值 (例如<xref:System.Windows.Controls.Frame>) 為止。  
  
## <a name="see-also"></a>請參閱  
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [附加屬性概觀](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [相依性屬性值優先順序](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)
