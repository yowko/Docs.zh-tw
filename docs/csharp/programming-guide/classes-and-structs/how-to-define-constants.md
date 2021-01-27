---
title: 如何在 C# 中定義常數
description: '瞭解如何在 c # 中定義常數，也就是值在編譯時期設定的欄位。 使用常數為特殊值提供有意義的名稱。'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 4ee1b04cf30b7602ae563cb02daed49f82c04de7
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898992"
---
# <a name="how-to-define-constants-in-c"></a><span data-ttu-id="6e555-104">如何在 C 中定義常數\#</span><span class="sxs-lookup"><span data-stu-id="6e555-104">How to define constants in C\#</span></span>

<span data-ttu-id="6e555-105">常數是欄位，其值於編譯時期設定且絕對不會變更。</span><span class="sxs-lookup"><span data-stu-id="6e555-105">Constants are fields whose values are set at compile time and can never be changed.</span></span> <span data-ttu-id="6e555-106">使用常數提供有意義的名稱，而不是特殊值的數值常值 (「神奇號碼」)。</span><span class="sxs-lookup"><span data-stu-id="6e555-106">Use constants to provide meaningful names instead of numeric literals ("magic numbers") for special values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e555-107">在 C# 中，[#define](../../language-reference/preprocessor-directives/preprocessor-define.md) 前置處理器指示詞不能以 C 和 C++ 一般使用的方式來定義常數。</span><span class="sxs-lookup"><span data-stu-id="6e555-107">In C# the [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) preprocessor directive cannot be used to define constants in the way that is typically used in C and C++.</span></span>  
  
 <span data-ttu-id="6e555-108">若要定義整數型別的常數值 (`int`、`byte` 等等)，請使用列舉類型。</span><span class="sxs-lookup"><span data-stu-id="6e555-108">To define constant values of integral types (`int`, `byte`, and so on) use an enumerated type.</span></span> <span data-ttu-id="6e555-109">如需詳細資訊，請參閱 [enum](../../language-reference/builtin-types/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="6e555-109">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="6e555-110">若要定義非整數常數，其中一個方法是將它們分組在名為 `Constants` 的單一靜態類別中。</span><span class="sxs-lookup"><span data-stu-id="6e555-110">To define non-integral constants, one approach is to group them in a single static class named `Constants`.</span></span> <span data-ttu-id="6e555-111">如下列範例所示，這需要常數的所有參考都以類別名稱開頭。</span><span class="sxs-lookup"><span data-stu-id="6e555-111">This will require that all references to the constants be prefaced with the class name, as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e555-112">範例</span><span class="sxs-lookup"><span data-stu-id="6e555-112">Example</span></span>  

 [!code-csharp[constants](snippets/how-to-define-constants/Program.cs)]  
  
 <span data-ttu-id="6e555-113">使用類別名稱限定詞，可協助確保您和其他常數使用者了解它是無法修改的常數。</span><span class="sxs-lookup"><span data-stu-id="6e555-113">The use of the class name qualifier helps ensure that you and others who use the constant understand that it is constant and cannot be modified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e555-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e555-114">See also</span></span>

- [<span data-ttu-id="6e555-115">類別和結構</span><span class="sxs-lookup"><span data-stu-id="6e555-115">Classes and Structs</span></span>](./index.md)
