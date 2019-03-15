---
title: x:Shared 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: 42de341d59e3e70103db765faf3160b5fe3250d3
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58039401"
---
# <a name="xshared-attribute"></a>x:Shared 屬性
當設定為`false`，修改 WPF 擷取資源的行為，讓屬性化資源的要求建立新的執行個體，針對每個要求，而不是共用相同的執行個體的所有要求。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>備註  
 `x:Shared` 對應至 XAML 語言 XAML 命名空間，且.NET Framework XAML 服務和其 XAML 讀取器所辨識為有效的 XAML 語言項目。 不過，所述的功能`x:Shared`才相關 WPF 應用程式和 WPF XAML 剖析器。 在 WPF 中，`x:Shared`才有用做為屬性，它會套用至存在於 WPF 中的物件時<xref:System.Windows.ResourceDictionary>。 其他使用方式不擲回剖析例外狀況或其他錯誤，但它們沒有任何作用。  
  
 意義`x:Shared`XAML 語言規格中未指定。 其他 XAML 實作中的，例如建置在.NET Framework XAML 服務中，不一定會提供資源共用的支援。 這類的 XAML 實作可以提供類似的行為，在支援的架構，也可以用`x:Shared`值。  
  
 在 WPF 中，預設值`x:Shared`資源的條件是`true`。 這種情況表示，任何指定的資源要求一律會傳回相同的執行個體。  
  
 修改物件，例如傳回資源的 API，透過<xref:System.Windows.FrameworkElement.FindResource%2A>，或修改物件直接內<xref:System.Windows.ResourceDictionary>，變更原始的資源。 如果該資源的參考動態資源參考，該資源的取用者會取得已變更的資源。  
  
 如果資源的參考靜態資源參考，變更後的資源為[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]處理時間無關。 如需靜態與動態資源參考的詳細資訊，請參閱[XAML 資源](../wpf/advanced/xaml-resources.md)。  
  
 明確指定`x:Shared="true"`很罕見，因為這已經是預設值。 沒有對等的程式碼直接`x:Shared`WPF 中的物件模型; 它只能指定在 XAML 用法，並必須處理的預設 WPF 行為或中繼上載入路徑 XAML 節點資料流中，如果使用.NET Framework XAML Se 處理rvices 和其 XAML 讀取器。  
  
 案例`x:Shared="false"`就是如果您定義<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生類別做為資源，然後您引入的項目資源內容的模型。 `x:Shared="false"` 可讓在相同的集合，將推出許多次的項目資源 (例如<xref:System.Windows.Controls.UIElementCollection>)。 不含`x:Shared="false"`這是無效的因為集合會強制執行唯一性的內容。 不過，`x:Shared="false"`行為會建立另一個資源，而不是傳回相同的執行個體的相同執行個體。  
  
 另一個情節`x:Shared="false"`是如果您使用<xref:System.Windows.Freezable>動畫值，但想来修改的資源，以每個動畫為基礎的資源。  
  
 字串處理`false`不區分大小寫。  
  
 在 WPF 中，`x:Shared`下列條件下才有效：  
  
-   <xref:System.Windows.ResourceDictionary>所包含的項目`x:Shared`必須編譯。 <xref:System.Windows.ResourceDictionary>不可在鬆散的 XAML，或用於佈景主題。  
  
-   <xref:System.Windows.ResourceDictionary>所包含的項目進行巢狀在另一個<xref:System.Windows.ResourceDictionary>。 例如，您無法使用`x:Shared`中的項目<xref:System.Windows.ResourceDictionary>裡<xref:System.Windows.Style>已經<xref:System.Windows.ResourceDictionary>項目。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.ResourceDictionary>
- [XAML 資源](../wpf/advanced/xaml-resources.md)
- [基底項目](../wpf/advanced/base-elements.md)
