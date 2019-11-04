---
title: 唯讀相依性屬性
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: a849b835bab832a4ddb8d594d1788ab062f4284e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459000"
---
# <a name="read-only-dependency-properties"></a>唯讀相依性屬性
本主題說明唯讀相依性屬性，包括現有的唯讀相依性屬性，以及用於建立自訂唯讀相依性屬性的案例和技術。  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prerequisites  
 本主題假設您已了解實作相依性屬性的基本案例，以及如何將中繼資料套用到自訂相依性屬性。 如需相關內容，請參閱[自訂相依性屬性](custom-dependency-properties.md)和[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>現有的唯讀相依性屬性  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中定義的一些相依性屬性為唯讀狀態。 指定唯讀相依性屬性的一般原因是，這些屬性應該用來判斷狀態，然而該狀態會受到許多因素影響，但從使用者介面設計觀點來看，只將屬性設為該狀態並不恰當。 例如，屬性 <xref:System.Windows.UIElement.IsMouseOver%2A> 實際上只會呈現從滑鼠輸入決定的狀態。 藉由規避實際的滑鼠輸入，以程式設計方式設定此值的任何嘗試，都是無法預測且會導致不一致的情況。  
  
 由於是不可設定的，因此，唯讀相依性屬性不適合許多相依性屬性通常可提供解決方案 (也就是：資料繫結、可直接設定的樣式值、驗證、動畫、繼承) 的案例。 儘管不可設定，唯讀相依性屬性仍然具有一些屬性系統中相依性屬性所支援的其他功能。 其餘最重要的功能是，唯讀相依性屬性仍可用來做為樣式中的屬性觸發程序。 您無法使用一般 common language runtime （CLR）屬性來啟用觸發程式。它必須是相依性屬性。 前述的 <xref:System.Windows.UIElement.IsMouseOver%2A> 屬性是一個案例的最佳範例，其中可能非常適合用來定義控制項的樣式，其中某些可見屬性（例如背景、前景或控制項中複合元素的類似屬性）將會當使用者將滑鼠放在控制項的某個定義區域時進行變更。 屬性系統固有的失效處理序也可以偵測到並回報唯讀相依性屬性中的變更，這實際上可在內部支援屬性觸發程序功能。  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>建立自訂唯讀相依性屬性  
 請務必閱讀前一節，以了解為什麼唯讀相依性屬性不適用許多一般的相依性屬性案例。 但是，如果您有適當的案例，您可能想要建立自己的唯讀相依性屬性。  
  
 在建立唯讀相依性屬性的處理序中，許多部分與[自訂相依性屬性](custom-dependency-properties.md)和[實作相依性屬性](how-to-implement-a-dependency-property.md)主題中所述的相同。 有三個重大差異：  
  
- 註冊屬性時，請呼叫 <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> 方法，而不是屬性註冊的一般 <xref:System.Windows.DependencyProperty.Register%2A> 方法。  
  
- 在執行 CLR 「包裝函式」屬性時，請確定包裝函式也沒有設定的執行，如此您公開的公用包裝函式就不會有不一致的唯讀狀態。  
  
- 唯讀註冊所傳回的物件是 <xref:System.Windows.DependencyPropertyKey>，而不是 <xref:System.Windows.DependencyProperty>。 您仍應將此欄位儲存為成員，但通常不需讓它成為類型的公用成員。  
  
 不論您必須支援的私用欄位或值為何，當然都能使用您決定的任何邏輯完整寫入您的唯讀相依性屬性。 不過，一開始或做為執行時間邏輯的一部分設定屬性最直接的方式，就是使用屬性系統的 Api，而不是避開屬性系統並直接設定私用支援欄位。 特別是，<xref:System.Windows.DependencyObject.SetValue%2A> 的簽章會接受 <xref:System.Windows.DependencyPropertyKey>類型的參數。 您在應用程式邏輯中設定此值的方式和位置，將會影響您在第一次註冊相依性屬性時所建立的 <xref:System.Windows.DependencyPropertyKey> 上，您可能想要設定存取權的方式。 如果您全都在類別內處理此邏輯，您可能會讓它成為私用，或者如果您需要從組件的其他部分設定它，則可能會將它設為內部。 其中一個方法是在相關事件的類別事件處理常式中呼叫 <xref:System.Windows.DependencyObject.SetValue%2A>，通知類別實例必須變更儲存的屬性值。 另一個方法是使用配對的 <xref:System.Windows.PropertyChangedCallback> 將相依性屬性結合在一起，並在註冊期間 <xref:System.Windows.CoerceValueCallback> 回呼做為這些屬性中繼資料的一部分。  
  
 因為 <xref:System.Windows.DependencyPropertyKey> 是私用的，而且不是由您程式碼外部的屬性系統所傳播，所以唯讀相依性屬性會比讀寫相依性屬性更能設定安全性。 針對讀寫相依性屬性，識別欄位是明確或隱含公開的，因此該屬性是可廣泛設定的。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。  
  
## <a name="see-also"></a>請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
