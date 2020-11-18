---
title: 相依性屬性
ms.date: 10/22/2008
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: c6cebd7c6c630af6a1a439b48faccad2aea74a91
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821368"
---
# <a name="dependency-properties"></a><span data-ttu-id="97244-102">相依性屬性</span><span class="sxs-lookup"><span data-stu-id="97244-102">Dependency Properties</span></span>
<span data-ttu-id="97244-103"> (DP) 的相依性屬性是一般屬性，它會將其值儲存在屬性存放區，而不是將它儲存在類型變數 (欄位) 中。</span><span class="sxs-lookup"><span data-stu-id="97244-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="97244-104">附加的相依性屬性是一種模型化為靜態 Get 和 Set 方法的相依性屬性，其代表描述物件與其容器之間關聯性的「屬性」 (例如， `Button` 容器上物件的位置 `Panel`) 。</span><span class="sxs-lookup"><span data-stu-id="97244-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="97244-105">如果您需要屬性來支援樣式、觸發程式、資料系結、動畫、動態資源和繼承等 WPF 功能，✔️提供相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="97244-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="97244-106">相依性屬性設計</span><span class="sxs-lookup"><span data-stu-id="97244-106">Dependency Property Design</span></span>
 <span data-ttu-id="97244-107">✔️在執行相依性 <xref:System.Windows.DependencyObject> 屬性時，會繼承自或其中一個子類型。</span><span class="sxs-lookup"><span data-stu-id="97244-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="97244-108">此類型提供非常有效率的屬性存放區執行，並自動支援 WPF 資料系結。</span><span class="sxs-lookup"><span data-stu-id="97244-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="97244-109">✔️確實提供一般 CLR 屬性和公用靜態唯讀欄位，以儲存每個相依性 <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> 屬性的實例。</span><span class="sxs-lookup"><span data-stu-id="97244-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="97244-110">✔️藉由呼叫實例方法和來執行相依性屬性 <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="97244-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="97244-111">✔️透過 suffixing 具有 "Property" 的屬性名稱，將相依性屬性靜態欄位命名。</span><span class="sxs-lookup"><span data-stu-id="97244-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="97244-112">❌ 請勿在程式碼中明確設定相依性屬性的預設值;請改為在中繼資料中設定這些專案。</span><span class="sxs-lookup"><span data-stu-id="97244-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="97244-113">如果您明確地設定屬性預設值，您可能會防止某個隱含的方法（例如樣式）設定該屬性。</span><span class="sxs-lookup"><span data-stu-id="97244-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="97244-114">❌ 請勿將程式碼放在標準程式碼以外的屬性存取子中，以存取靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="97244-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="97244-115">如果屬性是透過隱含方式（例如樣式）設定，則該程式碼不會執行，因為樣式會直接使用靜態欄位。</span><span class="sxs-lookup"><span data-stu-id="97244-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="97244-116">❌ 請勿使用相依性屬性來儲存安全的資料。</span><span class="sxs-lookup"><span data-stu-id="97244-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="97244-117">甚至可以公開存取私用相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="97244-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="97244-118">附加的相依性屬性設計</span><span class="sxs-lookup"><span data-stu-id="97244-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="97244-119">上一節所述的相依性屬性代表宣告類型的內建屬性;例如， `Text` 屬性是的屬性 `TextButton` ，它會宣告它。</span><span class="sxs-lookup"><span data-stu-id="97244-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="97244-120">特殊類型的相依性屬性是附加的相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="97244-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="97244-121">附加屬性的典型範例是 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="97244-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="97244-122">屬性代表按鈕的 (不是方格的) 資料行位置，但只有在該按鈕包含在方格中時才有關聯，因此它會依格線「附加」至按鈕。</span><span class="sxs-lookup"><span data-stu-id="97244-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

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

 <span data-ttu-id="97244-123">附加屬性的定義與一般相依性屬性的定義大致相同，不同之處在于存取子是以靜態 Get 和 Set 方法表示：</span><span class="sxs-lookup"><span data-stu-id="97244-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

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

## <a name="dependency-property-validation"></a><span data-ttu-id="97244-124">相依性屬性驗證</span><span class="sxs-lookup"><span data-stu-id="97244-124">Dependency Property Validation</span></span>
 <span data-ttu-id="97244-125">屬性通常會執行所謂的驗證。</span><span class="sxs-lookup"><span data-stu-id="97244-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="97244-126">當嘗試變更屬性的值時，就會執行驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="97244-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="97244-127">可惜的是，相依性屬性存取子不能包含任意驗證程式代碼。</span><span class="sxs-lookup"><span data-stu-id="97244-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="97244-128">相反地，必須在屬性註冊期間指定相依性屬性驗證邏輯。</span><span class="sxs-lookup"><span data-stu-id="97244-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="97244-129">❌ 請勿將相依性屬性驗證邏輯放在屬性的存取子中。</span><span class="sxs-lookup"><span data-stu-id="97244-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="97244-130">相反地，請將驗證回撥傳遞給 `DependencyProperty.Register` 方法。</span><span class="sxs-lookup"><span data-stu-id="97244-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="97244-131">相依性屬性變更通知</span><span class="sxs-lookup"><span data-stu-id="97244-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="97244-132">❌ 請勿在相依性屬性存取子中執行變更通知邏輯。</span><span class="sxs-lookup"><span data-stu-id="97244-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="97244-133">相依性屬性具有內建的變更通知功能，必須藉由提供變更通知回呼來使用 <xref:System.Windows.PropertyMetadata> 。</span><span class="sxs-lookup"><span data-stu-id="97244-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="97244-134">相依性屬性值強制型轉</span><span class="sxs-lookup"><span data-stu-id="97244-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="97244-135">在實際修改屬性存放區之前，setter 會修改指定給屬性 setter 的值時，就會發生屬性強制型轉。</span><span class="sxs-lookup"><span data-stu-id="97244-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="97244-136">❌ 請勿在相依性屬性存取子中執行強制邏輯。</span><span class="sxs-lookup"><span data-stu-id="97244-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="97244-137">相依性屬性具有內建的強制功能，可透過提供的強制回呼回呼來使用 `PropertyMetadata` 。</span><span class="sxs-lookup"><span data-stu-id="97244-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="97244-138">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="97244-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="97244-139">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="97244-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="97244-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="97244-140">See also</span></span>

- [<span data-ttu-id="97244-141">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="97244-141">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="97244-142">常見的設計模式</span><span class="sxs-lookup"><span data-stu-id="97244-142">Common Design Patterns</span></span>](common-design-patterns.md)
