---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614618"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a><span data-ttu-id="3efa8-101">WPF 在主要/詳細資料案例中顯示 ADO 資料時會變更主索引鍵</span><span class="sxs-lookup"><span data-stu-id="3efa8-101">WPF Changing a primary key when displaying ADO data in a Master/Detail scenario</span></span>

#### <a name="details"></a><span data-ttu-id="3efa8-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3efa8-102">Details</span></span>

<span data-ttu-id="3efa8-103">假設您有 `Order` 類型的 ADO 項目集合，並具有名為 &quot;OrderDetails&quot; 的關係，透過主索引鍵 &quot;OrderID&quot; 將它與 `Detail` 類型的項目集合相關聯。</span><span class="sxs-lookup"><span data-stu-id="3efa8-103">Suppose you have an ADO collection of items of type `Order`, with a relation named &quot;OrderDetails&quot; relating it to a collection of items of type `Detail` via the primary key &quot;OrderID&quot;.</span></span> <span data-ttu-id="3efa8-104">在 WPF 應用程式中，您可以將清單控制項繫結到指定訂單的詳細資料：</span><span class="sxs-lookup"><span data-stu-id="3efa8-104">In your WPF app, you can bind a list control to the details for a given order:</span></span>

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

<span data-ttu-id="3efa8-105">其中 DataContext 是 `Order`。</span><span class="sxs-lookup"><span data-stu-id="3efa8-105">where the DataContext is an `Order`.</span></span> <span data-ttu-id="3efa8-106">WPF 會取得屬性的值 `OrderDetails` -所有專案的集合 D， `Detail` 其 `OrderID` 符合 `OrderID` 主要專案的。</span><span class="sxs-lookup"><span data-stu-id="3efa8-106">WPF gets the value of the `OrderDetails` property - a collection D of all the `Detail` items whose `OrderID` matches the `OrderID` of the master item.</span></span> <span data-ttu-id="3efa8-107">當您變更主要專案的主鍵時，就會發生行為變更 `OrderID` 。</span><span class="sxs-lookup"><span data-stu-id="3efa8-107">The behavior change arises when you change the primary key `OrderID` of the master item.</span></span> <span data-ttu-id="3efa8-108">ADO 會自動變更 Details 集合中每個受影響記錄的 `OrderID` (也就是複製到集合 D 的項目)。</span><span class="sxs-lookup"><span data-stu-id="3efa8-108">ADO automatically changes the `OrderID` of each of the affected records in the Details collection (namely the ones copied into collection D).</span></span>  <span data-ttu-id="3efa8-109">但 D 會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="3efa8-109">But what happens to D?</span></span>

- <span data-ttu-id="3efa8-110">舊的行為：集合 D 已清除。</span><span class="sxs-lookup"><span data-stu-id="3efa8-110">Old behavior: Collection D is cleared.</span></span> <span data-ttu-id="3efa8-111">主要項目*不會*針對屬性 `OrderDetails` 引發變更通知。</span><span class="sxs-lookup"><span data-stu-id="3efa8-111">The master item does *not* raise a change notification for property `OrderDetails`.</span></span> <span data-ttu-id="3efa8-112">ListBox 會繼續使用集合 D (它現在是空的)。</span><span class="sxs-lookup"><span data-stu-id="3efa8-112">The ListBox continues to use collection D, which is now empty.</span></span>
- <span data-ttu-id="3efa8-113">新的行為：系統不會變更集合 D。</span><span class="sxs-lookup"><span data-stu-id="3efa8-113">New behavior:  Collection D is unchanged.</span></span> <span data-ttu-id="3efa8-114">其每個項目都會針對 `OrderID` 屬性引發變更通知。</span><span class="sxs-lookup"><span data-stu-id="3efa8-114">Each of its items raises a change notification for the `OrderID` property.</span></span> <span data-ttu-id="3efa8-115">ListBox 會繼續使用集合 D，並以新的 `OrderID` 來顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3efa8-115">The ListBox continues to use collection D, and displays the details with the new `OrderID`.</span></span> <span data-ttu-id="3efa8-116">WPF 會透過以不同的方式建立集合 D 來實作新的行為，也就是搭配將 `followParent` 引數設定為 `true` 來呼叫 ADO 方法 <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="3efa8-116">WPF implements the new behavior by creating collection D in a different way:  by calling the ADO method <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> with the `followParent` argument set to `true`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3efa8-117">建議</span><span class="sxs-lookup"><span data-stu-id="3efa8-117">Suggestion</span></span>

<span data-ttu-id="3efa8-118">應用程式能透過使用下列 AppContext 參數來取得新的行為。</span><span class="sxs-lookup"><span data-stu-id="3efa8-118">An app gets the new behavior by using the following AppContext switch.</span></span>

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

<span data-ttu-id="3efa8-119">針對以 .NET 4.7.1 或更舊版本為目標的應用程式，此參數的預設值為 `true` (舊行為)，而針對以 .NET 4.7.2 或更新版本為目標的應用程式，預設值則為 `false` (新行為)。</span><span class="sxs-lookup"><span data-stu-id="3efa8-119">The switch defaults to `true` (old behavior) for apps that target .NET 4.7.1 or below, and to `false` (new behavior) for apps that target .NET 4.7.2 or above.</span></span>

| <span data-ttu-id="3efa8-120">名稱</span><span class="sxs-lookup"><span data-stu-id="3efa8-120">Name</span></span>    | <span data-ttu-id="3efa8-121">值</span><span class="sxs-lookup"><span data-stu-id="3efa8-121">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3efa8-122">影響範圍</span><span class="sxs-lookup"><span data-stu-id="3efa8-122">Scope</span></span>   | <span data-ttu-id="3efa8-123">Minor</span><span class="sxs-lookup"><span data-stu-id="3efa8-123">Minor</span></span>       |
| <span data-ttu-id="3efa8-124">版本</span><span class="sxs-lookup"><span data-stu-id="3efa8-124">Version</span></span> | <span data-ttu-id="3efa8-125">4.7.2</span><span class="sxs-lookup"><span data-stu-id="3efa8-125">4.7.2</span></span>       |
| <span data-ttu-id="3efa8-126">類型</span><span class="sxs-lookup"><span data-stu-id="3efa8-126">Type</span></span>    | <span data-ttu-id="3efa8-127">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="3efa8-127">Retargeting</span></span> |
