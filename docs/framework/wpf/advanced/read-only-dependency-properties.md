---
title: 唯讀相依性屬性
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 9aeeab95342bce94c53e89229003f55009118f96
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379000"
---
# <a name="read-only-dependency-properties"></a>唯讀相依性屬性
本主題說明唯讀相依性屬性，包括現有的唯讀相依性屬性，以及用於建立自訂唯讀相依性屬性的案例和技術。  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已了解實作相依性屬性的基本案例，以及如何將中繼資料套用到自訂相依性屬性。 如需相關內容，請參閱[自訂相依性屬性](custom-dependency-properties.md)和[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>現有的唯讀相依性屬性  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中定義的一些相依性屬性為唯讀狀態。 指定唯讀相依性屬性的一般原因是，這些屬性應該用來判斷狀態，然而該狀態會受到許多因素影響，但從使用者介面設計觀點來看，只將屬性設為該狀態並不恰當。 例如，屬性<xref:System.Windows.UIElement.IsMouseOver%2A>其實只會呈現從滑鼠輸入所決定的狀態。 藉由規避實際的滑鼠輸入，以程式設計方式設定此值的任何嘗試，都是無法預測且會導致不一致的情況。  
  
 由於是不可設定的，因此，唯讀相依性屬性不適合許多相依性屬性通常可提供解決方案 (也就是：資料繫結、可直接設定的樣式值、驗證、動畫、繼承) 的案例。 儘管不可設定，唯讀相依性屬性仍然具有一些屬性系統中相依性屬性所支援的其他功能。 其餘最重要的功能是，唯讀相依性屬性仍可用來做為樣式中的屬性觸發程序。 您無法透過一般 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性啟用觸發程序；它必須是相依性屬性。 上述<xref:System.Windows.UIElement.IsMouseOver%2A>屬性是完美的範例案例，其中可能會非常有用，其中有一些定義的樣式控制項，例如背景、 foreground 或類似的屬性中複合元素的 visible 屬性當使用者將滑鼠置於某些控制項的已定義區域的上方時，將會變更控制項。 屬性系統固有的失效處理序也可以偵測到並回報唯讀相依性屬性中的變更，這實際上可在內部支援屬性觸發程序功能。  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>建立自訂唯讀相依性屬性  
 請務必閱讀前一節，以了解為什麼唯讀相依性屬性不適用許多一般的相依性屬性案例。 但是，如果您有適當的案例，您可能想要建立自己的唯讀相依性屬性。  
  
 在建立唯讀相依性屬性的處理序中，許多部分與[自訂相依性屬性](custom-dependency-properties.md)和[實作相依性屬性](how-to-implement-a-dependency-property.md)主題中所述的相同。 有三個重大差異：  
  
-   當註冊您的屬性，呼叫<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>方法，而非標準<xref:System.Windows.DependencyProperty.Register%2A>屬性註冊的方法。  
  
-   實作 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]「包裝函式」屬性，請確定包裝函式還沒有 set 實作，如此一來，就不會在您所公開之公用包裝函式的唯讀狀態中產生不一致的情況。  
  
-   唯讀註冊所傳回的物件是<xref:System.Windows.DependencyPropertyKey>而非<xref:System.Windows.DependencyProperty>。 您仍應將此欄位儲存為成員，但通常不需讓它成為類型的公用成員。  
  
 不論您必須支援的私用欄位或值為何，當然都能使用您決定的任何邏輯完整寫入您的唯讀相依性屬性。 不過，設定屬性 (不論是一開始就設定或設為執行階段邏輯一部分) 的最簡單方式是使用屬性系統的 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，而不是規避屬性系統來直接設定私用支援欄位。 特別是，沒有簽章<xref:System.Windows.DependencyObject.SetValue%2A>它會接受類型參數的<xref:System.Windows.DependencyPropertyKey>。 方式和位置您設定此值以程式設計方式在應用程式邏輯，會影響您可能想要如何設定存取<xref:System.Windows.DependencyPropertyKey>您第一次註冊相依性屬性時所建立。 如果您全都在類別內處理此邏輯，您可能會讓它成為私用，或者如果您需要從組件的其他部分設定它，則可能會將它設為內部。 其中一個方法是呼叫<xref:System.Windows.DependencyObject.SetValue%2A>相關的事件，以通知類別執行個體的預存的屬性值變更時所需的類別事件處理常式內。 另一種方法是將相依性屬性在一起的繫結使用配對<xref:System.Windows.PropertyChangedCallback>和<xref:System.Windows.CoerceValueCallback>回呼，註冊期間的那些屬性中繼資料的一部分。  
  
 因為<xref:System.Windows.DependencyPropertyKey>屬私人性質，並且不會傳播屬性系統，您的程式碼之外，唯讀相依性屬性有更好設定安全性會比讀寫相依性屬性。 針對讀寫相依性屬性，識別欄位是明確或隱含公開的，因此該屬性是可廣泛設定的。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。  
  
## <a name="see-also"></a>另請參閱
- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [樣式設定和範本化](../controls/styling-and-templating.md)
