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
ms.openlocfilehash: 825b2a3dc79300f0cc26514398b8de0abee64fd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540500"
---
# <a name="dependency-property-security"></a>相依性屬性的安全性
相依性屬性通常應該視為公用屬性。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統在本質上會防止進行相依性屬性值的安全性保證。  
  
  
<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>包裝函式和相依性屬性的存取和安全性  
 通常，相依性屬性會與「包裝函式」[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性一起實作，該屬性會簡化對執行個體屬性的取得或設定。 包裝函式，其實就是便利的方法實作的基礎，但是<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>靜態相依性屬性和互動時所使用的呼叫。 從另一個方面來思考，這些屬性會公開為剛好受到相依性屬性 (而不是私用欄位) 支援的[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 屬性。 套用到包裝函式的安全性機制，與屬性系統行為和基礎相依性屬性的存取並不相同。 置於包裝函式的安全性要求將不僅可以防止便利的方法的使用方式，但不是會防止呼叫<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>。 同樣地，對包裝函式設置保護或私用存取層級並不會提供任何有效的安全性防護。  
  
 如果您要撰寫您自己的相依性屬性，您應該宣告包裝函式和<xref:System.Windows.DependencyProperty>識別碼欄位，做為公用成員，讓呼叫端沒有未取得容易發生錯誤，該屬性，則為 true 的存取層級的相關資訊 （因為它的存放區正在實作為相依性屬性。）  
  
 自訂相依性屬性，您可以註冊您的屬性為唯讀相依性屬性，並防止任何人都不包含的參考設定屬性的有效方法，這提供<xref:System.Windows.DependencyPropertyKey>該屬性。 如需詳細資訊，請參閱[唯讀相依性屬性](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)。  
  
> [!NOTE]
>  宣告<xref:System.Windows.DependencyProperty>不禁止的識別項欄位私用，並有助於減少立即公開的命名空間的自訂類別，可用理論上，但這類屬性不應視為相同的意義上，為 「 私人 」 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]語言定義所定義的存取層級下, 一節中所述的原因。  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>相依性屬性的屬性系統公開  
 不是通常很有用，而且很可能會產生誤導，來宣告<xref:System.Windows.DependencyProperty>任何存取層級而不是公用。 該存取層級設定只能防止使用者取得宣告類別執行個體的參考。 但有幾個層面的屬性系統，將會傳回<xref:System.Windows.DependencyProperty>做為識別特定的屬性，因為它存在於類別的執行個體或衍生的類別執行個體，而且這個識別碼是在仍可使用的方法<xref:System.Windows.DependencyObject.SetValue%2A>即使呼叫如果原始的靜態識別項宣告為 nonpublic。 此外，<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>虛擬方法都會接收值變更任何現有相依性屬性資訊。 此外，<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>方法會傳回任何屬性的識別項執行個體與本機設定值。  
  
### <a name="validation-and-security"></a>驗證和安全性  
 套用要求<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>和預期要求失敗，以防止屬性所設定的驗證失敗不是適當的安全性機制。 透過強制執行設定值失效<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>可能也會歸併被惡意呼叫端，如果應用程式定義域內操作這些呼叫端。  
  
## <a name="see-also"></a>另請參閱  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
