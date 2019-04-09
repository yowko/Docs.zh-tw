---
title: WF 中的集合活動
ms.date: 03/30/2017
ms.assetid: 2680c3e2-9902-4968-b98d-cab776103dbe
ms.openlocfilehash: 6e4b9ce6f967ba9405f55dbf5fd4708d3319b458
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133776"
---
# <a name="collection-activities-in-wf"></a><span data-ttu-id="1998e-102">WF 中的集合活動</span><span class="sxs-lookup"><span data-stu-id="1998e-102">Collection Activities in WF</span></span>
<span data-ttu-id="1998e-103">集合活動可用來處理工作流程中的集合物件。</span><span class="sxs-lookup"><span data-stu-id="1998e-103">Collection activities are used to work with collection objects in a workflow.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="1998e-104">已新增和移除集合中的項目、 測試集合中的項目存在以及清除集合的系統提供活動。</span><span class="sxs-lookup"><span data-stu-id="1998e-104">has system-provided activities for adding and removing items from a collection, testing for the existence of an item in a collection, and clearing a collection.</span></span> `ExistsInCollection` <span data-ttu-id="1998e-105">並`RemoveFromCollection`有<xref:System.Activities.OutArgument%601>型別的<xref:System.Boolean>，這會表示結果。</span><span class="sxs-lookup"><span data-stu-id="1998e-105">and `RemoveFromCollection` have an <xref:System.Activities.OutArgument%601> of type <xref:System.Boolean>, which indicates the result.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1998e-106">如果集合活動在設定基礎集合物件之前執行，便會擲回 <xref:System.InvalidOperationException> 與活動錯誤。</span><span class="sxs-lookup"><span data-stu-id="1998e-106">If a collection activity is executed before setting the underlying collection object, an <xref:System.InvalidOperationException> is thrown and the activity faults.</span></span>  
  
## <a name="collection-activities"></a><span data-ttu-id="1998e-107">集合活動</span><span class="sxs-lookup"><span data-stu-id="1998e-107">Collection activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="1998e-108">將項目加入指定集合。</span><span class="sxs-lookup"><span data-stu-id="1998e-108">Adds an item to a specified collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="1998e-109">清除指定集合中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="1998e-109">Clears all items from a specified collection.</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="1998e-110">如果項目存在於集合中，則傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="1998e-110">Returns `true` if an item exists in a collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="1998e-111">移除指定集合中的項目，若順利移除該項目，則傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="1998e-111">Removes an item from a specified collection and returns `true` if the item was successfully removed.</span></span>|  
  
## <a name="using-collection-activities"></a><span data-ttu-id="1998e-112">使用集合活動</span><span class="sxs-lookup"><span data-stu-id="1998e-112">Using collection activities</span></span>  
 <span data-ttu-id="1998e-113">下列程式碼範例示範如何與宣告為工作流程變數的集合互動。</span><span class="sxs-lookup"><span data-stu-id="1998e-113">The following code example demonstrates how to interact with a collection declared as a workflow variable.</span></span> <span data-ttu-id="1998e-114">所使用的集合是名為 <xref:System.Collections.Generic.List%601> 之 <xref:System.String> 物件的 `fruitList`。</span><span class="sxs-lookup"><span data-stu-id="1998e-114">The collection used is a <xref:System.Collections.Generic.List%601> of <xref:System.String> objects named `fruitList`.</span></span>  
  
```csharp  
Variable<ICollection<string>> fruitList = new Variable<ICollection<string>>  
{  
    Default = new VisualBasicValue<ICollection<string>>("New List(Of String) From {\"Apple\", \"Orange\"}"),  
    Name = "FruitList"  
};  
  
Variable<bool> result = new Variable<bool>  
{  
    Name = "Result"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { fruitList, result },  
  
    Activities =   
    {  
        new If  
        {  
            Condition = new ExistsInCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Then = new AddToCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Else = new RemoveFromCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Apple"  
            }  
        },  
  
        new RemoveFromCollection<string>  
        {  
            Collection = fruitList,  
            Item = "Apple",  
            Result = result  
        },  
        new If  
        {  
            Condition = result,  
            Then = new ClearCollection<string>  
            {  
                Collection = fruitList,  
            }  
        }  
    }  
};  
```  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
    <x:Reference>__ReferenceID1</x:Reference>  
  </Sequence.Variables>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <ExistsInCollection  
           x:TypeArguments="x:String"  
           Item="Pear">  
          <ExistsInCollection.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </ExistsInCollection.Result>  
          <InArgument  
             x:TypeArguments="scg:ICollection(x:String)">  
            <VariableValue  
               x:TypeArguments="scg:ICollection(x:String)">  
              <VariableValue.Result>  
                <OutArgument  
                   x:TypeArguments="scg:ICollection(x:String)" />  
              </VariableValue.Result>  
              <VariableValue.Variable>  
                <Variable  
                   x:TypeArguments="scg:ICollection(x:String)"  
                   x:Name="__ReferenceID0"  
                   Default="[New List(Of String) From {"Apple", "Orange"}]"  
                   Name="FruitList" />  
              </VariableValue.Variable>  
            </VariableValue>  
          </InArgument>  
        </ExistsInCollection>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <AddToCollection  
         x:TypeArguments="x:String"  
         Item="Pear">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </AddToCollection>  
    </If.Then>  
    <If.Else>  
      <RemoveFromCollection  
         x:TypeArguments="x:String"  
         Item="Apple"  
         Result="{x:Null}">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </RemoveFromCollection>  
    </If.Else>  
  </If>  
  <RemoveFromCollection  
     x:TypeArguments="x:String"  
     Item="Apple">  
    <RemoveFromCollection.Result>  
      <OutArgument  
         x:TypeArguments="x:Boolean">  
        <VariableReference  
           x:TypeArguments="x:Boolean">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(x:Boolean)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="x:Boolean"  
               x:Name="__ReferenceID1"  
               Name="Result" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </RemoveFromCollection.Result>  
    <InArgument  
       x:TypeArguments="scg:ICollection(x:String)">  
      <VariableValue  
         x:TypeArguments="scg:ICollection(x:String)"  
         Variable="{x:Reference __ReferenceID0}">  
        <VariableValue.Result>  
          <OutArgument  
             x:TypeArguments="scg:ICollection(x:String)" />  
        </VariableValue.Result>  
      </VariableValue>  
    </InArgument>  
  </RemoveFromCollection>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <VariableValue  
           x:TypeArguments="x:Boolean"  
           Variable="{x:Reference __ReferenceID1}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <ClearCollection  
         x:TypeArguments="x:String">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </ClearCollection>  
    </If.Then>  
  </If>  
</Sequence>  
```  
  
 <span data-ttu-id="1998e-115">上述程式碼範例也可以建立使用<xref:Microsoft.CSharp.Activities.CSharpValue%601>而不是</span><span class="sxs-lookup"><span data-stu-id="1998e-115">The above code samples can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of</span></span> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>  
  
```csharp
Variable<ICollection<string>> fruitList = new Variable<ICollection<string>>  
{  
    Default = new CSharpValue<ICollection<string>>("new List<String> From {\"Apple\", \"Orange\"};"),  
    Name = "FruitList"  
};  
  
Variable<bool> result = new Variable<bool>  
{  
    Name = "Result"  
};  
  
Activity wf = new Sequence  
{  
    Variables = { fruitList, result },  
  
    Activities =   
    {  
        new If  
        {  
            Condition = new ExistsInCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Then = new AddToCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Pear"  
            },  
            Else = new RemoveFromCollection<string>  
            {  
                Collection = fruitList,  
                Item = "Apple"  
            }  
        },  
  
        new RemoveFromCollection<string>  
        {  
            Collection = fruitList,  
            Item = "Apple",  
            Result = result  
        },  
        new If  
        {  
            Condition = result,  
            Then = new ClearCollection<string>  
            {  
                Collection = fruitList,  
            }  
        }  
    }  
};  
```  
  
```xml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
    <x:Reference>__ReferenceID1</x:Reference>  
  </Sequence.Variables>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <ExistsInCollection  
           x:TypeArguments="x:String"  
           Item="Pear">  
          <ExistsInCollection.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </ExistsInCollection.Result>  
          <InArgument  
             x:TypeArguments="scg:ICollection(x:String)">  
            <VariableValue  
               x:TypeArguments="scg:ICollection(x:String)">  
              <VariableValue.Result>  
                <OutArgument  
                   x:TypeArguments="scg:ICollection(x:String)" />  
              </VariableValue.Result>  
              <VariableValue.Variable>  
                <Variable  
                   x:TypeArguments="scg:ICollection(x:String)"  
                   x:Name="__ReferenceID0"  
                   Default="[new List<String> From {"Apple", "Orange"};]"  
                   Name="FruitList" />  
              </VariableValue.Variable>  
            </VariableValue>  
          </InArgument>  
        </ExistsInCollection>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <AddToCollection  
         x:TypeArguments="x:String"  
         Item="Pear">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </AddToCollection>  
    </If.Then>  
    <If.Else>  
      <RemoveFromCollection  
         x:TypeArguments="x:String"  
         Item="Apple"  
         Result="{x:Null}">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </RemoveFromCollection>  
    </If.Else>  
  </If>  
  <RemoveFromCollection  
     x:TypeArguments="x:String"  
     Item="Apple">  
    <RemoveFromCollection.Result>  
      <OutArgument  
         x:TypeArguments="x:Boolean">  
        <VariableReference  
           x:TypeArguments="x:Boolean">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(x:Boolean)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="x:Boolean"  
               x:Name="__ReferenceID1"  
               Name="Result" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </RemoveFromCollection.Result>  
    <InArgument  
       x:TypeArguments="scg:ICollection(x:String)">  
      <VariableValue  
         x:TypeArguments="scg:ICollection(x:String)"  
         Variable="{x:Reference __ReferenceID0}">  
        <VariableValue.Result>  
          <OutArgument  
             x:TypeArguments="scg:ICollection(x:String)" />  
        </VariableValue.Result>  
      </VariableValue>  
    </InArgument>  
  </RemoveFromCollection>  
  <If>  
    <If.Condition>  
      <InArgument  
         x:TypeArguments="x:Boolean">  
        <VariableValue  
           x:TypeArguments="x:Boolean"  
           Variable="{x:Reference __ReferenceID1}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="x:Boolean" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </If.Condition>  
    <If.Then>  
      <ClearCollection  
         x:TypeArguments="x:String">  
        <InArgument  
           x:TypeArguments="scg:ICollection(x:String)">  
          <VariableValue  
             x:TypeArguments="scg:ICollection(x:String)"  
             Variable="{x:Reference __ReferenceID0}">  
            <VariableValue.Result>  
              <OutArgument  
                 x:TypeArguments="scg:ICollection(x:String)" />  
            </VariableValue.Result>  
          </VariableValue>  
        </InArgument>  
      </ClearCollection>  
    </If.Then>  
  </If>  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1998e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1998e-116">See also</span></span>

- [<span data-ttu-id="1998e-117">使用命令式程式碼撰寫工作流程、活動和運算式</span><span class="sxs-lookup"><span data-stu-id="1998e-117">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
