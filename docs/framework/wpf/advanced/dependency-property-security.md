---
title: 相依性屬性的安全性
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers [WPF], access
- wrappers [WPF], security
- dependency properties [WPF], security
- security [WPF], wrappers
- validation [WPF], dependency properties
- dependency properties [WPF], access
- security [WPF], dependency properties
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
ms.openlocfilehash: d51f8f5fd704b0c95b8e6f841b9b0ff8567899cb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364810"
---
# <a name="dependency-property-security"></a>相依性屬性的安全性
相依性屬性通常應該視為公用屬性。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統在本質上會防止進行相依性屬性值的安全性保證。  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>包裝函式和相依性屬性的存取和安全性  
 通常，相依性屬性會與「包裝函式」[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性一起實作，該屬性會簡化對執行個體屬性的取得或設定。 但包裝函式其實是便利的方法實作的基礎<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>與相依性屬性互動時所使用的靜態呼叫。 從另一個方面來思考，這些屬性會公開為剛好受到相依性屬性 (而不是私用欄位) 支援的[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性。 套用到包裝函式的安全性機制，與屬性系統行為和基礎相依性屬性的存取並不相同。 在 包裝函式設置安全性要求只會防止使用這種方便的方法，但不是會防止呼叫<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>。 同樣地，對包裝函式設置保護或私用存取層級並不會提供任何有效的安全性防護。  
  
 如果您正在撰寫自己的相依性屬性，您應該宣告包裝函式和<xref:System.Windows.DependencyProperty>識別碼欄位，為公用成員，讓呼叫端執行不誤會該屬性，則為 true 的存取層級 （因為其存放區正在實作為相依性屬性。）  
  
 自訂相依性屬性，您可以將屬性註冊為唯讀相依性屬性，因此這提供有效的方法，防止未持有的參考的任何人所設定的屬性<xref:System.Windows.DependencyPropertyKey>該屬性。 如需詳細資訊，請參閱[唯讀相依性屬性](read-only-dependency-properties.md)。  
  
> [!NOTE]
>  宣告<xref:System.Windows.DependencyProperty>識別項欄位為私用不會受到禁止，理論上可以用來協助降低直接公開的命名空間的自訂類別，而這類屬性不應視為 「 私用 」 同樣[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]語言定義會定義該存取層級下, 一節中所述的原因。  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>相依性屬性的屬性系統公開  
 它不實用，而且可能會造成誤導，來宣告<xref:System.Windows.DependencyProperty>任何存取層級而非公用。 該存取層級設定只能防止使用者取得宣告類別執行個體的參考。 但有幾個層面的屬性系統會傳回<xref:System.Windows.DependencyProperty>做為識別特定的屬性，因為它存在於類別的執行個體或衍生的類別的執行個體，而且這個識別碼是在仍可使用的方法<xref:System.Windows.DependencyObject.SetValue%2A>即使呼叫如果原始靜態識別項宣告為非公用。 此外，<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>虛擬方法接收的任何現有的相依性屬性的值變更的資訊。 颾魤 ㄛ<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>方法會傳回具有本機設定的執行個體上的任何屬性的識別碼值。  
  
### <a name="validation-and-security"></a>驗證和安全性  
 藉由套用至<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>和預期要求失敗，以防止屬性所設定的驗證失敗不是足夠的安全性機制。 透過強制執行設定值失效<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>也可以隱藏被惡意呼叫端，如果這些呼叫端應用程式定義域內操作。  
  
## <a name="see-also"></a>另請參閱
- [自訂相依性屬性](custom-dependency-properties.md)
