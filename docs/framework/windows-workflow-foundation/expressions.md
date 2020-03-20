---
title: 運算式 - WF
ms.date: 03/30/2017
ms.assetid: c42341a9-43a1-462c-bffb-c5de004aa428
ms.openlocfilehash: 93fe449e8fa6c50f715d842c2ef6a9ecbd31aff2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182933"
---
# <a name="expressions"></a>運算式

Windows 工作流基礎 （WF） 運算式是返回結果的任何活動。 所有運算式活動會間接自 <xref:System.Activities.Activity%601> 衍生，其包含名為 <xref:System.Activities.OutArgument> 的 <xref:System.Activities.Activity%601.Result%2A> 做為活動的傳回值。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 隨附範圍廣大的運算式活動，包括簡單的活動 (例如 <xref:System.Activities.Expressions.VariableValue%601> 和 <xref:System.Activities.Expressions.VariableReference%601>，可透過運算子活動存取單一工作流程變數) 及複雜的活動 (例如 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>，可存取完整範圍的 Visual Basic 語言以產生結果)。 其他運算式活動可從 <xref:System.Activities.CodeActivity%601> 或 <xref:System.Activities.NativeActivity%601> 來衍生建立。

## <a name="using-expressions"></a>使用運算式
 工作流程設計工具會將 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> 和 <xref:Microsoft.VisualBasic.Activities.VisualBasicReference%601> 用於 Visual Basic 專案中的所有運算式，並將 <xref:Microsoft.CSharp.Activities.CSharpValue%601> 和 <xref:Microsoft.CSharp.Activities.CSharpReference%601> 用於 C# 工作流程專案中的運算式。

> [!NOTE]
> 在 .NET 框架 4.5 中引入了對工作流專案中 C# 運算式的支援。 有關詳細資訊，請參閱[C# 運算式](csharp-expressions.md)。

 由設計工具產生的工作流程會儲存為 XAML，其中會以方括號括住運算式，如以下範例所示。

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

 當以程式碼定義工作流程時，可使用任何運算式活動。 下面的示例顯示了運算子活動組合用於添加三個數字的用法：

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

 使用 C# lambda 運算式可以更緊湊地表示相同的工作流，如以下示例所示：
  
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

## <a name="extending-available-expressions-with-custom-expression-activities"></a>使用自訂運算式活動延伸可用的運算式

 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 中的運算式可延伸，以便建立其他的運算式活動。 下列程式碼範例示範會傳回三個整數值加總的活動。

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

 使用此新活動，您可以重寫添加三個值的上一個工作流，如以下示例所示：

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

 有關在代碼中使用運算式的詳細資訊，請參閱[使用命令代碼創作工作流、活動和運算式](authoring-workflows-activities-and-expressions-using-imperative-code.md)。
