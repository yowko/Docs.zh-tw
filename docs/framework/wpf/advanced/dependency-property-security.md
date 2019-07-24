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
ms.openlocfilehash: 2f9de32eb8637e58c17aba2309eed33dcfdd42a7
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400763"
---
# <a name="dependency-property-security"></a>相依性屬性的安全性
相依性屬性通常應該視為公用屬性。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統在本質上會防止進行相依性屬性值的安全性保證。  

<a name="AccessSecurity"></a>   
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>包裝函式和相依性屬性的存取和安全性  
 通常, 相依性屬性會與「包裝函式」 common language runtime (CLR) 屬性一起執行, 以簡化從實例取得或設定屬性的方式。 但是, 包裝函式其實只是一種便利的<xref:System.Windows.DependencyObject.GetValue%2A>方法<xref:System.Windows.DependencyObject.SetValue%2A> , 可執行與相依性屬性互動時所使用的基礎和靜態呼叫。 以另一種方式思考, 這些屬性會公開為通用語言執行平臺 (CLR) 屬性, 而這些屬性會被相依性屬性 (而非私用欄位) 所支援。 套用到包裝函式的安全性機制，與屬性系統行為和基礎相依性屬性的存取並不相同。 在包裝函式上放置安全性需求, 只會防止使用便利方法, 但不會防止呼叫<xref:System.Windows.DependencyObject.GetValue%2A>或。 <xref:System.Windows.DependencyObject.SetValue%2A> 同樣地，對包裝函式設置保護或私用存取層級並不會提供任何有效的安全性防護。  
  
 如果您要撰寫自己的相依性屬性, 您應該將包裝函式<xref:System.Windows.DependencyProperty>和識別碼欄位宣告為公用成員, 讓呼叫端不會收到關於該屬性之真正存取層級的誤導資訊 (因為其存放區是實作為相依性屬性)。  
  
 若為自訂相依性屬性, 您可以將屬性註冊為唯讀相依性屬性, 這樣做會提供有效的方法, 防止未持有該屬性之參考<xref:System.Windows.DependencyPropertyKey>的任何人設定屬性。 如需詳細資訊，請參閱[唯讀相依性屬性](read-only-dependency-properties.md)。  
  
> [!NOTE]
>  不允許將識別碼欄位設為私用, 而且它可以用來協助減少立即公開的自訂類別命名空間, 但是這類屬性不應視為「私用」, 與通用語言相同<xref:System.Windows.DependencyProperty>執行時間 (CLR) 語言定義會定義該存取層級, 原因如下一節中所述。  
  
<a name="PropertySystemExposure"></a>   
## <a name="property-system-exposure-of-dependency-properties"></a>相依性屬性的屬性系統公開  
 它通常並不實用, 而且可能會誤導, 以宣告為公用<xref:System.Windows.DependencyProperty>以外的任何存取層級。 該存取層級設定只能防止使用者取得宣告類別執行個體的參考。 但在屬性系統中, 有幾個層面會<xref:System.Windows.DependencyProperty>傳回, 做為在類別或衍生類別實例的實例上識別特定屬性的方法, 而且這個識別碼仍然可以<xref:System.Windows.DependencyObject.SetValue%2A>在呼叫中使用。如果原始靜態識別碼宣告為非公用。 此外, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>虛擬方法也會接收任何已變更值之現有相依性屬性的資訊。 此外, 此<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>方法會針對具有本機設定值的實例上的任何屬性傳回識別碼。  
  
### <a name="validation-and-security"></a>驗證和安全性  
 將需求套用至<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> , 並預期在要求失敗時驗證失敗, 以防止設定屬性不是適當的安全性機制。 透過<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>強制執行的設定值失效, 如果這些呼叫端是在應用程式域內運作, 惡意的呼叫端也可能會隱藏。  
  
## <a name="see-also"></a>另請參閱

- [自訂相依性屬性](custom-dependency-properties.md)
