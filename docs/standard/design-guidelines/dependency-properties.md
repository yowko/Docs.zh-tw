---
title: 相依性屬性
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7398202cc265fbd55b9bf0b5a53367dedcab57b0
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948481"
---
# <a name="dependency-properties"></a>相依性屬性
相依性屬性 (DP) 是將其值儲存在屬性存放區，而不是儲存在類型變數 （欄位），例如的一般屬性。  
  
 附加的相依性屬性是一種相依性屬性模型化成靜態代表 「 屬性 」 描述的物件和其容器之間的關聯性的 Get 和 Set 方法 (例如，位置`Button`物件上`Panel`容器）。  
  
 **✓ 不要**提供的相依性屬性，如果您需要支援 WPF 功能，例如樣式、 觸發程序、 資料繫結、 動畫、 動態的資源和繼承的屬性。  
  
## <a name="dependency-property-design"></a>相依性屬性的設計  
 **✓ 不要**繼承自<xref:System.Windows.DependencyObject>，或其中一個它的子類型，實作相依性屬性時。 此類型提供 una implementación muy eficaz 屬性存放區，會自動支援 WPF 資料繫結。  
  
 **✓ 不要**提供規則的 CLR 屬性和公用靜態唯讀欄位中儲存的執行個體<xref:System.Windows.DependencyProperty?displayProperty=nameWithType>每一個相依性屬性。  
  
 **✓ 不要**呼叫執行個體方法來實作相依性屬性<xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType>和<xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>。  
  
 **✓ 不要**藉由使用 「 屬性 」。 屬性名稱的尾碼名稱相依性屬性的靜態欄位  
  
 **X 不**程式碼中明確設定相依性屬性的預設值，則將它們設定在中繼資料。  
  
 如果您明確設定屬性的預設值，您可能會讓該屬性從某些隱含的方式，例如樣式設定。  
  
 **X 不**放置在屬性存取子標準的程式碼以外，若要存取的靜態欄位的程式碼。  
  
 程式碼將不會執行此屬性設定隱含的方式，例如樣式，如果因為樣式直接使用靜態欄位。  
  
 **X 不**使用相依性屬性來儲存資料的安全。 可公開存取甚至私用相依性屬性。  
  
## <a name="attached-dependency-property-design"></a>附加的相依性屬性的設計  
 上一節中所述的相依性屬性代表宣告的類型; 內建屬性例如，`Text`屬性是屬性的`TextButton`，其中宣告它。 一種特殊的相依性屬性是附加的相依性屬性。  
  
 附加屬性的典型的範例是<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>屬性。 此屬性代表按鈕的 （不方格的） 資料行位置，但是只有相關如果按鈕包含在方格中，因此它 「 附加 」 到按鈕的方格。  
  
```xaml
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 附加屬性的定義看起來大部分的一般相依性屬性的不同之處在於存取子都由靜態的 Get 和 Set 方法：  
  
```csharp
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a>相依性屬性驗證  
 屬性通常會實作稱為驗證。 當嘗試變更屬性的值時，就會執行驗證邏輯。  
  
 不幸的是相依性屬性存取子不能包含任意的驗證程式碼。 相反地，相依性屬性的驗證邏輯，需要屬性登錄期間指定。  
  
 **X 不**放在屬性存取子的相依性屬性的驗證邏輯。 相反地，通過驗證回呼，以`DependencyProperty.Register`方法。  
  
## <a name="dependency-property-change-notifications"></a>相依性屬性的變更告知  
 **X 不**在相依性屬性存取子實作變更通知邏輯。 相依性屬性具有內建的變更通知的一項功能，必須使用藉由提供變更通知回呼<xref:System.Windows.PropertyMetadata>。  
  
## <a name="dependency-property-value-coercion"></a>相依性屬性的值強制型轉  
 屬性的強制型轉會發生時實際修改的屬性存放區之前 setter 修改該值提供給屬性 setter。  
  
 **X 不**強制型轉邏輯實作相依性屬性存取子中。  
  
 相依性屬性有內建的強制型轉功能，並可供提供強制型轉回撥到`PropertyMetadata`。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [一般設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)
