---
title: 必要引數與多載群組
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: d7cfe00d93f1eede77bcda5881c63843722c9a17
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452897"
---
# <a name="required-arguments-and-overload-groups"></a><span data-ttu-id="8ee5e-102">必要引數與多載群組</span><span class="sxs-lookup"><span data-stu-id="8ee5e-102">Required Arguments and Overload Groups</span></span>
<span data-ttu-id="8ee5e-103">您可以設定活動，讓繫結活動所需的某些引數有效，以便用於執行。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-103">Activities can be configured so that certain arguments are required to be bound for the activity to be valid for execution.</span></span> <span data-ttu-id="8ee5e-104">`RequiredArgument` 屬性用於指出活動的特定引數是必要的，而 `OverloadGroup` 屬性則用於群組必要引數的分類。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-104">The `RequiredArgument` attribute is used to indicate that certain arguments on an activity are required and the `OverloadGroup` attribute is used to group categories of required arguments together.</span></span> <span data-ttu-id="8ee5e-105">透過使用屬性，活動作者可以提供簡單或複雜的活動驗證組態。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-105">By using the attributes, activity authors can provide simple or complex activity validation configurations.</span></span>  
  
## <a name="using-required-arguments"></a><span data-ttu-id="8ee5e-106">使用必要的引數</span><span class="sxs-lookup"><span data-stu-id="8ee5e-106">Using Required Arguments</span></span>  
 <span data-ttu-id="8ee5e-107">若要在活動中使用 `RequiredArgument` 屬性，請使用 <xref:System.Activities.RequiredArgumentAttribute> 指出所需的引數。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-107">To use the `RequiredArgument` attribute in an activity, indicate the desired arguments using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="8ee5e-108">在此範例中，會定義具有兩個必要引數的 `Add` 活動。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-108">In this example, an `Add` activity is defined that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="8ee5e-109">在 XAML 中，必要的引數也會使用 <xref:System.Activities.RequiredArgumentAttribute> 來表示。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-109">In XAML, required arguments are also indicated by using <xref:System.Activities.RequiredArgumentAttribute>.</span></span> <span data-ttu-id="8ee5e-110">在此範例中，`Add` 活動以三個引數來定義，並使用 <xref:System.Activities.Statements.Assign%601> 活動來執行加入作業。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-110">In this example the `Add` activity is defined by using three arguments and uses an <xref:System.Activities.Statements.Assign%601> activity to perform the add operation.</span></span>  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 <span data-ttu-id="8ee5e-111">如果使用該活動，而未繫結程序任一必要引數，就會傳回下列驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-111">If the activity is used and either of the required arguments is not bound the following validation error is returned.</span></span>  
  
 <span data-ttu-id="8ee5e-112">**未提供必要的活動引數 'Operand1' 的值。**</span><span class="sxs-lookup"><span data-stu-id="8ee5e-112">**Value for a required activity argument 'Operand1' was not supplied.**</span></span>  
> [!NOTE]
> <span data-ttu-id="8ee5e-113">如需檢查和處理驗證錯誤和警告的詳細資訊，請參閱 <<c0> [ 叫用活動驗證](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-113">For more information about checking for and handling validation errors and warnings, see [Invoking Activity Validation](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md).</span></span>  
  
## <a name="using-overload-groups"></a><span data-ttu-id="8ee5e-114">使用多載群組</span><span class="sxs-lookup"><span data-stu-id="8ee5e-114">Using Overload Groups</span></span>

<span data-ttu-id="8ee5e-115">多載群組提供方法，指出活動中哪些引數組合是有效的。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-115">Overload groups provide a method for indicating which combinations of arguments are valid in an activity.</span></span> <span data-ttu-id="8ee5e-116">引數會使用 <xref:System.Activities.OverloadGroupAttribute> 群組在一起。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-116">Arguments are grouped together by using <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="8ee5e-117">每個群組會給予所指定的名稱<xref:System.Activities.OverloadGroupAttribute>。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-117">Each group is given a name that is specified by the <xref:System.Activities.OverloadGroupAttribute>.</span></span> <span data-ttu-id="8ee5e-118">只有一組多載群組中的引數繫結時，活動才有效。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-118">The activity is valid when only one set of arguments in an overload group are bound.</span></span> <span data-ttu-id="8ee5e-119">在下列範例中，會定義 `CreateLocation` 類別。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-119">In the following example, a `CreateLocation` class is defined.</span></span>  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }                  
}  
```  
  
 <span data-ttu-id="8ee5e-120">這個活動的目的是要指定美國的地點。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-120">The objective of this activity is to specify a location in the US.</span></span> <span data-ttu-id="8ee5e-121">若要完成這項作業，活動的使用者可以使用三個引數群組的其中之一來指定地點。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-121">To do this, the user of the activity can specify the location using one of three groups of arguments.</span></span> <span data-ttu-id="8ee5e-122">為指定有效的引數組合，會定義三個多載群組。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-122">To specify the valid combinations of arguments, three overload groups are defined.</span></span> <span data-ttu-id="8ee5e-123">`G1` 包含 `Latitude` 和 `Longitude` 引數。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-123">`G1` contains the `Latitude` and `Longitude` arguments.</span></span> <span data-ttu-id="8ee5e-124">`G2` 包含 `Street`、`City` 和 `State`。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-124">`G2` contains `Street`, `City`, and `State`.</span></span> <span data-ttu-id="8ee5e-125">`G3` 包含 `Street` 和 `Zip`。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-125">`G3` contains `Street` and `Zip`.</span></span> <span data-ttu-id="8ee5e-126">`Name` 也是必要引數，但不是多載群組的一部分。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-126">`Name` is also a required argument, but it is not part of an overload group.</span></span> <span data-ttu-id="8ee5e-127">若要使這個活動有效，`Name` 必須與來自同一個多載群組的所有引數繫結在一起。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-127">For this activity to be valid, `Name` would have to be bound together with all of the arguments from one and only one overload group.</span></span>  
  
 <span data-ttu-id="8ee5e-128">下列範例中，在取自[資料庫存取活動](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)範例中，有兩個多載群組：`ConnectionString`和`ConfigFileSectionName`。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-128">In the following example, taken from the [Database Access Activities](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) sample, there are two overload groups: `ConnectionString` and `ConfigFileSectionName`.</span></span> <span data-ttu-id="8ee5e-129">若要讓此活動有效，必須繫結 `ProviderName` 和 `ConnectionString` 引數，或是繫結 `ConfigName` 引數，但不能同時使用這兩種方式。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-129">For this activity to be valid, either the `ProviderName` and `ConnectionString` arguments must be bound, or the `ConfigName` argument, but not both.</span></span>  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
 <span data-ttu-id="8ee5e-130">定義多載群組時：</span><span class="sxs-lookup"><span data-stu-id="8ee5e-130">When defining an overload group:</span></span>  
  
-   <span data-ttu-id="8ee5e-131">多載群組不得為其他多載群組的子集或對等的多載群組。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-131">An overload group cannot be a subset or an equivalent set of another overload group.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ee5e-132">這個規則只有一個例外。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-132">There is one exception to this rule.</span></span> <span data-ttu-id="8ee5e-133">如果多載群組是另一個多載群組的子集，且該子集只包含 `RequiredArgument` 是 `false` 的引數，則該多載群組是有效的。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-133">If an overload group is a subset of another overload group, and the subset contains only arguments where `RequiredArgument` is `false`, then the overload group is valid.</span></span>  
  
-   <span data-ttu-id="8ee5e-134">多載群組可以重疊，但是如果群組交集範圍內包含一個或兩個多載群組所需的全部引數，則會是錯誤。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-134">Overload groups can overlap but it is an error if the intersection of the groups contains all the required arguments of one or both of the overload groups.</span></span> <span data-ttu-id="8ee5e-135">在上一個範例中，`G2` 和 `G3` 多載群組是重疊的，但因為交集不包含這兩個群組之一或兩者的所有引數，所以這樣有效。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-135">In the previous example the `G2` and `G3` overload groups overlapped, but because the intersection did not contain all the arguments of one or both of the groups this was valid.</span></span>  
  
 <span data-ttu-id="8ee5e-136">繫結多載群組中的引數時：</span><span class="sxs-lookup"><span data-stu-id="8ee5e-136">When binding arguments in an overload group:</span></span>  
  
-   <span data-ttu-id="8ee5e-137">如果群組中所有的 `RequiredArgument` 引數已繫結，則將多載群組視為已繫結。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-137">An overload group is considered bound if all the `RequiredArgument` arguments in the group are bound.</span></span>  
  
-   <span data-ttu-id="8ee5e-138">如果群組沒有任何 `RequiredArgument` 引數，而且至少有一個引數已繫結，則將群組視為已繫結。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-138">If a group has zero `RequiredArgument` arguments and at least one argument bound, then the group is considered bound.</span></span>  
  
-   <span data-ttu-id="8ee5e-139">如果所有多載群組均未繫結，則會是驗證錯誤，除非有一個多載群組之中未包含任何 `RequiredArgument` 引數。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-139">It is a validation error if no overload groups are bound unless one overload group has no `RequiredArgument` arguments in it.</span></span>  
  
-   <span data-ttu-id="8ee5e-140">繫結多個多載群組 (也就是說，一個多載群組中所需的所有引數皆已繫結，而且其他多載群組中所有引數也已繫結) 是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="8ee5e-140">It is an error to have more than one overload group bound, that is, all required arguments in one overload group are bound and any argument in another overload group is also bound.</span></span>
