---
title: 必要引數與多載群組
ms.date: 03/30/2017
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
ms.openlocfilehash: 794a0a531fbd26d9e4242d40be5147ab41547192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517556"
---
# <a name="required-arguments-and-overload-groups"></a>必要引數與多載群組
您可以設定活動，讓繫結活動所需的某些引數有效，以便用於執行。 `RequiredArgument` 屬性用於指出活動的特定引數是必要的，而 `OverloadGroup` 屬性則用於群組必要引數的分類。 透過使用屬性，活動作者可以提供簡單或複雜的活動驗證組態。  
  
## <a name="using-required-arguments"></a>使用必要的引數  
 若要在活動中使用 `RequiredArgument` 屬性，請使用 <xref:System.Activities.RequiredArgumentAttribute> 指出所需的引數。 在此範例中，會定義具有兩個必要引數的 `Add` 活動。  
  
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
  
 在 XAML 中，必要的引數也會使用 <xref:System.Activities.RequiredArgumentAttribute> 來表示。 在此範例中，`Add` 活動以三個引數來定義，並使用 <xref:System.Activities.Statements.Assign%601> 活動來執行加入作業。  
  
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
  
 如果使用該活動，而未繫結程序任一必要引數，就會傳回下列驗證錯誤。  
  
 **未提供必要的活動引數 'Operand1' 的值。**  
> [!NOTE]
>  如需檢查和處理驗證錯誤和警告的相關詳細資訊，請參閱[叫用活動驗證](../../../docs/framework/windows-workflow-foundation/invoking-activity-validation.md)。  
  
## <a name="using-overload-groups"></a>使用多載群組  
 多載群組提供方法，指出活動中哪些引數組合是有效的。 引數會使用 <xref:System.Activities.OverloadGroupAttribute> 群組在一起。 每個群組會擁有一個由 <xref:System.Activities.OverloadGroupAttribute> 所指定的名稱。唯有繫結多載群組中的一組引數時，活動才有效。 在下列範例中，取自[OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md)範例中，`CreateLocation`類別定義。  
  
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
  
 這個活動的目的是要指定美國的地點。 若要完成這項作業，活動的使用者可以使用三個引數群組的其中之一來指定地點。 為指定有效的引數組合，會定義三個多載群組。 `G1` 包含 `Latitude` 和 `Longitude` 引數。 `G2` 包含 `Street`、`City` 和 `State`。 `G3` 包含 `Street` 和 `Zip`。 `Name` 也是必要引數，但不是多載群組的一部分。 若要使這個活動有效，`Name` 必須與來自同一個多載群組的所有引數繫結在一起。  
  
 在下列範例中，取自[資料庫存取活動](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md)範例有兩個多載群組：`ConnectionString`和`ConfigFileSectionName`。 若要讓此活動有效，必須繫結 `ProviderName` 和 `ConnectionString` 引數，或是繫結 `ConfigName` 引數，但不能同時使用這兩種方式。  
  
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
  
 定義多載群組時：  
  
-   多載群組不得為其他多載群組的子集或對等的多載群組。  
  
    > [!NOTE]
    >  這個規則只有一個例外。 如果多載群組是另一個多載群組的子集，且該子集只包含 `RequiredArgument` 是 `false` 的引數，則該多載群組是有效的。  
  
-   多載群組可以重疊，但是如果群組交集範圍內包含一個或兩個多載群組所需的全部引數，則會是錯誤。 在上一個範例中，`G2` 和 `G3` 多載群組是重疊的，但因為交集不包含這兩個群組之一或兩者的所有引數，所以這樣有效。  
  
 繫結多載群組中的引數時：  
  
-   如果群組中所有的 `RequiredArgument` 引數已繫結，則將多載群組視為已繫結。  
  
-   如果群組沒有任何 `RequiredArgument` 引數，而且至少有一個引數已繫結，則將群組視為已繫結。  
  
-   如果所有多載群組均未繫結，則會是驗證錯誤，除非有一個多載群組之中未包含任何 `RequiredArgument` 引數。  
  
-   繫結多個多載群組 (也就是說，一個多載群組中所需的所有引數皆已繫結，而且其他多載群組中所有引數也已繫結) 是錯誤的。
