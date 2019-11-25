---
title: Function 陳述式
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345925"
---
# <a name="function-statement-visual-basic"></a>Function 陳述式 (Visual Basic)

Declares the name, parameters, and code that define a `Function` procedure.

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>組件

- `attributelist`

  選擇項。 See [Attribute List](attribute-list.md).

- `accessmodifier`

  選擇項。 可以是下列其中一項：

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  請參閱 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

- `proceduremodifiers`

  選擇項。 可以是下列其中一項：

  - [多載](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [New](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  選擇項。 See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  選擇項。 See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Async`

  選擇項。 See [Async](../../../visual-basic/language-reference/modifiers/async.md).

- `Iterator`

  選擇項。 See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  必要項。 Name of the procedure. 請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。

- `typeparamlist`

  選擇項。 List of type parameters for a generic procedure. See [Type List](type-list.md).

- `parameterlist`

  選擇項。 List of local variable names representing the parameters of this procedure. See [Parameter List](parameter-list.md).

- `returntype`

  Required if `Option Strict` is `On`. Data type of the value returned by this procedure.

- `Implements`

  選擇項。 Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure. See [Implements Statement](implements-statement.md).

- `implementslist`

  如果使用 `Implements`，則為必要項。 實作之 `Function` 程序的清單。

  `implementedprocedure [ , implementedprocedure ... ]`

  每個 `implementedprocedure` 都具有下列語法和組件：

  `interface.definedname`

  |組件|描述|
  |---|---|
  |`interface`|必要項。 Name of an interface implemented by this procedure's containing class or structure.|
  |`definedname`|必要項。 名稱，據以在 `interface` 中定義程序。|

- `Handles`

  選擇項。 Indicates that this procedure can handle one or more specific events. See [Handles](handles-clause.md).

- `eventlist`

  如果使用 `Handles`，則為必要項。 List of events this procedure handles.

  `eventspecifier [ , eventspecifier ... ]`

  每個 `eventspecifier` 都具有下列語法和組件：

  `eventvariable.event`

  |組件|描述|
  |---|---|
  |`eventvariable`|必要項。 Object variable declared with the data type of the class or structure that raises the event.|
  |`event`|必要項。 Name of the event this procedure handles.|

- `statements`

  選擇項。 Block of statements to be executed within this procedure.

- `End Function`

  Terminates the definition of this procedure.

## <a name="remarks"></a>備註

All executable code must be inside a procedure. Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.

To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.

## <a name="defining-a-function"></a>Defining a Function

You can define a `Function` procedure only at the module level. Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block. 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

`Function` procedures default to public access. You can adjust their access levels with the access modifiers.

A `Function` procedure can declare the data type of the value that the procedure returns. You can specify any data type or the name of an enumeration, a structure, a class, or an interface. If you don't specify the `returntype` parameter, the procedure returns `Object`.

If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement. The `Implements` statement must include each interface that's specified in `implementslist`. However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).

> [!NOTE]
> You can use lambda expressions to define function expressions inline. For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Returning from a Function

When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.

To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.

The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure. Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.

If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`. If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.

## <a name="calling-a-function"></a>呼叫函式

You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression. You can omit the parentheses only if you aren't supplying any arguments. However, your code is more readable if you always include the parentheses.

You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.

You can also call a function by using the `Call` keyword. In that case, the return value is ignored. Use of the `Call` keyword isn't recommended in most cases. For more information, see [Call Statement](call-statement.md).

Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency. For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.

## <a name="async-functions"></a>Async Functions

The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.

If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function. When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes. When the task is complete, execution can resume in the function.

> [!NOTE]
> An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.

An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>. An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.

An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.

A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier. This is primarily used for event handlers, where a value cannot be returned. An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.

For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Iterator Functions

An *iterator* function performs a custom iteration over a collection, such as a list or array. An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time. When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered. 下次呼叫迭代器函式時，便會從這個位置重新開始執行。

You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.

The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.

如需詳細資訊，請參閱[迭代器](../../programming-guide/concepts/iterators.md)。

## <a name="example"></a>範例

The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure. The `ParamArray` modifier enables the function to accept a variable number of arguments.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>範例

The following example invokes the function declared in the preceding example.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>範例

In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>. `DelayAsync` 具有傳回整數的 `Return` 陳述式。 Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`. Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer. This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.

The `startButton_Click` procedure is an example of an `Async Sub` procedure. Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`. The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>請參閱

- [Sub 陳述式](sub-statement.md)
- [函式程序](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [參數清單](parameter-list.md)
- [Dim 陳述式](dim-statement.md)
- [Call 陳述式](call-statement.md)
- [Of](of-clause.md)
- [參數陣列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [如何：使用泛型類別](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [函式運算式](../../../visual-basic/language-reference/operators/function-expression.md)
