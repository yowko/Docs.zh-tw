---
title: 屬性值繼承
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: eb757d039437d9954a2b648c5f758dffa3fee3d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958367"
---
# <a name="property-value-inheritance"></a>屬性值繼承
屬性值繼承是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統的功能。 屬性值繼承可讓元素樹狀結構中的子元素，在將它設定於最接近之父元素中的任一處時，可從父元素中取得特殊屬性的值，並繼承該值。 父元素可能也會透過屬性值繼承來取得它的值，因此，系統有可能會不停地遞迴到頁面根元素。 屬性值繼承不是預設的屬性系統行為；屬性必須使用特殊的中繼資料值來建立，才能讓該屬性起始子元素上的屬性值繼承。  

<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>屬性值繼承是內含項目繼承  
 「繼承」在此處做為一個詞彙，它不完全等同於類型內容中的繼承概念，且為一般物件導向程式設計，其中衍生的類別會繼承來自其基底類別的成員定義。 該繼承的意義也適用於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]︰定義於各種基底類別中的屬性 (Property) 均會在衍生的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 類別用來做為元素時，公開為其屬性 (Attribute)，並公開為程式碼的成員。 屬性值繼承特別是關於屬性值如何根據元素樹狀結構內的父/子關聯性，從某一個元素繼承至另一個元素。 當您在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 標記中定義應用程式，於其他元素內巢串元素時，幾乎可以直接看見該元素樹狀結構。 物件的樹狀結構也可以透過程式設計方式，將物件新增至其他物件的指定集合來建立，而屬性值繼承會在執行階段，於完成的樹狀結構中以相同方式來運作。  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>屬性值繼承的實際應用程式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Api 包含數個已啟用屬性繼承的屬性。 一般而言，適用於這些屬性的案例是它們所包含的屬性適合在每個頁面上只設定該屬性一次，但該屬性也是其中一個基底元素類別的成員，因此，也會存在於大多數的子元素中。 例如, <xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性會控制要在頁面上呈現和排列之內容的方向。 一般而言，您會想要以一致性方式在所有子元素中處理文字流動的概念。 如果使用者或環境動作基於某些因素而在元素樹狀結構的某些層級中重設流動方向，則通常應該全部重設。 當屬性<xref:System.Windows.FrameworkElement.FlowDirection%2A>設為 [繼承] 時, 只需要在專案樹狀結構中的層級設定或重設此值一次, 以包含應用程式中每個頁面的呈現需求。 甚至連初始的預設值也將以這種方式繼承。 屬性值繼承模型仍可讓個別的元素在故意混合流動方向的罕見情況下重設值。  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>讓自訂屬性成為可繼承  
 藉由變更自訂屬性的中繼資料，您也可以讓自己的自訂屬性成為可繼承。 但請注意，將屬性指定為可繼承有一些效能考量。 假如該屬性沒有已建立的本機值，或是透過樣式、範本或資料繫結取得的值，可繼承的屬性就會為邏輯樹狀結構中的所有子元素提供其指派的屬性值。  
  
 若要讓參與值的屬性成為可繼承，請建立自訂的附加屬性，如[註冊附加屬性](how-to-register-an-attached-property.md)中所述。 使用中繼資料 (<xref:System.Windows.FrameworkPropertyMetadata>) 註冊屬性, 並在該中繼資料內的 [選項] 設定中指定 [繼承] 選項。 也請確定屬性具有已建立的預設值，因為該值現在將會繼承。 儘管您已將屬性註冊為附加，但您可能也想要針對擁有者類型上的 get/set 存取建立屬性「包裝函式」，就像您針對「非附加的」相依性屬性所做的一樣。 這麼做之後, 就可以使用擁有者類型或衍生類型上的 direct 屬性包裝函式來設定可繼承的屬性, 也可以在任何<xref:System.Windows.DependencyObject>上使用附加的屬性語法來設定它。  
  
 附加屬性在概念上類似于全域屬性;您可以檢查是否有任何<xref:System.Windows.DependencyObject>值, 並取得有效的結果。 附加屬性的一般案例是在子專案上設定屬性值, 而且如果問題中的屬性是附加屬性, 而且一律會隱含呈現為每個<xref:System.Windows.DependencyObject>專案上的附加屬性,則此案例更有效率。) 在樹狀結構中。  
  
> [!NOTE]
> 雖然屬性值繼承似乎適用於非附加的相依性屬性，但在執行階段的樹狀結構中，透過特定元素界限的非附加屬性繼承行為是未定義的。 請一律<xref:System.Windows.DependencyProperty.RegisterAttached%2A>使用來註冊您在元<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>資料中指定的屬性。  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>跨樹狀結構界限繼承屬性值  
 屬性繼承的運作方式是周遊元素的樹狀結構。 此樹狀結構通常會與邏輯樹狀結構平行。 不過, 每當您在定義專案樹狀結構的標記中包含 WPF 核心層級物件 (例如<xref:System.Windows.Media.Brush>) 時, 就表示您已建立不連續的邏輯樹狀結構。 True 邏輯樹狀結構在概念上不會透過<xref:System.Windows.Media.Brush>進行擴充, 因為邏輯樹狀結構是 WPF 架構層級的概念。 使用的方法<xref:System.Windows.LogicalTreeHelper>時, 您可以在結果中看到這會反映出來。 不過, 屬性值繼承可以在邏輯樹狀結構中橋接此間隙, 而且仍然可以透過來傳遞繼承的值, 只要可繼承的屬性已註冊為附加屬性, 而且沒有刻意的繼承封鎖界限 (例如<xref:System.Windows.Controls.Frame>)。  
  
## <a name="see-also"></a>另請參閱

- [相依性屬性中繼資料](dependency-property-metadata.md)
- [附加屬性概觀](attached-properties-overview.md)
- [相依性屬性值優先順序](dependency-property-value-precedence.md)
