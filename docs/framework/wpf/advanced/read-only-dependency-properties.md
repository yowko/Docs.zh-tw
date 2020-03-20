---
title: 唯讀相依性屬性
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 8adc90182f0f42f52e6ace4e13c68acb3539516b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187173"
---
# <a name="read-only-dependency-properties"></a>唯讀相依性屬性
本主題說明唯讀相依性屬性，包括現有的唯讀相依性屬性，以及用於建立自訂唯讀相依性屬性的案例和技術。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必要條件  
 本主題假設您已了解實作相依性屬性的基本案例，以及如何將中繼資料套用到自訂相依性屬性。 如需相關內容，請參閱[自訂相依性屬性](custom-dependency-properties.md)和[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
<a name="existing"></a>
## <a name="existing-read-only-dependency-properties"></a>現有的唯讀相依性屬性  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 架構中定義的一些相依性屬性為唯讀狀態。 指定唯讀相依性屬性的一般原因是，這些屬性應該用來判斷狀態，然而該狀態會受到許多因素影響，但從使用者介面設計觀點來看，只將屬性設為該狀態並不恰當。 例如，屬性<xref:System.Windows.UIElement.IsMouseOver%2A>實際上只是從滑鼠輸入確定的曲面狀態。 藉由規避實際的滑鼠輸入，以程式設計方式設定此值的任何嘗試，都是無法預測且會導致不一致的情況。  
  
 由於是不可設定的，因此，唯讀相依性屬性不適合許多相依性屬性通常可提供解決方案 (也就是：資料繫結、可直接設定的樣式值、驗證、動畫、繼承) 的案例。 儘管不可設定，唯讀相依性屬性仍然具有一些屬性系統中相依性屬性所支援的其他功能。 其餘最重要的功能是，唯讀相依性屬性仍可用來做為樣式中的屬性觸發程序。 不能啟用具有普通通用語言運行時 （CLR） 屬性的觸發器;因此，無法啟用觸發器。它需要是一個依賴項屬性。 上述<xref:System.Windows.UIElement.IsMouseOver%2A>屬性是一個場景的完美示例，其中為控制項定義樣式可能非常有用，當使用者將滑鼠放在控制項的某些已定義的區域上時，控制項中某些可見屬性（如背景、前景或類似屬性）將發生變化。 屬性系統固有的失效處理序也可以偵測到並回報唯讀相依性屬性中的變更，這實際上可在內部支援屬性觸發程序功能。  
  
<a name="new"></a>
## <a name="creating-custom-read-only-dependency-properties"></a>建立自訂唯讀相依性屬性  
 請務必閱讀前一節，以了解為什麼唯讀相依性屬性不適用許多一般的相依性屬性案例。 但是，如果您有適當的案例，您可能想要建立自己的唯讀相依性屬性。  
  
 在建立唯讀相依性屬性的處理序中，許多部分與[自訂相依性屬性](custom-dependency-properties.md)和[實作相依性屬性](how-to-implement-a-dependency-property.md)主題中所述的相同。 有三個重大差異：  
  
- 註冊屬性時，調用<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>方法而不是屬性註冊的正常<xref:System.Windows.DependencyProperty.Register%2A>方法。  
  
- 實現 CLR"包裝器"屬性時，請確保包裝器也沒有集實現，因此公開的公共包裝器的唯讀狀態沒有不一致。  
  
- 唯讀註冊返回的物件不是<xref:System.Windows.DependencyPropertyKey><xref:System.Windows.DependencyProperty>。 您仍應將此欄位儲存為成員，但通常不需讓它成為類型的公用成員。  
  
 不論您必須支援的私用欄位或值為何，當然都能使用您決定的任何邏輯完整寫入您的唯讀相依性屬性。 但是，設置屬性的最直接方法是使用屬性系統的 API，而不是繞過屬性系統並直接設置私有備份欄位。 特別是，有一個接受類型參數<xref:System.Windows.DependencyObject.SetValue%2A><xref:System.Windows.DependencyPropertyKey>的簽名。 在應用程式邏輯中以程式設計方式設置此值的方式和位置將影響在首次註冊依賴項屬性時，您可能希望在<xref:System.Windows.DependencyPropertyKey>創建的上設置存取權限的方式。 如果您全都在類別內處理此邏輯，您可能會讓它成為私用，或者如果您需要從組件的其他部分設定它，則可能會將它設為內部。 一種方法是在類事件<xref:System.Windows.DependencyObject.SetValue%2A>處理常式中調用相關事件，該事件通知類實例需要更改存儲的屬性值。 另一種方法是在註冊期間使用配對<xref:System.Windows.PropertyChangedCallback>和<xref:System.Windows.CoerceValueCallback>回檔作為這些屬性中繼資料的一部分，將依賴項屬性綁定在一起。  
  
 由於<xref:System.Windows.DependencyPropertyKey>是私有的，並且不由代碼外部的屬性系統傳播，因此唯讀依賴項屬性的設置安全性確實優於讀寫依賴項屬性。 針對讀寫相依性屬性，識別欄位是明確或隱含公開的，因此該屬性是可廣泛設定的。 如需詳細資訊，請參閱[相依性屬性的安全性](dependency-property-security.md)。  
  
## <a name="see-also"></a>另請參閱

- [相依性屬性概觀](dependency-properties-overview.md)
- [自訂相依性屬性](custom-dependency-properties.md)
- [設定樣式和範本](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
