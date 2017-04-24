---
title: "DependencyObject 的安全建構函式模式 | Microsoft Docs"
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
  - "相依性物件的建構函式模式"
  - "相依性物件, 建構函式模式"
  - "FXCop 工具"
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# DependencyObject 的安全建構函式模式
一般來說，類別建構函式不應呼叫像是虛擬方法或委派之類的回呼，因為建構函式可以呼叫做為衍生類別之建構函式的基底初始設定。  進入虛擬方法可在任何指定物件還在未完成初始設定的狀態時完成。  不過，屬性系統本身會在內部呼叫和公開回呼，以做為相依性屬性系統的一部分。  簡單如使用 <xref:System.Windows.DependencyObject.SetValue%2A> 呼叫設定相依性屬性的作業，都可能在決定的某個部分包含回呼。  因此，在建構函式主體內設定相依性屬性時應小心，如果將型別當做基底類別使用，就可能會發生問題。  有一種實作 <xref:System.Windows.DependencyObject> 建構函式的特殊模式可避免相依性屬性狀態和內建回呼的問題，這裡將說明此模式。  
  
   
  
<a name="Property_System_Virtual_Methods"></a>   
## 屬性系統虛擬方法  
 在計算設定相依性屬性值的 <xref:System.Windows.DependencyObject.SetValue%2A> 呼叫期間，可能會呼叫下列虛擬方法或回呼：<xref:System.Windows.ValidateValueCallback>、<xref:System.Windows.PropertyChangedCallback>、<xref:System.Windows.CoerceValueCallback>、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A>。  上述每一個虛擬方法或回呼在擴充 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統和相依性屬性多樣化功能方面都有其特定用途。  如需如何使用這些虛擬自訂屬性值決定的詳細資訊，請參閱[相依性屬性回呼和驗證](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)。  
  
### FXCop 規則強制執行和屬性系統虛擬的比較  
 如果您使用 Microsoft 工具 FXCop 做為建置程序的一部分，並從某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構類別衍生來呼叫基底建構函式，或在衍生類別上實作自己的相依性屬性，可能會違反特定 FXCop 規則。  這項違規的名稱字串為：  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 此規則屬於 FXCop 預設公用規則集的一部分。  此規則所報告的可能是透過相依性屬性系統 \(最終呼叫相依性屬性系統虛擬方法\) 所進行的追蹤。  即使依照本主題建議的建構函式模式，此項違規可能仍會出現，因此您可能需要在 FXCop 規則集組態中停用或限制該規則。  
  
### 問題多半來自於衍生類別，而非使用現有的類別  
 當您從使用虛擬方法在建構序列實作的類別衍生時，就會發生此規則所報告的問題。  如果您密封類別，或者知道或強制類別不得衍生，那麼這裡說明的考量和 FXCop 規則引發的問題將不適用於您。  不過，如果您撰寫的類別將當做基底類別使用，例如，如果建立樣板或可擴充的控制項程式庫集，請依照這裡所建議的建構函式模式。  
  
### 預設建構函式必須初始設定回呼要求的所有值  
 類別覆寫或回呼 \(＜屬性系統虛擬＞一節所列的回呼\) 所使用的任何執行個體成員都必須在類別預設建構函式中初始設定，即使部分值已透過非預設建構函式參數填入「實際」值。  
  
 下列範例程式碼 \(以及其後的範例\) 是虛擬 C\# 範例，它違反了此規則並說明問題所在：  
  
```  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 當應用程式的程式碼呼叫 `new MyClass(objectvalue)` 時，這會呼叫預設建構函式和基底類別建構函式。  然後它會設定 `Property1 = object1`，這會在主控 `MyClass` <xref:System.Windows.DependencyObject> 上呼叫虛擬方法 `OnPropertyChanged`。  覆寫會參考尚未初始設定的 `_myList`。  
  
 避免這些問題的一個方法是確定回呼只使用其他相依性屬性，而且每個相依性屬性在其註冊的中繼資料都有已建立的預設值。  
  
<a name="Safe_Constructor_Patterns"></a>   
## 安全建構函式模式  
 若要避免類別當做基底類別使用時有未完成初始設定的風險，請依循下列模式：  
  
#### 預設建構函式呼叫基底初始設定  
 實作這些呼叫基底預設值的建構函式：  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### 非預設 \(便捷\) 建構函式，未符合任何基底簽章  
 如果這些建構函式使用參數在初始設定中設定相依性屬性，請先呼叫您自己的類別預設建構函式來進行初始設定，再使用參數設定相依性屬性。  這些可能是您的類別定義的相依性屬性，或從基底類別繼承的相依性屬性，不過無論在哪種情況下，請使用下列模式：  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### 非預設 \(便捷\) 建構函式，符合基底簽章  
 請不要使用相同參數化呼叫基底建構函式，而是再次呼叫您自己類別的預設建構函式。  請不要呼叫基底初始設定式，而應呼叫 `this()`。  然後使用傳遞的參數做為設定相關屬性的值，藉此重現原始的建構函式行為。  請使用原始基底建構函式文件做為方針，來判斷應使用特定參數設定的屬性：  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### 必須符合所有簽章  
 針對基底型別有多個簽章的情況，您必須使用自己的建構函式實作 \(使用建議的呼叫類別預設建構函式模式\) 符合所有可能的簽章，再設定進一步的屬性。  
  
#### 使用 SetValue 設定相依性屬性  
 如果您設定的屬性沒有方便設定屬性的包裝函式，而使用 <xref:System.Windows.DependencyObject.SetValue%2A> 設定值，也同樣適用上述模式。  透過建構函式參數傳遞的 <xref:System.Windows.DependencyObject.SetValue%2A> 呼叫，也應呼叫類別的預設建構函式來進行初始設定。  
  
## 請參閱  
 [自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [相依性屬性的安全性](../../../../docs/framework/wpf/advanced/dependency-property-security.md)