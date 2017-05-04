---
title: "相依性屬性回呼和驗證 | Microsoft Docs"
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
  - "回呼, 驗證"
  - "強制轉型值回呼"
  - "相依性屬性, 回呼"
  - "相依性屬性, 驗證"
  - "相依性屬性驗證"
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 相依性屬性回呼和驗證
本主題說明如何使用屬性相關功能 \(例如有效性驗證\) 的替代自訂實作、每次屬性有效值變更時叫用 \(Invoke\) 的回呼 \(Callback\)，以及對值決策的覆寫可能外在影響，建立相依性屬性。  這個主題也討論適合使用這些技巧來擴大預設屬性系統行為的案例。  
  
   
  
<a name="prerequisites"></a>   
## 必要條件  
 本主題假設您已了解實作相依性屬性的基本案例，以及中繼資料 \(Metadata\) 套用至自訂相依性屬性的方式。  如需相關內容，請參閱[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)和[相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)。  
  
<a name="Validation_Callbacks"></a>   
## 驗證回呼  
 您可以在第一次註冊相依性屬性時為其指派驗證回呼。  驗證回呼不是屬性中繼資料的一部分，而是 <xref:System.Windows.DependencyProperty.Register%2A> 方法的直接輸入。  因此，一旦建立相依性屬性的驗證回呼之後，就不能以新實作加以覆寫。  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 實作回呼的方式就是針對回呼提供物件值。  如果提供的值是屬性的有效值，回呼會傳回 `true`，否則便會傳回 `false`。  一般假設屬性具有正確的型別 \(依據向屬性系統註冊的型別來判斷\)，因此通常不會在回呼內檢查型別。  屬性系統會在各種不同的作業中使用回呼，  包括依預設值進行初次的型別初始設定、透過叫用 <xref:System.Windows.DependencyObject.SetValue%2A> 進行程式設計變更，或是嘗試以提供的預設值覆寫中繼資料。  如果驗證回呼是由前述任何一項作業所叫用，並傳回 `false`，則會引發例外狀況。  應用程式撰寫者必須做好處理這些例外狀況的準備。  驗證回呼通常用來驗證列舉值，或是在屬性設定必須是零或大於零的度量資訊時，限制整數或雙精度浮點數 \(Double\) 的值。  
  
 驗證回呼是專門用來做為類別驗證程式，而非執行個體驗證程式。  回呼的參數不會傳遞設定要驗證之屬性的特定 <xref:System.Windows.DependencyObject>。  因此驗證回呼並不能用來強制採用可能影響屬性值的「相依性」，其中屬性的執行個體專用值相依於諸如其他屬性之執行個體專用值或執行階段狀態等因素。  
  
 下列範例程式碼適用於非常簡單的驗證回呼案例：驗證基本型別為 <xref:System.Double> 的屬性不是 <xref:System.Double.PositiveInfinity> 或 <xref:System.Double.NegativeInfinity>。  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## 強制轉型值回呼和屬性變更事件  
 強制轉型值回呼會傳遞屬性的特定 <xref:System.Windows.DependencyObject> 執行個體，而每次相依性屬性值變更時屬性系統所叫用的 <xref:System.Windows.PropertyChangedCallback> 實作也一樣。  您可以搭配使用這兩種回呼，在項目上建立一系列屬性，讓其中一個屬性的變更強制另一個屬性進行強制轉型或重新評估。  
  
 使用相依性屬性之連結的典型案例是當您擁有使用者介面驅動屬性，而其中項目各持有一個最小值和最大值的屬性，以及另一個實際值或目前值的屬性。  在此案例中，如果調整最大值後導致目前的值超過新的最大值，您可能需要強制轉型目前的值，使其不大於新的最大值，同時讓最小值與目前的值產生類似的關係。  
  
 以下顯示一段非常簡短的程式碼範例，僅適用於說明這種關係的三種相依性屬性其中一種。  此範例示範如何註冊相關 \*Reading 屬性之 Min\/Max\/Current 集合的 `CurrentReading` 屬性。  範例中使用驗證的方式如上一節所示。  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 Current 的屬性變更回呼可用來將變更轉送至其他相依屬性，方法是明確叫用針對其他屬性註冊的強制轉型值回呼：  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 強制轉型值回會檢查目前屬性可能相依的屬性值，並在必要時強制轉型目前的值：  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  屬性的預設值不會強制轉型。  屬性值等於預設值的情況可能發生在屬性值仍然具有其初始預設值時，或是以 <xref:System.Windows.DependencyObject.ClearValue%2A> 清除其他值之後。  
  
 強制轉型值回呼和屬性變更回呼是屬性中繼資料的一部分。  因此，若特定相依屬性所在的型別係衍生自擁有該相依屬性的型別，您就可以透過在自己的型別上覆寫該屬性的中繼資料，以變更該特定相依性屬性的回呼。  
  
<a name="Advanced"></a>   
## 進階強制轉型和回呼案例  
  
### 限制條件和需要的值  
 屬性系統會依照您宣告的邏輯，使用 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 回呼來強制轉型值，但本機設定之屬性的強制轉型值在內部仍會保留「需要的值」。  如果條件約束以在應用程式存留期 \(Lifetime\) 間可能動態變更的其他屬性值做為基礎，強制轉型 \(Coercion\) 條件約束也會動態變更，而受限制的屬性則可變更其值，以便在新條件約束的限制下取得最接近需要的值。  如果解除所有條件約束，這個值就會變成需要的值。  如果您擁有多個屬性，而這些屬性彼此具有循環相依關係，您可能會引入某些相當複雜的相依性案例。  例如，在 Min\/Max\/Current 案例中，您可以選擇讓 Minimum 和 Maximum 變成使用者可設定的項目。  若是如此，您可能必須強制轉型讓 Maximum 永遠大於 Minimum，且反之亦然。  但是如果該強制轉型正在作用，且 Maximum 強制轉型成 Minimum，它就會讓 Current 處於無法設定的狀態，因為這個值相依於兩者，而且受限為兩個值之間的範圍，而這個範圍是零。  接著，如果 Maximum 或 Minimum 已經過調整，Current 就會「採用」其中一個值，因為 Current 需要的值仍為儲存狀態，而且正嘗試達到需要的值，如同解除條件約束時一般。  
  
 複雜的相依性在技術上並無任何不當之處，但是如果這種相依性需要進行大量的重新評估可能會對效能造成些微的負面影響，而若直接影響到 UI，也會對使用者造成困擾。  請審慎使用屬性變更和強制轉型值回呼，並確定嘗試執行的強制轉型能夠以最明確的方式處理，而且不會產生「過度條件約束」。  
  
### 使用 CoerceValue 取消值變更  
 屬性系統會將傳回 <xref:System.Windows.DependencyProperty.UnsetValue> 值的任何 <xref:System.Windows.CoerceValueCallback> 視為特例。  這個特例表示屬性系統應該拒絕造成呼叫 <xref:System.Windows.CoerceValueCallback> 之結果的屬性變更，而且應該改為回報屬性先前擁有的任何值。  這項機制可以用來檢查非同步啟始的屬性變更對於目前的物件狀態是否仍然有效，若已無效則隱藏這些變更。  另一個可能的案例是您可以依據負責回報值的屬性值元件，選擇性地隱藏值。  若要執行這項動作，您可以使用回呼中傳入的 <xref:System.Windows.DependencyProperty> 以及屬性識別項做為 <xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A> 的輸入，然後再處理 <xref:System.Windows.ValueSource>。  
  
## 請參閱  
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [相依性屬性中繼資料](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)