---
title: "相依性屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# 相依性屬性
相依性屬性 \(DP\) 是將其值儲存在屬性儲存區，而不是儲存在型別變數 （欄位），例如一般屬性。  
  
 附加的相依性屬性是一種相依性屬性模型化成靜態表示 「 屬性 」 描述的物件和其容器之間的關聯性的 Get 和 Set 方法 \(例如，位置 `Button` 物件上 `Panel` 容器\)。  
  
 **✓ 執行** 提供相依性屬性，如果您需要支援 WPF 的功能，例如樣式、 觸發程序、 資料繫結、 動畫、 動態資源和繼承的屬性。  
  
## 相依性屬性設計  
 **✓ 執行** 繼承自 <xref:System.Windows.DependencyObject>, ，或它的子類型，實作相依性屬性時的其中一個。 這個類型提供非常有效率的內容儲存區實作，會自動支援 WPF 資料繫結。  
  
 **✓ 執行** 提供一般 CLR 屬性和公用靜態唯讀欄位儲存的執行個體 <xref:System.Windows.DependencyProperty?displayProperty=fullName> 針對每個相依性屬性。  
  
 **✓ 執行** 呼叫執行個體方法實作相依性屬性 <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=fullName> 和 <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=fullName>。  
  
 **✓ 執行** 「 屬性 」。 與屬性名稱所命名的相依性屬性的靜態欄位  
  
 **X 不** 程式碼中明確設定相依性屬性的預設值，將它們設定在中繼資料。  
  
 如果您明確設定屬性的預設值，可能會使該屬性無法以隱含方式，例如樣式來設定。  
  
 **X 不** 將程式碼放在非標準的程式碼存取的靜態資料行屬性存取子。  
  
 程式碼將不會執行，如果屬性設定為隱含的方式，例如樣式，因為樣式直接使用的靜態欄位。  
  
 **X 不** 使用相依性屬性來儲存資料的安全。 即便是私用相依性屬性可以公開存取。  
  
## 附加的相依性屬性設計  
 上一節中所述的相依性屬性代表內建屬性的宣告型別。例如， `Text` 屬性是屬性的 `TextButton`, ，這會將其宣告。 一種特殊的相依性屬性是附加的相依性屬性。  
  
 附加屬性的典型的範例是 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=fullName> 屬性。 屬性代表按鈕的 （不方格的） 資料行位置，不過它只與相關按鈕已包含在方格中，因此它會 「 附加 」 至按鈕的方格。  
  
```  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 附加屬性的定義看起來大部分的一般相依性屬性，不同之處在於存取子都由靜態的 Get 和 Set 方法︰  
  
```  
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
  
## 相依性屬性驗證  
 屬性通常會實作稱為驗證。 當嘗試變更屬性的值時，就會執行驗證邏輯。  
  
 不幸的是相依性屬性存取子不能包含任意的驗證程式碼。 相反地，您必須指定屬性註冊期間相依性屬性的驗證邏輯。  
  
 **X 不** 相依性屬性驗證邏輯放在屬性存取子。 相反地，通過驗證的回呼，以 `DependencyProperty.Register` 方法。  
  
## 相依性屬性變更告知  
 **X 不** 在相依性屬性存取子中實作變更通知邏輯。 相依性屬性有內建的變更通知功能，必須使用提供的變更通知回呼 <xref:System.Windows.PropertyMetadata>。  
  
## 相依性屬性值強制型轉  
 提供給屬性 setter 的值修改 setter 的屬性儲存區實際上在修改之前時，屬性強制型轉會發生。  
  
 **X 不** 實作相依性屬性存取子中的強制型轉邏輯。  
  
 相依性屬性有內建的強制型轉功能，並可供提供強制型轉回撥到 `PropertyMetadata`。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [常見的設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)