---
description: ':: 運算子 - C# 參考'
title: ':: 運算子 - C# 參考'
ms.date: 08/09/2019
f1_keywords:
- ::_CSharpKeyword
- global_CSharpKeyword
- global
helpviewer_keywords:
- ':: operator [C#]'
- namespace alias qualifier [C#]
- namespace [C#]
- global keyword [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 6c901ce083dde6f2e28520fafe3313071ae792c8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118321"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2bcb9-103">:: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2bcb9-103">:: operator (C# reference)</span></span>

<span data-ttu-id="2bcb9-104">使用命名空間別名辨識符號 `::` 來存取別名命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-104">Use the namespace alias qualifier `::` to access a member of an aliased namespace.</span></span> <span data-ttu-id="2bcb9-105">您只能在 `::` 兩個識別碼之間使用限定詞。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-105">You can use the `::` qualifier only between two identifiers.</span></span> <span data-ttu-id="2bcb9-106">左邊的識別碼可以是下列任何別名：</span><span class="sxs-lookup"><span data-stu-id="2bcb9-106">The left-hand identifier can be any of the following aliases:</span></span>

- <span data-ttu-id="2bcb9-107">使用 [using alias](../keywords/using-directive.md)指示詞建立的命名空間別名：</span><span class="sxs-lookup"><span data-stu-id="2bcb9-107">A namespace alias created with a [using alias directive](../keywords/using-directive.md):</span></span>

  ```csharp
  using forwinforms = System.Drawing;
  using forwpf = System.Windows;
  
  public class Converters
  {
      public static forwpf::Point Convert(forwinforms::Point point) => new forwpf::Point(point.X, point.Y);
  }
  ```

- <span data-ttu-id="2bcb9-108">[外部別名](../keywords/extern-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-108">An [extern alias](../keywords/extern-alias.md).</span></span>
- <span data-ttu-id="2bcb9-109">`global` 別名，這是全域命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-109">The `global` alias, which is the global namespace alias.</span></span> <span data-ttu-id="2bcb9-110">全域命名空間是包含未在具名命名空間中宣告之命名空間和型別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-110">The global namespace is the namespace that contains namespaces and types that are not declared inside a named namespace.</span></span> <span data-ttu-id="2bcb9-111">與 `::` 限定詞搭配使用時，`global` 別名一律會參考全域命名空間，即使有使用者定義的 `global` 命名空間別名也一樣。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-111">When used with the `::` qualifier, the `global` alias always references the global namespace, even if there is the user-defined `global` namespace alias.</span></span>

  <span data-ttu-id="2bcb9-112">下列範例使用 `global` 別名來存取 .NET <xref:System> 命名空間，這是全域命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-112">The following example uses the `global` alias to access the .NET <xref:System> namespace, which is a member of the global namespace.</span></span> <span data-ttu-id="2bcb9-113">如果沒有 `global` 別名，則會存取使用者定義的 `System` 命名空間，這是 `MyCompany.MyProduct` 命名空間的成員：</span><span class="sxs-lookup"><span data-stu-id="2bcb9-113">Without the `global` alias, the user-defined `System` namespace, which is a member of the `MyCompany.MyProduct` namespace, would be accessed:</span></span>

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
  > <span data-ttu-id="2bcb9-114">`global` 關鍵字只有在它是 `::` 限定詞的左邊識別碼時，才是全域命名空間別名。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-114">The `global` keyword is the global namespace alias only when it's the left-hand identifier of the `::` qualifier.</span></span>

<span data-ttu-id="2bcb9-115">您也可以使用[ `.` 權杖](member-access-operators.md#member-access-expression-)來存取別名命名空間的成員。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-115">You can also use the [`.` token](member-access-operators.md#member-access-expression-) to access a member of an aliased namespace.</span></span> <span data-ttu-id="2bcb9-116">不過， `.` 標記也用來存取類型成員。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-116">However, the `.` token is also used to access a type member.</span></span> <span data-ttu-id="2bcb9-117">`::` 限定詞可確保其左邊的識別碼一律會參考命名空間別名，即使存在具有相同名稱的型別或命名空間也一樣。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-117">The `::` qualifier ensures that its left-hand identifier always references a namespace alias, even if there exists a type or namespace with the same name.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2bcb9-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2bcb9-118">C# language specification</span></span>

<span data-ttu-id="2bcb9-119">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[命名空間別名限定詞](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers)一節。</span><span class="sxs-lookup"><span data-stu-id="2bcb9-119">For more information, see the [Namespace alias qualifiers](~/_csharplang/spec/namespaces.md#namespace-alias-qualifiers) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2bcb9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bcb9-120">See also</span></span>

- [<span data-ttu-id="2bcb9-121">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="2bcb9-121">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2bcb9-122">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="2bcb9-122">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="2bcb9-123">使用命名空間</span><span class="sxs-lookup"><span data-stu-id="2bcb9-123">Using namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
