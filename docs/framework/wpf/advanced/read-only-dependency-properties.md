---
title: 唯讀相依性屬性
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: aa6893b100311ead74f610dd20f327d130dff74a
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401648"
---
# <a name="read-only-dependency-properties"></a>唯讀相依性屬性
本主題說明唯讀相依性屬性，包括現有的唯讀相依性屬性，以及用於建立自訂唯讀相依性屬性的案例和技術。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已了解實作相依性屬性的基本案例，以及如何將中繼資料套用到自訂相依性屬性。 如需相關內容，請參閱[自訂相依性屬性](custom-dependency-properties.md)和[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>現有的唯讀相依性屬性  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中定義的一些相依性屬性為唯讀狀態。 指定唯讀相依性屬性的一般原因是，這些屬性應該用來判斷狀態，然而該狀態會受到許多因素影響，但從使用者介面設計觀點來看，只將屬性設為該狀態並不恰當。 例如, 屬性<xref:System.Windows.UIElement.IsMouseOver%2A>實際上只會呈現從滑鼠輸入決定的狀態。 藉由規避實際的滑鼠輸入，以程式設計方式設定此值的任何嘗試，都是無法預測且會導致不一致的情況。  
  
 由於是不可設定的，因此，唯讀相依性屬性不適合許多相依性屬性通常可提供解決方案 (也就是：資料繫結、可直接設定的樣式值、驗證、動畫、繼承) 的案例。 儘管不可設定，唯讀相依性屬性仍然具有一些屬性系統中相依性屬性所支援的其他功能。 其餘最重要的功能是，唯讀相依性屬性仍可用來做為樣式中的屬性觸發程序。 您無法使用一般 common language runtime (CLR) 屬性來啟用觸發程式。它必須是相依性屬性。 前述<xref:System.Windows.UIElement.IsMouseOver%2A>的屬性是案例的最佳範例, 其中可能非常適合用來定義控制項的樣式, 其中有些可見屬性 (例如背景、前景或類似的屬性, 在當使用者將滑鼠放在控制項的某個定義區域上方時, 控制項就會變更。 屬性系統固有的失效處理序也可以偵測到並回報唯讀相依性屬性中的變更，這實際上可在內部支援屬性觸發程序功能。  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>建立自訂唯讀相依性屬性  
 請務必閱讀前一節，以了解為什麼唯讀相依性屬性不適用許多一般的相依性屬性案例。 但是，如果您有適當的案例，您可能想要建立自己的唯讀相依性屬性。  
  
 在建立唯讀相依性屬性的處理序中，許多部分與[自訂相依性屬性](custom-dependency-properties.md)和[實作相依性屬性](how-to-implement-a-dependency-property.md)主題中所述的相同。 有三個重大差異：  
  
- 在註冊您的<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>屬性時, 請呼叫方法, 而不是屬性註冊的一般<xref:System.Windows.DependencyProperty.Register%2A>方法。  
  
- 在執行 CLR 「包裝函式」屬性時, 請確定包裝函式也沒有設定的執行, 如此您公開的公用包裝函式就不會有不一致的唯讀狀態。  
  
- 唯讀註冊所傳回的物件是, <xref:System.Windows.DependencyPropertyKey> <xref:System.Windows.DependencyProperty>而不是。 您仍應將此欄位儲存為成員，但通常不需讓它成為類型的公用成員。  
  
 不論您必須支援的私用欄位或值為何，當然都能使用您決定的任何邏輯完整寫入您的唯讀相依性屬性。 不過, 一開始或做為執行時間邏輯的一部分設定屬性最直接的方式, 就是使用屬性系統的 Api, 而不是避開屬性系統並直接設定私用支援欄位。 特別是, 有一個<xref:System.Windows.DependencyObject.SetValue%2A>可接受型<xref:System.Windows.DependencyPropertyKey>別之參數的簽章。 您在應用程式邏輯中設定此值的方式和位置, 將會影響您在第一次註冊<xref:System.Windows.DependencyPropertyKey>相依性屬性時所建立之上的存取權。 如果您全都在類別內處理此邏輯，您可能會讓它成為私用，或者如果您需要從組件的其他部分設定它，則可能會將它設為內部。 其中一個方法是在<xref:System.Windows.DependencyObject.SetValue%2A>相關事件的類別事件處理常式中呼叫, 通知類別實例必須變更儲存的屬性值。 另一種方法是在註冊期間使用配對<xref:System.Windows.PropertyChangedCallback>的和<xref:System.Windows.CoerceValueCallback>回呼, 將相依性屬性結合在這些屬性的中繼資料中。  
  
 <xref:System.Windows.DependencyPropertyKey>因為是私用的, 而且不是由您的程式碼外部的屬性系統所傳播, 所以唯讀相依性屬性的設定安全性比讀寫相依性屬性更好。 針對讀寫相依性屬性，識別欄位是明確或隱含公開的，因此該屬性是可廣泛設定的。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。  
  
## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [樣式設定和範本化](../controls/styling-and-templating.md)
