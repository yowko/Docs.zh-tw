---
title: 如何：在 C# 中定義常數
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 03912a71aba883ec9127d265e6f1a2b05e1e60fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="3aaf6-102">如何：在 C# 中定義常數</span><span class="sxs-lookup"><span data-stu-id="3aaf6-102">How to: Define Constants in C#</span></span>
<span data-ttu-id="3aaf6-103">常數是欄位，其值於編譯時期設定且絕對不會變更。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-103">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="3aaf6-104">使用常數提供有意義的名稱，而不是特殊值的數值常值 (「神奇號碼」)。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-104">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3aaf6-105">在 C# 中，[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) 前置處理器指示詞不能以 C 和 C++ 一般使用的方式來定義常數。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-105">In C# the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="3aaf6-106">若要定義整數型別的常數值 (`int`、`byte` 等等)，請使用列舉類型。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-106">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="3aaf6-107">如需詳細資訊，請參閱 [enum](../../../csharp/language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-107">For more information, see [enum](../../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="3aaf6-108">若要定義非整數常數，其中一個方法是將它們分組在名為 `Constants` 的單一靜態類別中。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-108">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="3aaf6-109">如下列範例所示，這需要常數的所有參考都以類別名稱開頭。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-109">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3aaf6-110">範例</span><span class="sxs-lookup"><span data-stu-id="3aaf6-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#89](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-constants_1.cs)]  
  
 <span data-ttu-id="3aaf6-111">使用類別名稱限定詞，可協助確保您和其他常數使用者了解它是無法修改的常數。</span><span class="sxs-lookup"><span data-stu-id="3aaf6-111">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aaf6-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3aaf6-112">See Also</span></span>  
 [<span data-ttu-id="3aaf6-113">類別和結構</span><span class="sxs-lookup"><span data-stu-id="3aaf6-113">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
