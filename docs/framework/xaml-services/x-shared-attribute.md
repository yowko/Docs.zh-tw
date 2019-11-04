---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459922"
---
# <a name="xshared-attribute"></a>x:Shared 屬性
設定為 `false`時，會修改 WPF 資源抓取行為，讓屬性化資源的要求為每個要求建立新的實例，而不是共用所有要求的相同實例。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>備註  
 `x:Shared` 會對應至 XAML 語言 XAML 命名空間，並藉由 .NET Framework XAML 服務及其 XAML 讀取器來辨識為有效的 XAML 語言專案。 不過，`x:Shared` 所述的功能僅與 WPF 應用程式和 WPF XAML 剖析器有關。 在 WPF 中，`x:Shared` 只有當屬性套用至存在於 WPF <xref:System.Windows.ResourceDictionary>內的物件時，才有用。 其他使用方式不會擲回剖析例外狀況或其他錯誤，但它們沒有任何作用。  
  
 XAML 語言規格中未指定 `x:Shared` 的意義。 其他 XAML 執行（例如建置於 .NET Framework XAML 服務上的）不一定會提供資源分享支援。 這類 XAML 執行可能會在支援的架構中，提供同樣用於 `x:Shared` 值的類似行為。  
  
 在 WPF 中，資源的預設 `x:Shared` 條件是 `true`。 這種情況表示任何指定的資源要求一律會傳回相同的實例。  
  
 修改透過資源 API 傳回的物件（例如 <xref:System.Windows.FrameworkElement.FindResource%2A>）或直接在 <xref:System.Windows.ResourceDictionary>中修改物件，會變更原始資源。 如果對該資源的參考是動態資源參考，該資源的取用者會取得已變更的資源。  
  
 如果資源的參考是靜態資源參考，則在 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 處理時間之後對資源所做的變更是不相關的。 如需靜態與動態資源參考的詳細資訊，請參閱[XAML 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)。  
  
 明確指定 `x:Shared="true"` 很少會完成，因為這已經是預設值。 WPF 物件模型中的 `x:Shared` 沒有直接的程式碼對應項;它只能在 XAML 使用方式中指定，而且如果使用 .NET Framework XAML 服務及其 XAML 讀取器來處理，則必須由預設 WPF 行為或載入路徑上的中繼 XAML 節點資料流程來處理。  
  
 `x:Shared="false"` 的案例是，如果您將 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 衍生的類別定義為資源，然後將元素資源引入內容模型中。 `x:Shared="false"` 可讓元素資源在同一個集合（例如 <xref:System.Windows.Controls.UIElementCollection>）中引進多次。 沒有 `x:Shared="false"` 這會無效，因為集合會強制執行其內容的唯一性。 不過，`x:Shared="false"` 行為會建立另一個相同的資源實例，而不會傳回相同的實例。  
  
 `x:Shared="false"` 的另一個案例是，如果您將 <xref:System.Windows.Freezable> 資源用於動畫值，但想要以每個動畫為基礎修改資源。  
  
 `false` 的字串處理不區分大小寫。  
  
 在 WPF 中，`x:Shared` 只有在下列情況下才有效：  
  
- 包含具有 `x:Shared` 之專案的 <xref:System.Windows.ResourceDictionary> 必須進行編譯。 <xref:System.Windows.ResourceDictionary> 不能在鬆散的 XAML 內或用於主題。  
  
- 包含專案的 <xref:System.Windows.ResourceDictionary> 不得嵌套在另一個 <xref:System.Windows.ResourceDictionary>內。 例如，您無法在已經是 <xref:System.Windows.ResourceDictionary> 專案的 <xref:System.Windows.Style> 中 <xref:System.Windows.ResourceDictionary> 專案使用 `x:Shared`。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.ResourceDictionary>
- [XAML 資源](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [基底項目](../wpf/advanced/base-elements.md)
