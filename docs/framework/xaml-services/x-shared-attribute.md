---
title: "x:Shared Attribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML [XAML Services], x:Shared attribute"
  - "x:Shared attribute [XAML Services]"
  - "Shared attribute in XAML [XAML Services]"
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
caps.latest.revision: 16
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 16
---
# x:Shared Attribute
設定為 `false` 時，便會修改 WPF 資源擷取行為，讓屬性化資源的要求為每個要求建立新的執行個體，而不會讓所有要求共用相同的執行個體。  
  
## XAML Attribute Usage  
  
```  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## 備註  
 `x:Shared` 對應至 XAML 語言 XAML 命名空間，而且由 .NET Framework XAML Services 及其 XAML 讀取器辨識為有效的 XAML 語言項目。  不過，`x:Shared` 的前述功能只與 WPF 應用程式和 WPF XAML 剖析器有關。  在 WPF 中，只有做為屬性套用至存在於 WPF <xref:System.Windows.ResourceDictionary> 內部的物件時，`x:Shared` 才會是有用的。  其他使用方式不會擲回剖析例外狀況或其他錯誤，但是它們沒有任何作用。  
  
 在 XAML 語言規格中未指定 `x:Shared` 的意義。  其他 XAML 實作，例如那些建置在 .NET Framework XAML Services 上的實作，並不一定會提供資源共用支援。  這類 XAML 實作可以提供與支援架構 \(也使用 `x:Shared` 值\) 類似的行為。  
  
 在 WPF 中，資源的預設 `x:Shared` 條件為 `true`。  這個條件代表任何指定的資源要求一定會傳回相同執行個體。  
  
 修改透過資源 API 傳回的物件，例如 <xref:System.Windows.FrameworkElement.FindResource%2A>，或是在 <xref:System.Windows.ResourceDictionary> 內直接修改物件，變更原始資源。  如果該資源的參考是動態資源參考，該資源的消費者會取得變更的資源  
  
 如果該資源的參考是靜態資源參考，則 [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] 處理時間過後的資源變更就無關緊要。  如需靜態與動態資源參考的詳細資訊，請參閱[XAML 資源](../../../ocs/framework/wpf/advanced/xaml-resources.md).  
  
 很少明確指定`x:Shared="true"`，因為這已經是預設值。  在 WPF 物件模型沒有 `x:Shared` 的直接對等程式碼。它只能以 XAML 使用方式來指定，而且必須由預設的 WPF 行為處理，或者如果使用 .NET Framework XAML Services 及其 XAML 讀取器處理，則必須位於載入路徑上的中繼 XAML 節點資料流中。  
  
 一個使用 `x:Shared="false"` 的情節是當您定義 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 衍生類別做為資源，並將項目資源引入內容模型時。  `x:Shared="false"` 可以讓項目資源多次引入至相同集合中 \(例如 <xref:System.Windows.Controls.UIElementCollection>\)。  沒有 `x:Shared="false"`，這就會是無效的，因為集合會強制其內容的唯一性。  然而，`x:Shared="false"`行為會建立另一個相同的資源執行個體，而非傳回相同的執行個體。a  
  
 另一個使用 `x:Shared="false"` 的情節，是當您使用動畫值的 <xref:System.Windows.Freezable> 資源，卻想要針對每個動畫修改資源。  
  
 `false` 的字串處理不會區分大小寫。  
  
 在 WPF 中，`x:Shared` 只有在下列條件下才是有效的：  
  
-   包含具有 `x:Shared` 的項目的 <xref:System.Windows.ResourceDictionary> 必須經過編譯。  <xref:System.Windows.ResourceDictionary> 不能位於鬆散的 XAML 內部，或是由佈景主題使用。  
  
-   包含項目的 <xref:System.Windows.ResourceDictionary> 不能位於另一個 <xref:System.Windows.ResourceDictionary> 的巢狀結構內。  例如，在已經是 <xref:System.Windows.ResourceDictionary> 項目的 <xref:System.Windows.Style> 內的 <xref:System.Windows.ResourceDictionary> 中，您不能使用項目的 `x:Shared`。  
  
## 請參閱  
 <xref:System.Windows.ResourceDictionary>   
 [XAML 資源](../../../ocs/framework/wpf/advanced/xaml-resources.md)   
 [基底項目](../../../ocs/framework/wpf/advanced/base-elements.md)