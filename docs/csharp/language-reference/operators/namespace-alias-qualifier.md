---
title: ':: 運算子 - C# 參考'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 84c418627462f83630fe5072a0b0e2089f6588f6
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507122"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="fab45-102">:: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="fab45-102">:: operator (C# reference)</span></span>

<span data-ttu-id="fab45-103">使用命名空間別名限定詞`::`訪問別名命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="fab45-103">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="fab45-104">只能在兩個`::`識別碼之間使用限定詞。</span><span class="sxs-lookup"><span data-stu-id="fab45-104">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="fab45-105">左邊的識別碼可以是下列任何別名：</span><span class="sxs-lookup"><span data-stu-id="fab45-105">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="fab45-106">使用[使用別名指令](../keywords/using-directive.md)創建的命名空間別名 ：</span><span class="sxs-lookup"><span data-stu-id="fab45-106">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="fab45-107">[外部別名](../keywords/extern-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="fab45-107">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="fab45-108">`global` 別名，這是全域命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="fab45-108">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="fab45-109">全域命名空間是包含未在具名命名空間中宣告之命名空間和型別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="fab45-109">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="fab45-110">與 `::` 限定詞搭配使用時，`global` 別名一律會參考全域命名空間，即使有使用者定義的 `global` 命名空間別名也一樣。</span><span class="sxs-lookup"><span data-stu-id="fab45-110">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="fab45-111">下列範例使用 `global` 別名來存取 .NET <xref:System> 命名空間，這是全域命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="fab45-111">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="fab45-112">如果沒有 `global` 別名，則會存取使用者定義的 `System` 命名空間，這是 `MyCompany.MyProduct` 命名空間的成員：</span><span class="sxs-lookup"><span data-stu-id="fab45-112">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

  ```csharp
  namespace MyCompany.MyProduct.System
  {
      class Program
      {
          static void Main() => global::System.Console.WriteLine("Using global alias");
      }

      class Console
      {
          string Suggestion => "Consider renaming this class";
      }
  }
  ```

  > [!NOTE]
  > <span data-ttu-id="fab45-113">`global` 關鍵字只有在它是 `::` 限定詞的左邊識別碼時，才是全域命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="fab45-113">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="fab45-114">您還可以使用[`.`權杖](member-access-operators.md#member-access-expression-)訪問別名命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="fab45-114">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="fab45-115">但是，權杖`.`也用於訪問類型成員。</span><span class="sxs-lookup"><span data-stu-id="fab45-115">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="fab45-116">`::` 限定詞可確保其左邊的識別碼一律會參考命名空間別名，即使存在具有相同名稱的型別或命名空間也一樣。</span><span class="sxs-lookup"><span data-stu-id="fab45-116">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fab45-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="fab45-117">C# language specification</span></span>

<span data-ttu-id="fab45-118">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[命名空間別名限定詞](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers)一節。</span><span class="sxs-lookup"><span data-stu-id="fab45-118">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fab45-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fab45-119">See also</span></span>

- [<span data-ttu-id="fab45-120">C# 參考</span><span class="sxs-lookup"><span data-stu-id="fab45-120">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fab45-121">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="fab45-121">C# operators</span></span>](index.md)
- [<span data-ttu-id="fab45-122">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="fab45-122">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
