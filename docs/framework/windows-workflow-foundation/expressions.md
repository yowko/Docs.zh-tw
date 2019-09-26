---
title: 運算式-WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 62b278825de6242075e89e3b243b6d6d8ef4d599
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306198"
---
# <a name="expressions"></a><span data-ttu-id="ad83c-102">運算式</span><span class="sxs-lookup"><span data-stu-id="ad83c-102">Expressions</span></span>

<span data-ttu-id="ad83c-103">Windows Workflow Foundation （WF）運算式是傳回結果的任何活動。</span><span class="sxs-lookup"><span data-stu-id="ad83c-103">A Windows Workflow Foundation (WF) expression is any activity that returns a result.</span></span> <span data-ttu-id="ad83c-104">所有運算式活動會間接自 <xref:System.Activities.Activity%601> 衍生，其包含名為 <xref:System.Activities.OutArgument> 的 <xref:System.Activities.Activity%601.Result%2A> 做為活動的傳回值。</span><span class="sxs-lookup"><span data-stu-id="ad83c-104">All expression activities derive indirectly from <xref:System.Activities.Activity%601>, which contains an <xref:System.Activities.OutArgument> property named <xref:System.Activities.Activity%601.Result%2A> as the activity’s return value.</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)] <span data-ttu-id="ad83c-105">隨附範圍廣大的運算式活動，包括簡單的活動 (例如 <xref:System.Activities.Expressions.VariableValue%601> 和 <xref:System.Activities.Expressions.VariableReference%601>，可透過運算子活動存取單一工作流程變數) 及複雜的活動 (例如 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>，可存取完整範圍的 Visual Basic 語言以產生結果)。</span><span class="sxs-lookup"><span data-stu-id="ad83c-105">ships with a wide range of expression activities from simple ones like <xref:System.Activities.Expressions.VariableValue%601> and <xref:System.Activities.Expressions.VariableReference%601>, which provide access to single workflow variable through operator activities, to complex activities such as <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> that offer access to the full breadth of Visual Basic language to produce the result.</span></span> <span data-ttu-id="ad83c-106">其他運算式活動可從 <xref:System.Activities.CodeActivity%601> 或 <xref:System.Activities.NativeActivity%601> 來衍生建立。</span><span class="sxs-lookup"><span data-stu-id="ad83c-106">Additional expression activities can be created by deriving from <xref:System.Activities.CodeActivity%601> or <xref:System.Activities.NativeActivity%601>.</span></span>

## <a name="using-expressions"></a><span data-ttu-id="ad83c-107">使用運算式</span><span class="sxs-lookup"><span data-stu-id="ad83c-107">Using Expressions</span></span>
 <span data-ttu-id="ad83c-108">工作流程設計工具會將 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 用於 Visual Basic 專案中的所有運算式，並將 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 和 <xref:Microsoft.CSharp.Activities.CSharpReference%601> 用於 C# 工作流程專案中的運算式。</span><span class="sxs-lookup"><span data-stu-id="ad83c-108">Workflow designer uses <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> and <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> for all expressions in Visual Basic projects, and <xref:Microsoft.CSharp.Activities.CSharpValue%601> and <xref:Microsoft.CSharp.Activities.CSharpReference%601> for expressions in C# workflow projects.</span></span>

> [!NOTE]
> <span data-ttu-id="ad83c-109">工作流程C#專案中的運算式支援是在 .NET Framework 4.5 中引進。</span><span class="sxs-lookup"><span data-stu-id="ad83c-109">Support for C# expressions in workflow projects was introduced in .NET Framework 4.5.</span></span> <span data-ttu-id="ad83c-110">如需詳細資訊，請參閱[ C#運算式](csharp-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="ad83c-110">For more information, see [C# Expressions](csharp-expressions.md).</span></span>

 <span data-ttu-id="ad83c-111">由設計工具產生的工作流程會儲存為 XAML，其中會以方括號括住運算式，如以下範例所示。</span><span class="sxs-lookup"><span data-stu-id="ad83c-111">Workflows produced by designer are saved in XAML, where expressions appear enclosed in square brackets, as in the following example.</span></span>

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

 <span data-ttu-id="ad83c-112">當以程式碼定義工作流程時，可使用任何運算式活動。</span><span class="sxs-lookup"><span data-stu-id="ad83c-112">When defining a workflow in code, any expression activities can be used.</span></span> <span data-ttu-id="ad83c-113">下列範例示範如何使用運算子活動的組合來新增三個數字：</span><span class="sxs-lookup"><span data-stu-id="ad83c-113">The following example shows the usage of a composition of operator activities to add three numbers:</span></span>

```csharp
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

 <span data-ttu-id="ad83c-114">相同的工作流程可以使用C# lambda 運算式來表示更簡潔地，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad83c-114">The same workflow can be expressed more compactly by using C# lambda expressions, as shown in the following example:</span></span>
  
```csharp
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a><span data-ttu-id="ad83c-115">使用自訂運算式活動延伸可用的運算式</span><span class="sxs-lookup"><span data-stu-id="ad83c-115">Extending Available Expressions with Custom Expression Activities</span></span>

 <span data-ttu-id="ad83c-116">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中的運算式可延伸，以便建立其他的運算式活動。</span><span class="sxs-lookup"><span data-stu-id="ad83c-116">Expressions in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] are extensible allowing for additional expression activities to be created.</span></span> <span data-ttu-id="ad83c-117">下列程式碼範例示範會傳回三個整數值加總的活動。</span><span class="sxs-lookup"><span data-stu-id="ad83c-117">The following example shows an activity that returns a sum of three integer values.</span></span>

```csharp
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

 <span data-ttu-id="ad83c-118">透過這個新活動，您可以重寫先前新增三個值的工作流程，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad83c-118">With this new activity you can rewrite the previous workflow that added three values as shown in the following example:</span></span>

```csharp
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

 <span data-ttu-id="ad83c-119">如需在程式碼中使用運算式的詳細資訊，請參閱[使用命令式程式碼撰寫工作流程、活動和運算式](authoring-workflows-activities-and-expressions-using-imperative-code.md)。</span><span class="sxs-lookup"><span data-stu-id="ad83c-119">For more information about using expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md).</span></span>
