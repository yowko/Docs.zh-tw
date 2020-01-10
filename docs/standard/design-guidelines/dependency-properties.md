---
title: 相依性屬性
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: bd12d05dbba133503778e6df3cd0e6c3e5689d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709487"
---
# <a name="dependency-properties"></a><span data-ttu-id="9eba5-102">相依性屬性</span><span class="sxs-lookup"><span data-stu-id="9eba5-102">Dependency Properties</span></span>
<span data-ttu-id="9eba5-103">相依性屬性（DP）是將其值儲存在屬性存放區中的一般屬性，而不是將它儲存在類型變數（欄位）中，例如。</span><span class="sxs-lookup"><span data-stu-id="9eba5-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>  
  
 <span data-ttu-id="9eba5-104">附加的相依性屬性是一種以靜態 Get 和 Set 方法模型化的相依性屬性，其代表描述物件及其容器之間關聯性的「屬性」（例如，在 `Panel` 容器上 `Button` 物件的位置）。</span><span class="sxs-lookup"><span data-stu-id="9eba5-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>  
  
 <span data-ttu-id="9eba5-105">如果您需要屬性來支援樣式、觸發程式、資料系結、動畫、動態資源和繼承等 WPF 功能，則**✓**會提供相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9eba5-105">**✓ DO** provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>  
  
## <a name="dependency-property-design"></a><span data-ttu-id="9eba5-106">相依性屬性設計</span><span class="sxs-lookup"><span data-stu-id="9eba5-106">Dependency Property Design</span></span>  
 <span data-ttu-id="9eba5-107">在執行相依性屬性時， **✓ DO**會繼承自 <xref:System.Windows.DependencyObject>或它的其中一個子類型。</span><span class="sxs-lookup"><span data-stu-id="9eba5-107">**✓ DO** inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="9eba5-108">型別提供非常有效率的屬性存放區執行，並自動支援 WPF 資料系結。</span><span class="sxs-lookup"><span data-stu-id="9eba5-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>  
  
 <span data-ttu-id="9eba5-109">**✓ DO**提供一般 CLR 屬性和公用靜態唯讀欄位，以儲存每個相依性屬性的 <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> 實例。</span><span class="sxs-lookup"><span data-stu-id="9eba5-109">**✓ DO** provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>  
  
 <span data-ttu-id="9eba5-110">**✓**會藉由呼叫實例方法 <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> 和 <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>來執行相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9eba5-110">**✓ DO** implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9eba5-111">**✓ DO**藉由 suffixing 具有 "property" 屬性的屬性名稱，來命名相依性屬性靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="9eba5-111">**✓ DO** name the dependency property static field by suffixing the name of the property with "Property."</span></span>  
  
 <span data-ttu-id="9eba5-112">**X 不會**在程式碼中明確設定相依性屬性的預設值;請改為在中繼資料中設定它們。</span><span class="sxs-lookup"><span data-stu-id="9eba5-112">**X DO NOT** set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>  
  
 <span data-ttu-id="9eba5-113">如果您明確地設定屬性預設值，您可能會防止某個隱含的方式設定該屬性，例如樣式。</span><span class="sxs-lookup"><span data-stu-id="9eba5-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>  
  
 <span data-ttu-id="9eba5-114">**X 不會**將程式碼放在標準程式碼以外的屬性存取子中，以存取靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="9eba5-114">**X DO NOT** put code in the property accessors other than the standard code to access the static field.</span></span>  
  
 <span data-ttu-id="9eba5-115">如果屬性是以隱含方式設定（例如樣式），則該程式碼將不會執行，因為樣式會直接使用靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="9eba5-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>  
  
 <span data-ttu-id="9eba5-116">**X**不使用相依性屬性來儲存安全的資料。</span><span class="sxs-lookup"><span data-stu-id="9eba5-116">**X DO NOT** use dependency properties to store secure data.</span></span> <span data-ttu-id="9eba5-117">甚至可以公開存取私用相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9eba5-117">Even private dependency properties can be accessed publicly.</span></span>  
  
## <a name="attached-dependency-property-design"></a><span data-ttu-id="9eba5-118">附加的相依性屬性設計</span><span class="sxs-lookup"><span data-stu-id="9eba5-118">Attached Dependency Property Design</span></span>  
 <span data-ttu-id="9eba5-119">上一節所述的相依性屬性代表宣告類型的內建屬性。例如，`Text` 屬性是 `TextButton`的屬性，其會將其宣告。</span><span class="sxs-lookup"><span data-stu-id="9eba5-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="9eba5-120">特殊類型的相依性屬性是附加的相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9eba5-120">A special kind of dependency property is the attached dependency property.</span></span>  
  
 <span data-ttu-id="9eba5-121">附加屬性的典型範例是 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9eba5-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9eba5-122">屬性代表按鈕的（而不是方格的）資料行位置，但只有在按鈕包含在方格中，而且它是「附加」至按鈕 by 格線時才相關。</span><span class="sxs-lookup"><span data-stu-id="9eba5-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>  
  
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
  
 <span data-ttu-id="9eba5-123">附加屬性的定義與一般相依性屬性大致相似，不同之處在于存取子是以靜態 Get 和 Set 方法來表示：</span><span class="sxs-lookup"><span data-stu-id="9eba5-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>  
  
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
  
## <a name="dependency-property-validation"></a><span data-ttu-id="9eba5-124">相依性屬性驗證</span><span class="sxs-lookup"><span data-stu-id="9eba5-124">Dependency Property Validation</span></span>  
 <span data-ttu-id="9eba5-125">屬性通常會執行所謂的驗證。</span><span class="sxs-lookup"><span data-stu-id="9eba5-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="9eba5-126">當嘗試變更屬性的值時，就會執行驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="9eba5-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>  
  
 <span data-ttu-id="9eba5-127">可惜的是，相依性屬性存取子不能包含任意驗證程式代碼。</span><span class="sxs-lookup"><span data-stu-id="9eba5-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="9eba5-128">相反地，在屬性註冊期間，必須指定相依性屬性驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="9eba5-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>  
  
 <span data-ttu-id="9eba5-129">**X 不會**將相依性屬性驗證邏輯放在屬性的存取子中。</span><span class="sxs-lookup"><span data-stu-id="9eba5-129">**X DO NOT** put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="9eba5-130">相反地，請將驗證回呼傳遞給 `DependencyProperty.Register` 方法。</span><span class="sxs-lookup"><span data-stu-id="9eba5-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>  
  
## <a name="dependency-property-change-notifications"></a><span data-ttu-id="9eba5-131">相依性屬性變更通知</span><span class="sxs-lookup"><span data-stu-id="9eba5-131">Dependency Property Change Notifications</span></span>  
 <span data-ttu-id="9eba5-132">**X 不會**在相依性屬性存取子中執行變更通知邏輯。</span><span class="sxs-lookup"><span data-stu-id="9eba5-132">**X DO NOT** implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="9eba5-133">相依性屬性具有內建變更通知功能，必須透過提供 <xref:System.Windows.PropertyMetadata>的變更通知回呼來使用。</span><span class="sxs-lookup"><span data-stu-id="9eba5-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>  
  
## <a name="dependency-property-value-coercion"></a><span data-ttu-id="9eba5-134">相依性屬性值強制型轉</span><span class="sxs-lookup"><span data-stu-id="9eba5-134">Dependency Property Value Coercion</span></span>  
 <span data-ttu-id="9eba5-135">當 setter 在實際修改屬性存放區之前修改了指定給屬性 setter 的值時，就會發生屬性強制型轉。</span><span class="sxs-lookup"><span data-stu-id="9eba5-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>  
  
 <span data-ttu-id="9eba5-136">**X 不會**在相依性屬性存取子中執行強制型轉邏輯。</span><span class="sxs-lookup"><span data-stu-id="9eba5-136">**X DO NOT** implement coercion logic in dependency property accessors.</span></span>  
  
 <span data-ttu-id="9eba5-137">相依性屬性具有內建強制型轉功能，而且可以藉由提供 `PropertyMetadata`的強制型轉回呼來使用。</span><span class="sxs-lookup"><span data-stu-id="9eba5-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>  
  
 <span data-ttu-id="9eba5-138">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="9eba5-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9eba5-139">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="9eba5-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eba5-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="9eba5-140">See also</span></span>

- [<span data-ttu-id="9eba5-141">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="9eba5-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="9eba5-142">一般設計模式</span><span class="sxs-lookup"><span data-stu-id="9eba5-142">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)
