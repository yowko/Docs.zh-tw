---
title: 相依性屬性
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e5ab558149615128f6d8cb0a68bf7f70e7006b79
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="dependency-properties"></a><span data-ttu-id="6fba5-102">相依性屬性</span><span class="sxs-lookup"><span data-stu-id="6fba5-102">Dependency Properties</span></span>
<span data-ttu-id="6fba5-103">相依性屬性 (DP) 是將其值儲存在屬性存放區，而不是儲存在類型變數 （欄位），例如的一般屬性。</span><span class="sxs-lookup"><span data-stu-id="6fba5-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="6fba5-104">附加的相依性屬性是一種相依性屬性模型化成靜態代表 「 屬性 」 描述的物件和其容器之間的關聯性的 Get 和 Set 方法 (例如，位置`Button`物件上`Panel`容器）。</span><span class="sxs-lookup"><span data-stu-id="6fba5-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="6fba5-105">**✓ 不要**提供的相依性屬性，如果您需要支援 WPF 功能，例如樣式、 觸發程序、 資料繫結、 動畫、 動態的資源和繼承的屬性。</span><span class="sxs-lookup"><span data-stu-id="6fba5-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="6fba5-106">相依性屬性的設計</span><span class="sxs-lookup"><span data-stu-id="6fba5-106">Dependency Property Design</span></span>  
 <span data-ttu-id="6fba5-107">**✓ 不要**繼承自<xref:System.Windows.DependencyObject>，或其中一個它的子類型，實作相依性屬性時。</span><span class="sxs-lookup"><span data-stu-id="6fba5-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="6fba5-108">此類型提供 una implementación muy eficaz 屬性存放區，會自動支援 WPF 資料繫結。</span><span class="sxs-lookup"><span data-stu-id="6fba5-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="6fba5-109">**✓ 不要**提供規則的 CLR 屬性和公用靜態唯讀欄位中儲存的執行個體<xref:System.Windows.DependencyProperty?displayProperty=nameWithType>每一個相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="6fba5-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="6fba5-110">**✓ 不要**呼叫執行個體方法來實作相依性屬性<xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType>和<xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6fba5-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6fba5-111">**✓ 不要**藉由使用 「 屬性 」。 屬性名稱的尾碼名稱相依性屬性的靜態欄位</span><span class="sxs-lookup"><span data-stu-id="6fba5-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="6fba5-112">**X 不**程式碼中明確設定相依性屬性的預設值，則將它們設定在中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6fba5-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="6fba5-113">如果您明確設定屬性的預設值，您可能會讓該屬性從某些隱含的方式，例如樣式設定。</span><span class="sxs-lookup"><span data-stu-id="6fba5-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="6fba5-114">**X 不**放置在屬性存取子標準的程式碼以外，若要存取的靜態欄位的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6fba5-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="6fba5-115">程式碼將不會執行此屬性設定隱含的方式，例如樣式，如果因為樣式直接使用靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="6fba5-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="6fba5-116">**X 不**使用相依性屬性來儲存資料的安全。</span><span class="sxs-lookup"><span data-stu-id="6fba5-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="6fba5-117">可公開存取甚至私用相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="6fba5-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="6fba5-118">附加的相依性屬性的設計</span><span class="sxs-lookup"><span data-stu-id="6fba5-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="6fba5-119">上一節中所述的相依性屬性代表宣告的類型; 內建屬性例如，`Text`屬性是屬性的`TextButton`，其中宣告它。</span><span class="sxs-lookup"><span data-stu-id="6fba5-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="6fba5-120">一種特殊的相依性屬性是附加的相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="6fba5-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="6fba5-121">附加屬性的典型的範例是<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="6fba5-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6fba5-122">此屬性代表按鈕的 （不方格的） 資料行位置，但是只有相關如果按鈕包含在方格中，因此它 「 附加 」 到按鈕的方格。</span><span class="sxs-lookup"><span data-stu-id="6fba5-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
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
  
 <span data-ttu-id="6fba5-123">附加屬性的定義看起來大部分的一般相依性屬性的不同之處在於存取子都由靜態的 Get 和 Set 方法：</span><span class="sxs-lookup"><span data-stu-id="6fba5-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
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
  
## <a name="dependency-property-validation"></a><span data-ttu-id="6fba5-124">相依性屬性驗證</span><span class="sxs-lookup"><span data-stu-id="6fba5-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="6fba5-125">屬性通常會實作稱為驗證。</span><span class="sxs-lookup"><span data-stu-id="6fba5-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="6fba5-126">當嘗試變更屬性的值時，就會執行驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="6fba5-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="6fba5-127">不幸的是相依性屬性存取子不能包含任意的驗證程式碼。</span><span class="sxs-lookup"><span data-stu-id="6fba5-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="6fba5-128">相反地，相依性屬性的驗證邏輯，需要屬性登錄期間指定。</span><span class="sxs-lookup"><span data-stu-id="6fba5-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="6fba5-129">**X 不**放在屬性存取子的相依性屬性的驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="6fba5-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="6fba5-130">相反地，通過驗證回呼，以`DependencyProperty.Register`方法。</span><span class="sxs-lookup"><span data-stu-id="6fba5-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="6fba5-131">相依性屬性的變更告知</span><span class="sxs-lookup"><span data-stu-id="6fba5-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="6fba5-132">**X 不**在相依性屬性存取子實作變更通知邏輯。</span><span class="sxs-lookup"><span data-stu-id="6fba5-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="6fba5-133">相依性屬性具有內建的變更通知的一項功能，必須使用藉由提供變更通知回呼<xref:System.Windows.PropertyMetadata>。</span><span class="sxs-lookup"><span data-stu-id="6fba5-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="6fba5-134">相依性屬性的值強制型轉</span><span class="sxs-lookup"><span data-stu-id="6fba5-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="6fba5-135">屬性的強制型轉會發生時實際修改的屬性存放區之前 setter 修改該值提供給屬性 setter。</span><span class="sxs-lookup"><span data-stu-id="6fba5-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="6fba5-136">**X 不**強制型轉邏輯實作相依性屬性存取子中。</span><span class="sxs-lookup"><span data-stu-id="6fba5-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="6fba5-137">相依性屬性有內建的強制型轉功能，並可供提供強制型轉回撥到`PropertyMetadata`。</span><span class="sxs-lookup"><span data-stu-id="6fba5-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="6fba5-138">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="6fba5-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6fba5-139">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="6fba5-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fba5-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fba5-140">See Also</span></span>  
 [<span data-ttu-id="6fba5-141">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="6fba5-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="6fba5-142">一般設計模式</span><span class="sxs-lookup"><span data-stu-id="6fba5-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)
