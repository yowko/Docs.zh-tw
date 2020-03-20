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
ms.openlocfilehash: f5640b348ccd68819052f58756489489371862d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186389"
---
# <a name="dependency-property-security"></a>相依性屬性的安全性
相依性屬性通常應該視為公用屬性。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統在本質上會防止進行相依性屬性值的安全性保證。  

<a name="AccessSecurity"></a>
## <a name="access-and-security-of-wrappers-and-dependency-properties"></a>包裝函式和相依性屬性的存取和安全性  
 通常，依賴項屬性與"包裝器"通用語言運行時 （CLR） 屬性一起實現，這些屬性可簡化從實例獲取或設置屬性。 但是，包裝器實際上只是實現與依賴項屬互時使用<xref:System.Windows.DependencyObject.GetValue%2A>的基礎<xref:System.Windows.DependencyObject.SetValue%2A>調用和靜態調用的便捷方法。 換句話考慮，屬性被公開為通用語言運行時 （CLR） 屬性，這些屬性恰好由依賴項屬性而不是私有欄位支援。 套用到包裝函式的安全性機制，與屬性系統行為和基礎相依性屬性的存取並不相同。 對包裝器發出安全要求只會阻止使用方便方法，但不會阻止對 或<xref:System.Windows.DependencyObject.GetValue%2A><xref:System.Windows.DependencyObject.SetValue%2A>的調用。 同樣地，對包裝函式設置保護或私用存取層級並不會提供任何有效的安全性防護。  
  
 如果要編寫自己的依賴項屬性，則應將包裝器和<xref:System.Windows.DependencyProperty>識別碼欄位聲明為公共成員，以便調用方不會收到有關該屬性的真實存取層級的誤導性資訊（因為它的存儲作為依賴項屬性實現）。  
  
 對於自訂依賴項屬性，您可以將屬性註冊為唯讀依賴項屬性，這確實提供了一種有效方法，可以防止不保存該屬性引用<xref:System.Windows.DependencyPropertyKey>的任何人設置屬性。 如需詳細資訊，請參閱[唯讀相依性屬性](read-only-dependency-properties.md)。  
  
> [!NOTE]
> 不禁止<xref:System.Windows.DependencyProperty>將識別碼欄位聲明為私有，可以想像，它可用於説明減少自訂類的立即公開的命名空間，但此類屬性不應被視為"私有"，其意義上與通用語言運行時 （CLR） 語言定義定義該存取層級相同，原因如下一節所述。  
  
<a name="PropertySystemExposure"></a>
## <a name="property-system-exposure-of-dependency-properties"></a>相依性屬性的屬性系統公開  
 將 a<xref:System.Windows.DependencyProperty>聲明為公共以外的任何存取層級通常沒有用，而且可能具有誤導性。 該存取層級設定只能防止使用者取得宣告類別執行個體的參考。 但是，屬性系統有幾個方面將返回 作為<xref:System.Windows.DependencyProperty>標識特定屬性的方法，因為它存在於類或派生類實例的實例上，並且此識別碼在<xref:System.Windows.DependencyObject.SetValue%2A>調用中仍然可用，即使原始靜態識別碼聲明為非公共的。 此外，<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>虛擬方法接收更改值的任何現有依賴項屬性的資訊。 此外，<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A>該方法返回具有本地設置值的實例上任何屬性的識別碼。  
  
### <a name="validation-and-security"></a>驗證和安全性  
 將請求應用於 和<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>預期在請求失敗時無法阻止屬性被設置的驗證失敗，這不是一個適當的安全機制。 如果這些調用方在應用程式域中<xref:System.Windows.DependencyProperty.ValidateValueCallback%2A>操作，則通過強制執行的設定值失效也可能被惡意調用方抑制。  
  
## <a name="see-also"></a>另請參閱

- [自訂相依性屬性](custom-dependency-properties.md)
