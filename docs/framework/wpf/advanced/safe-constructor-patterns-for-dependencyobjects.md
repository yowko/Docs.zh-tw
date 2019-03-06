---
title: DependencyObject 的安全建構函式模式
ms.date: 03/30/2017
helpviewer_keywords:
- constructor patterns for dependency objects [WPF]
- dependency objects [WPF], constructor patterns
- FXCop tool [WPF]
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
ms.openlocfilehash: d963d9c8b7ddfba0c24fcb10ddf9cc45a2f4d0c5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363978"
---
# <a name="safe-constructor-patterns-for-dependencyobjects"></a><span data-ttu-id="822bc-102">DependencyObject 的安全建構函式模式</span><span class="sxs-lookup"><span data-stu-id="822bc-102">Safe Constructor Patterns for DependencyObjects</span></span>
<span data-ttu-id="822bc-103">一般而言，類別建構函式不應該呼叫回呼 (例如，虛擬方法或委派)，因為建構函式可以當成衍生類別之建構函式的基底初始化來呼叫。</span><span class="sxs-lookup"><span data-stu-id="822bc-103">Generally, class constructors should not call callbacks such as virtual methods or delegates, because constructors can be called as base initialization of constructors for a derived class.</span></span> <span data-ttu-id="822bc-104">進入虛擬項目，可能是在任何指定物件的未完成初始化狀態中完成的。</span><span class="sxs-lookup"><span data-stu-id="822bc-104">Entering the virtual might be done at an incomplete initialization state of any given object.</span></span> <span data-ttu-id="822bc-105">不過，屬性系統本身會在內部呼叫並公開回呼，以做為相依性屬性系統的一部分。</span><span class="sxs-lookup"><span data-stu-id="822bc-105">However, the property system itself calls and exposes callbacks internally, as part of the dependency property system.</span></span> <span data-ttu-id="822bc-106">使用相依性屬性值設定為簡單作業<xref:System.Windows.DependencyObject.SetValue%2A>呼叫可能會包含回呼某處中決定。</span><span class="sxs-lookup"><span data-stu-id="822bc-106">As simple an operation as setting a dependency property value with <xref:System.Windows.DependencyObject.SetValue%2A> call potentially includes a callback somewhere in the determination.</span></span> <span data-ttu-id="822bc-107">基於這個理由，在建構函式的主體內設定相依性屬性值時應特別小心，如果您的類型是用來做為基底類別，這可能就會發生問題。</span><span class="sxs-lookup"><span data-stu-id="822bc-107">For this reason, you should be careful when setting dependency property values within the body of a constructor, which can become problematic if your type is used as a base class.</span></span> <span data-ttu-id="822bc-108">沒有實作的特定模式<xref:System.Windows.DependencyObject>可避免與相依性屬性狀態和繼承回呼中，特定的問題所記載的建構函式。</span><span class="sxs-lookup"><span data-stu-id="822bc-108">There is a particular pattern for implementing <xref:System.Windows.DependencyObject> constructors that avoids specific problems with dependency property states and the inherent callbacks, which is documented here.</span></span>  
  
 
  
<a name="Property_System_Virtual_Methods"></a>   
## <a name="property-system-virtual-methods"></a><span data-ttu-id="822bc-109">屬性系統虛擬方法</span><span class="sxs-lookup"><span data-stu-id="822bc-109">Property System Virtual Methods</span></span>  
 <span data-ttu-id="822bc-110">下列虛擬方法或回呼可能在計算期間呼叫<xref:System.Windows.DependencyObject.SetValue%2A>呼叫，以設定相依性屬性值： <xref:System.Windows.ValidateValueCallback>， <xref:System.Windows.PropertyChangedCallback>， <xref:System.Windows.CoerceValueCallback>， <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>。</span><span class="sxs-lookup"><span data-stu-id="822bc-110">The following virtual methods or callbacks are potentially called during the computations of the <xref:System.Windows.DependencyObject.SetValue%2A> call that sets a dependency property value: <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.</span></span> <span data-ttu-id="822bc-111">這其中每一個虛擬方法或回呼，會在展開多樣化的 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 屬性系統和相依性屬性時具有特殊用途。</span><span class="sxs-lookup"><span data-stu-id="822bc-111">Each of these virtual methods or callbacks serves a particular purpose in expanding the versatility of the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] property system and dependency properties.</span></span> <span data-ttu-id="822bc-112">如需如何使用這些虛擬項目來自訂屬性值判斷的詳細資訊，請參閱[相依性屬性回呼和驗證](dependency-property-callbacks-and-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="822bc-112">For more information on how to use these virtuals to customize property value determination, see [Dependency Property Callbacks and Validation](dependency-property-callbacks-and-validation.md).</span></span>  
  
### <a name="fxcop-rule-enforcement-vs-property-system-virtuals"></a><span data-ttu-id="822bc-113">FXCop 規則強制與屬性系統虛擬項目</span><span class="sxs-lookup"><span data-stu-id="822bc-113">FXCop Rule Enforcement vs. Property System Virtuals</span></span>  
 <span data-ttu-id="822bc-114">如果您使用 Microsoft 工具 FXCop 做為建置流程的一部分，而且是衍生自從呼叫基底建構函式的特定 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 架構類別，或是在衍生類別中實作自己的相依性屬性，則您可能會遇到特殊的 FXCop 規則違規。</span><span class="sxs-lookup"><span data-stu-id="822bc-114">If you use the Microsoft tool FXCop as part of your build process, and you either derive from certain [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] framework classes calling the base constructor, or implement your own dependency properties on derived classes, you might encounter a particular FXCop rule violation.</span></span> <span data-ttu-id="822bc-115">此違規的名稱字串為：</span><span class="sxs-lookup"><span data-stu-id="822bc-115">The name string for this violation is:</span></span>  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 <span data-ttu-id="822bc-116">此規則屬於 FXCop 的預設公用規則集。</span><span class="sxs-lookup"><span data-stu-id="822bc-116">This is a rule that is part of the default public rule set for FXCop.</span></span> <span data-ttu-id="822bc-117">此規則可能會報告哪些內容，是透過相依性屬性系統來追蹤，此系統最終會呼叫相依性屬性系統虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="822bc-117">What this rule might be reporting is a trace through the dependency property system that eventually calls a dependency property system virtual method.</span></span> <span data-ttu-id="822bc-118">即使依照本主題中所述的建議建構函式模式來執行，此規則違規可能還會繼續出現，因此，您可能需要在 FXCop 規則集組態中停用或隱藏該規則。</span><span class="sxs-lookup"><span data-stu-id="822bc-118">This rule violation might continue to appear even after following the recommended constructor patterns documented in this topic, so you might need to disable or suppress that rule in your FXCop rule set configuration.</span></span>  
  
### <a name="most-issues-come-from-deriving-classes-not-using-existing-classes"></a><span data-ttu-id="822bc-119">大部分的問題均來自衍生類別，而非使用現有的類別</span><span class="sxs-lookup"><span data-stu-id="822bc-119">Most Issues Come From Deriving Classes, Not Using Existing Classes</span></span>  
 <span data-ttu-id="822bc-120">若接著會從中衍生您在其建構序列中使用虛擬方法實作的類別，就會發生此規則所報告的問題。</span><span class="sxs-lookup"><span data-stu-id="822bc-120">The issues reported by this rule occur when a class that you implement with virtual methods in its construction sequence is then derived from.</span></span> <span data-ttu-id="822bc-121">如果您密封類別，或是知道或強制您的類別將不會從中衍生，則此處所說明的考量和 FXCop 規則所引發的問題對您並不適用。</span><span class="sxs-lookup"><span data-stu-id="822bc-121">If you seal your class, or otherwise know or enforce that your class will not be derived from, the considerations explained here and the issues that motivated the FXCop rule do not apply to you.</span></span> <span data-ttu-id="822bc-122">不過，如果您正以有意使用它們當做基底類別 (例如，如果您正在建立範本) 或可擴展控制項程式庫集的方式來撰寫類別，則應遵循此處針對建構函式所建議的模式。</span><span class="sxs-lookup"><span data-stu-id="822bc-122">However, if you are authoring classes in such a way that they are intended to be used as base classes, for instance if you are creating templates, or an expandable control library set, you should follow the patterns recommended here for constructors.</span></span>  
  
### <a name="default-constructors-must-initialize-all-values-requested-by-callbacks"></a><span data-ttu-id="822bc-123">預設建構函式必須初始化回呼要求的所有值</span><span class="sxs-lookup"><span data-stu-id="822bc-123">Default Constructors Must Initialize All Values Requested By Callbacks</span></span>  
 <span data-ttu-id="822bc-124">您的類別覆寫或回呼 (回呼來自＜屬性系統虛擬項目＞一節中的清單) 所使用的任何執行個體成員，都必須在您的類別預設建構函式中加以初始化，即使那其中的一些值是透過非預設建構函式的參數，利用「實際」值來填滿。</span><span class="sxs-lookup"><span data-stu-id="822bc-124">Any instance members that are used by your class overrides or callbacks (the callbacks from the list in the Property System Virtuals section) must be initialized in your class default constructor, even if some of those values are filled by "real" values through parameters of the nondefault constructors.</span></span>  
  
 <span data-ttu-id="822bc-125">下列範例程式碼 (和後續範例) 是違反這項規則的虛擬 C# 範例，並將說明問題：</span><span class="sxs-lookup"><span data-stu-id="822bc-125">The following example code (and subsequent examples) is a pseudo-C# example that violates this rule and explains the problem:</span></span>  
  
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
  
 <span data-ttu-id="822bc-126">當應用程式程式碼呼叫 `new MyClass(objectvalue)` 時，這會呼叫預設建構函式和基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="822bc-126">When application code calls `new MyClass(objectvalue)`, this calls the default constructor and base class constructors.</span></span> <span data-ttu-id="822bc-127">然後它會設定`Property1 = object1`，它會呼叫虛擬方法`OnPropertyChanged`上擁有`MyClass` <xref:System.Windows.DependencyObject>。</span><span class="sxs-lookup"><span data-stu-id="822bc-127">Then it sets `Property1 = object1`, which calls the virtual method `OnPropertyChanged` on the owning `MyClass` <xref:System.Windows.DependencyObject>.</span></span>  <span data-ttu-id="822bc-128">覆寫是指尚未初始化的 `_myList`。</span><span class="sxs-lookup"><span data-stu-id="822bc-128">The override refers to `_myList`, which has not been initialized yet.</span></span>  
  
 <span data-ttu-id="822bc-129">避免這些問題的方法之一是，確定回呼只會使用其他相依性屬性，而且每個這類相依性屬性都已建立預設值做為其已註冊中繼資料的一部分。</span><span class="sxs-lookup"><span data-stu-id="822bc-129">One way to avoid these issues is to make sure that callbacks use only other dependency properties, and that each such dependency property has an established default value as part of its registered metadata.</span></span>  
  
<a name="Safe_Constructor_Patterns"></a>   
## <a name="safe-constructor-patterns"></a><span data-ttu-id="822bc-130">安全的建構函式模式</span><span class="sxs-lookup"><span data-stu-id="822bc-130">Safe Constructor Patterns</span></span>  
 <span data-ttu-id="822bc-131">若要在您的類別用來當做基底類別時，避免產生未完成初始化的風險，請遵循下列模式：</span><span class="sxs-lookup"><span data-stu-id="822bc-131">To avoid the risks of incomplete initialization if your class is used as a base class, follow these patterns:</span></span>  
  
#### <a name="default-constructors-calling-base-initialization"></a><span data-ttu-id="822bc-132">預設建構函式呼叫基底初始化</span><span class="sxs-lookup"><span data-stu-id="822bc-132">Default constructors calling base initialization</span></span>  
 <span data-ttu-id="822bc-133">實作這些呼叫基底預設值的建構函式：</span><span class="sxs-lookup"><span data-stu-id="822bc-133">Implement these constructors calling the base default:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-not-matching-any-base-signatures"></a><span data-ttu-id="822bc-134">非預設 (便捷) 建構函式，不符合任何基底簽章</span><span class="sxs-lookup"><span data-stu-id="822bc-134">Non-default (convenience) constructors, not matching any base signatures</span></span>  
 <span data-ttu-id="822bc-135">如果這些建構函式會在初始化期間使用參數來設定相依性屬性，請先呼叫您自己的類別預設建構函式進行初始化，接著使用參數來設定相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="822bc-135">If these constructors use the parameters to set dependency properties in the initialization, first call your own class default constructor for initialization, and then use the parameters to set dependency properties.</span></span> <span data-ttu-id="822bc-136">這些可能是您的類別所定義的相依性屬性或繼承自基底類別的相依性屬性，但在這任一種情況下，請使用下列模式：</span><span class="sxs-lookup"><span data-stu-id="822bc-136">These could either be dependency properties defined by your class, or dependency properties inherited from base classes, but in either case use the following pattern:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="non-default-convenience-constructors-which-do-match-base-signatures"></a><span data-ttu-id="822bc-137">非預設 (便捷) 建構函式，其符合任何基底簽章</span><span class="sxs-lookup"><span data-stu-id="822bc-137">Non-default (convenience) constructors, which do match base signatures</span></span>  
 <span data-ttu-id="822bc-138">不要使用同一個參數化來呼叫基底建構函式，而是再次呼叫您自己的類別預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="822bc-138">Instead of calling the base constructor with the same parameterization, again call your own class' default constructor.</span></span> <span data-ttu-id="822bc-139">請勿呼叫基底初始設定式；您應該改為呼叫 `this()`。</span><span class="sxs-lookup"><span data-stu-id="822bc-139">Do not call the base initializer; instead you should call `this()`.</span></span> <span data-ttu-id="822bc-140">然後使用傳遞的參數做為用來設定相關屬性的值，藉以重現原始的建構函式行為。</span><span class="sxs-lookup"><span data-stu-id="822bc-140">Then reproduce the original constructor behavior by using the passed parameters as values for setting the relevant properties.</span></span> <span data-ttu-id="822bc-141">使用原始的基底建構函式文件做為指引，來判斷要設定特定參數的屬性：</span><span class="sxs-lookup"><span data-stu-id="822bc-141">Use the original base constructor documentation for guidance in determining the properties that the particular parameters are intended to set:</span></span>  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### <a name="must-match-all-signatures"></a><span data-ttu-id="822bc-142">必須符合所有簽章</span><span class="sxs-lookup"><span data-stu-id="822bc-142">Must match all signatures</span></span>  
 <span data-ttu-id="822bc-143">在基底類型具有多個簽章的情況下，您必須刻意讓所有可能的簽章與您自己的建構函式實作相符，後者會使用在進一步設定屬性之前呼叫類別預設建構函式的建議模式。</span><span class="sxs-lookup"><span data-stu-id="822bc-143">For cases where the base type has multiple signatures, you must deliberately match all possible signatures with a constructor implementation of your own that uses the recommended pattern of calling the class default constructor before setting further properties.</span></span>  
  
#### <a name="setting-dependency-properties-with-setvalue"></a><span data-ttu-id="822bc-144">使用 SetValue 設定相依性屬性</span><span class="sxs-lookup"><span data-stu-id="822bc-144">Setting dependency properties with SetValue</span></span>  
 <span data-ttu-id="822bc-145">如果您要設定此屬性，沒有屬性設定方便起見，包裝函式，以及設定值，這些相同的模式適用於<xref:System.Windows.DependencyObject.SetValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="822bc-145">These same patterns apply if you are setting a property that does not have a wrapper for property setting convenience, and set values with <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="822bc-146">您呼叫<xref:System.Windows.DependencyObject.SetValue%2A>該通過建構函式參數也應該呼叫類別的預設建構函式進行初始化。</span><span class="sxs-lookup"><span data-stu-id="822bc-146">Your calls to <xref:System.Windows.DependencyObject.SetValue%2A> that pass through constructor parameters should also call the class' default constructor for initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="822bc-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="822bc-147">See also</span></span>
- [<span data-ttu-id="822bc-148">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="822bc-148">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="822bc-149">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="822bc-149">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="822bc-150">相依性屬性的安全性</span><span class="sxs-lookup"><span data-stu-id="822bc-150">Dependency Property Security</span></span>](dependency-property-security.md)
