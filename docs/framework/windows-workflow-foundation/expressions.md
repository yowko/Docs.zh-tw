---
title: Expressions1
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18c64daca1532bb626a59e5f01528e207e6b6b87
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="expressions"></a><span data-ttu-id="012fd-102">運算式</span><span class="sxs-lookup"><span data-stu-id="012fd-102">Expressions</span></span>
<span data-ttu-id="012fd-103">Windows Workflow Foundation (WF) 運算式會傳回結果的任何活動。</span><span class="sxs-lookup"><span data-stu-id="012fd-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="012fd-104">所有運算式活動會間接自 <xref:System.Activities.Activity%601> 衍生，其包含名為 <xref:System.Activities.OutArgument> 的 <xref:System.Activities.Activity%601.Result%2A> 做為活動的傳回值。</span><span class="sxs-lookup"><span data-stu-id="012fd-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="012fd-105"> 隨附範圍廣大的運算式活動，包括簡單的活動 (例如 <xref:System.Activities.Expressions.VariableValue%601> 和 <xref:System.Activities.Expressions.VariableReference%601>，可透過運算子活動存取單一工作流程變數) 及複雜的活動 (例如 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>，可存取完整範圍的 Visual Basic 語言以產生結果)。</span><span class="sxs-lookup"><span data-stu-id="012fd-105"> ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="012fd-106">其他運算式活動可從 <xref:System.Activities.CodeActivity%601> 或 <xref:System.Activities.NativeActivity%601> 來衍生建立。</span><span class="sxs-lookup"><span data-stu-id="012fd-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>  
  
## <a name="using-expressions"></a><span data-ttu-id="012fd-107">使用運算式</span><span class="sxs-lookup"><span data-stu-id="012fd-107">Using Expressions</span></span>  
 <span data-ttu-id="012fd-108">工作流程設計工具會將 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 用於 Visual Basic 專案中的所有運算式，並將 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 和 <xref:Microsoft.CSharp.Activities.CSharpReference%601> 用於 C# 工作流程專案中的運算式。</span><span class="sxs-lookup"><span data-stu-id="012fd-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="012fd-109">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中已導入工作流程專案中的 C# 運算式支援。</span><span class="sxs-lookup"><span data-stu-id="012fd-109">Support for C# expressions in workflow projects was introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="012fd-110">如需詳細資訊，請參閱[C# 運算式](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="012fd-110">For more information, see [C# Expressions](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).</span></span>  
  
 <span data-ttu-id="012fd-111">由設計工具產生的工作流程會儲存為 XAML，其中會以方括號括住運算式，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="012fd-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>  
  
```xml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:Int32" Default="1" Name="a" />  
    <Variable x:TypeArguments="x:Int32" Default="2" Name="b" />  
    <Variable x:TypeArguments="x:Int32" Default="3" Name="c" />  
    <Variable x:TypeArguments="x:Int32" Default="0" Name="r" />  
  </Sequence.Variables>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[r]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[a + b + c]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Sequence>  
```  
  
 <span data-ttu-id="012fd-112">當以程式碼定義工作流程時，可使用任何運算式活動。</span><span class="sxs-lookup"><span data-stu-id="012fd-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="012fd-113">下列範例顯示運算子活動新增三個數字的複合用法。</span><span class="sxs-lookup"><span data-stu-id="012fd-113">The following example shows the usage of a composition of operator activities to add three numbers.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new Add<int, int, int> {  
                    Left = new Add<int, int, int> {  
                        Left = new InArgument<int>(a),  
                        Right = new InArgument<int>(b)  
                    },  
                    Right = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 <span data-ttu-id="012fd-114">相同的工作流程可使用 C# lambda 運算式更簡潔地表示，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="012fd-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>((ctx) => a.Get(ctx) + b.Get(ctx) + c.Get(ctx))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="012fd-115">工作流程也可以使用 Visual Basic 運算式活動表示，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="012fd-115">The workflow can also be expressed by using Visual Basic expression activities, as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int>(new VisualBasicValue<int>("a + b + c"))  
        }  
    }  
};  
```  
  
## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="012fd-116">使用自訂運算式活動延伸可用的運算式</span><span class="sxs-lookup"><span data-stu-id="012fd-116">Extending Available Expressions with Custom Expression Activities</span></span>  
 <span data-ttu-id="012fd-117">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中的運算式可延伸，以便建立其他的運算式活動。</span><span class="sxs-lookup"><span data-stu-id="012fd-117">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="012fd-118">下列程式碼範例示範會傳回三個整數值加總的活動。</span><span class="sxs-lookup"><span data-stu-id="012fd-118">The following example shows an activity that returns a sum of three integer values.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Activities;  
  
namespace ExpressionsDemo  
{  
    public sealed class AddThreeValues : CodeActivity<int>  
    {  
        public InArgument<int> Value1 { get; set; }  
        public InArgument<int> Value2 { get; set; }  
        public InArgument<int> Value3 { get; set; }  
  
        protected override int Execute(CodeActivityContext context)  
        {  
            return Value1.Get(context) +   
                   Value2.Get(context) +   
                   Value3.Get(context);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="012fd-119">您可以使用這個新活動重新寫入先前新增三個值的工作流程，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="012fd-119">With this new activity you can rewrite the previous workflow that added three values as shown in the following example.</span></span>  
  
```  
Variable<int> a = new Variable<int>("a", 1);  
Variable<int> b = new Variable<int>("b", 2);  
Variable<int> c = new Variable<int>("c", 3);  
Variable<int> r = new Variable<int>("r", 0);  
  
Sequence w = new Sequence  
{  
    Variables = { a, b, c, r },  
    Activities =   
    {  
        new Assign {  
            To = new OutArgument<int>(r),  
            Value = new InArgument<int> {  
                Expression = new AddThreeValues() {  
                    Value1 = new InArgument<int>(a),  
                    Value2 = new InArgument<int>(b),  
                    Value3 = new InArgument<int>(c)  
                }  
            }  
        }  
    }  
};  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="012fd-120"> 程式碼中使用運算式，請參閱[撰寫工作流程、 活動和運算式使用命令式程式碼](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md)。</span><span class="sxs-lookup"><span data-stu-id="012fd-120"> using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
