---
title: 相依性屬性回呼和驗證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], validation
- coerce value callbacks [WPF]
- callbacks [WPF], validation
- dependency properties [WPF], callbacks
- validation of dependency properties [WPF]
ms.assetid: 48db5fb2-da7f-49a6-8e81-3540e7b25825
ms.openlocfilehash: ff7cbd995ba52f3cea712cb02b72f91d40422c33
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363926"
---
# <a name="dependency-property-callbacks-and-validation"></a>相依性屬性回呼和驗證
本主題說明如何針對屬性相關的功能建立使用替代自訂實作的相依性屬性，例如：驗證判斷、每當屬性有效值變更時叫用的回撥，以及覆寫值決策的可能外在影響。 本主題也會討論適合使用這些技術在展開預設屬性系統行為的案例。  
  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必要條件  
 本主題假設您已了解實作相依性屬性的基本案例，以及如何將中繼資料套用到自訂相依性屬性。 如需相關內容，請參閱[自訂相依性屬性](custom-dependency-properties.md)和[相依性屬性中繼資料](dependency-property-metadata.md)。  
  
<a name="Validation_Callbacks"></a>   
## <a name="validation-callbacks"></a>驗證回撥  
 第一次登錄驗證回撥時，可以將它指派給相依性屬性。 驗證回撥不屬於屬性中繼資料;它是直接輸入<xref:System.Windows.DependencyProperty.Register%2A>方法。 因此，一旦針對相依性屬性建立驗證回撥，就不能以新的實作覆寫。  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 實作回撥以提供物件值。 如果提供的值對屬性有效，它們會傳回 `true`；否則傳回 `false`。 因為假設屬性是依照屬性系統登錄類型的正確類型，所以通常不會在回撥內檢查類型。 屬性系統在各種不同的作業中使用回撥。 這包括初始型別初始設定的預設值，以程式設計方式變更藉由叫用<xref:System.Windows.DependencyObject.SetValue%2A>，或嘗試使用提供的新預設值來覆寫中繼資料。 如果這些作業的任何一項叫用了驗證回撥，並傳回 `false`，則會引發例外狀況。 應用程式撰寫者必須準備好處理這些例外狀況。 驗證回撥的常見用法是驗證列舉值，或屬性設定必須為零或大於零的度量時，限制整數或雙精度浮點數。  
  
 驗證回撥原為專用的類別驗證程式，不是執行個體驗證程式。 回呼參數不通訊特定<xref:System.Windows.DependencyObject>上所設定要驗證的屬性。 因此，驗證回撥對強制執行可能影響屬性值的可能「相依性」無幫助，其中屬性的執行個體特定值是取決於其他屬性的執行個體特定值或執行階段狀態等因素。  
  
 以下是非常簡單之驗證回撥案例的範例程式碼： 驗證屬性的類型是<xref:System.Double>基本不<xref:System.Double.PositiveInfinity>或<xref:System.Double.NegativeInfinity>。  
  
 [!code-csharp[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#validatevaluecallback)]
 [!code-vb[DPCallbackOverride#ValidateValueCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#validatevaluecallback)]  
  
<a name="Coerce_Value_Callbacks_and_Property_Changed_Events"></a>   
## <a name="coerce-value-callbacks-and-property-changed-events"></a>強制轉型值回撥和屬性變更事件  
 強制轉型值回撥會傳遞特定<xref:System.Windows.DependencyObject>執行個體屬性，如同<xref:System.Windows.PropertyChangedCallback>每當相依性屬性的值變更時屬性系統叫用的實作。 搭配使用這兩種回撥，您可以在有以下特性的項目上建立一系列的屬性：一個屬性中的變更會強制另一個屬性轉型或重新評估。  
  
 使用相依性屬性連結的一般案例，是當您有使用者介面驅動的屬性，其中項目為最小值和最大值各保留一個屬性，為實際值或目前值保留第三個屬性。 在這裡，如果以某種方式調整了最大值，以致目前的值超過新的最大值，您可能會想要將目前的值強制轉型為不大於新的最大值，且為最小值和目前值的類似關聯。  
  
 以下是示範這種關係之三種相依性屬性其一的極短範例程式碼。 本例示範如何登錄相關 *Reading 屬性的最小值/最大值/目前值集合的 `CurrentReading` 屬性。 它使用上一節中示範的驗證。  
  
 [!code-csharp[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#currentdefinitionwithwrapper)]
 [!code-vb[DPCallbackOverride#CurrentDefinitionWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#currentdefinitionwithwrapper)]  
  
 目前值的屬性變更回撥藉由明確叫用已為其他屬性登錄的強制轉型值回撥，用來將變更轉送至其他相依的屬性：  
  
 [!code-csharp[DPCallbackOverride#OnPCCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#onpccurrent)]
 [!code-vb[DPCallbackOverride#OnPCCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#onpccurrent)]  
  
 強制轉型值回撥會檢查目前屬性可能相依的屬性值，如有必要會強制轉型目前的值︰  
  
 [!code-csharp[DPCallbackOverride#CoerceCurrent](~/samples/snippets/csharp/VS_Snippets_Wpf/DPCallbackOverride/CSharp/SDKSampleLibrary/class1.cs#coercecurrent)]
 [!code-vb[DPCallbackOverride#CoerceCurrent](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DPCallbackOverride/visualbasic/sdksamplelibrary/class1.vb#coercecurrent)]  
  
> [!NOTE]
>  不會強制轉型屬性的預設值。 如果屬性值仍有其初始的預設值，或清除與其他值，可能會發生屬性值等於預設值<xref:System.Windows.DependencyObject.ClearValue%2A>。  
  
 強制轉型值和屬性變更回撥是屬性中繼資料的一部分。 因此，您可以覆寫您類型上該屬性的中繼資料，變更特定相依性屬性的回撥，因為它存在於擁有相依性屬性之衍生來源的類型。  
  
<a name="Advanced"></a>   
## <a name="advanced-coercion-and-callback-scenarios"></a>進階的強制型轉和回撥案例  
  
### <a name="constraints-and-desired-values"></a>條件約束和所需的值  
 <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>屬性系統強制值符合您宣告時，邏輯，但強制轉型的本機設定值使用回撥屬性仍然會保留 「 所需的值 」 在內部。 如果條件約束是以在應用程式存留期間可能動態變更的其他屬性值為基礎，則強制型轉條件約束也會動態變更，而受條件約束的屬性可以變更其值，以儘量接近新條件約束指定的所需值。 如果提取所有條件約束，則值會成為所需的值。 如有多個屬性彼此循環相依，您可能會造成相當複雜的相依性情況。 例如，在最小值/最大值/目前值的案例中，您可以選擇讓使用者能設定最小值和最大值。 如果這樣，您可能需要強制轉型「最大值」一律大於「最小值」，反之亦然。 但若該強制型轉為作用中，且「最大值」強制轉型成「最小值」，會讓目前值處於無法設定的狀態，因為它相依於兩者，且受條件約束在值的範圍內，也就是零。 然後，如果調整「最大值」或「最小值」，目前值就似乎會「遵循」其中一個值，因為因為當條件約束放寬時，目前值的所需值仍會儲存並嘗試達到所需的值。  
  
 複雜相依性沒有任何技術問題，但如果它們需要大量重新評估，對效能會略有損害，如果直接影響到 UI 也會造成使用者困擾。 請小心使用屬性變更和強制轉型值回撥，確定嘗試中的強制轉型能盡可能明確處理，不會「過度約束」。  
  
### <a name="using-coercevalue-to-cancel-value-changes"></a>使用 CoerceValue 取消值變更  
 屬性系統會將任何<xref:System.Windows.CoerceValueCallback>的傳回值<xref:System.Windows.DependencyProperty.UnsetValue>視為特殊案例。 表示屬性變更，導致這種特殊案例<xref:System.Windows.CoerceValueCallback>呼叫應該由屬性系統，遭到拒絕，且屬性系統應該改為回報屬性有任何先前的值。 這項機制很有用，可用來檢查過去以非同步方式初始化的屬性變更，現在是否對目前的物件狀態仍然有效，如果無效，則隱藏這些變更。 另一個可能的情況是，您可以看哪一個屬性值決定元件負責要回報的值，選擇性地隱藏值。 若要這樣做，您可以使用<xref:System.Windows.DependencyProperty>做為輸入傳遞回撥和屬性的識別項<xref:System.Windows.DependencyPropertyHelper.GetValueSource%2A>，然後再處理<xref:System.Windows.ValueSource>。  
  
## <a name="see-also"></a>另請參閱
- [相依性屬性概觀](dependency-properties-overview.md)
- [相依性屬性中繼資料](dependency-property-metadata.md)
- [自訂相依性屬性](custom-dependency-properties.md)
