---
title: '如何瞭解傳遞結構和傳遞類別參考給方法之間的差異-c # 程式設計手冊'
description: '將結構傳遞給方法，與將類別實例傳遞至 c # 中的方法不同。 這個範例會顯示以傳值方式傳遞的結構和類別實例。'
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: fd64a5e1a02a7039f9e49ac6592e75c6466d4bc6
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098875"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a><span data-ttu-id="ce1c1-104">如何瞭解傳遞結構和傳遞類別參考給方法之間的差異 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="ce1c1-104">How to know the difference between passing a struct and passing a class reference to a method (C# Programming Guide)</span></span>

<span data-ttu-id="ce1c1-105">下例示範將 [struct](../../language-reference/builtin-types/struct.md) 傳遞給方法，與將 [class](../../language-reference/keywords/class.md) 執行個體傳遞給方法有何不同。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-105">The following example demonstrates how passing a [struct](../../language-reference/builtin-types/struct.md) to a method differs from passing a [class](../../language-reference/keywords/class.md) instance to a method.</span></span> <span data-ttu-id="ce1c1-106">在此範例中，兩個引數 (struct 和 class 執行個體) 都是以傳值方式傳遞，而且兩種方法都會變更引數其中一個欄位的值。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-106">In the example, both of the arguments (struct and class instance) are passed by value, and both methods change the value of one field of the argument.</span></span> <span data-ttu-id="ce1c1-107">不過，兩個方法的結果不相同，因為傳遞 struct 時所傳送內容，和傳遞 class 執行個體時所傳送的內容不同。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-107">However, the results of the two methods are not the same because what is passed when you pass a struct differs from what is passed when you pass an instance of a class.</span></span>  
  
 <span data-ttu-id="ce1c1-108">因為 struct 是[實值型別](../../language-reference/builtin-types/value-types.md)，所以當您[以傳值方式傳遞 struct](./passing-value-type-parameters.md) 給方法時，方法會收到 struct 引數的複本並在其上運作。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-108">Because a struct is a [value type](../../language-reference/builtin-types/value-types.md), when you [pass a struct by value](./passing-value-type-parameters.md) to a method, the method receives and operates on a copy of the struct argument.</span></span> <span data-ttu-id="ce1c1-109">方法無法存取呼叫方法中的原始 struct，因此無法以任何方式變更它。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-109">The method has no access to the original struct in the calling method and therefore can't change it in any way.</span></span> <span data-ttu-id="ce1c1-110">方法只能變更複本。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-110">The method can change only the copy.</span></span>  
  
 <span data-ttu-id="ce1c1-111">class 執行個體是[參考型別](../../language-reference/keywords/reference-types.md)，不是實值型別。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-111">A class instance is a [reference type](../../language-reference/keywords/reference-types.md), not a value type.</span></span> <span data-ttu-id="ce1c1-112">當[以傳值方式傳遞參考型別](./passing-reference-type-parameters.md)給方法時，方法會收到 class 執行個體的參考複本。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-112">When [a reference type is passed by value](./passing-reference-type-parameters.md) to a method, the method receives a copy of the reference to the class instance.</span></span> <span data-ttu-id="ce1c1-113">也就是說，呼叫的方法會接收實例位址的複本，而呼叫的方法會保留實例的原始位址。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-113">That is, the called method receives a copy of the address of the instance, and the calling method retains the original address of the instance.</span></span> <span data-ttu-id="ce1c1-114">呼叫方法中的 class 執行個體有位址，被呼叫方法中的參數有位址複本，而且這兩個位址都指向相同的物件。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-114">The class instance in the calling method has an address, the parameter in the called method has a copy of the address, and both addresses refer to the same object.</span></span> <span data-ttu-id="ce1c1-115">因為參數只包含位址的複本，所以被呼叫的方法無法變更呼叫方法中的 class 執行個體的位址。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-115">Because the parameter contains only a copy of the address, the called method cannot change the address of the class instance in the calling method.</span></span> <span data-ttu-id="ce1c1-116">不過，呼叫的方法可以使用位址的複本來存取原始位址和位址參考複本的類別成員。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-116">However, the called method can use the copy of the address to access the class members that both the original address and the copy of the address reference.</span></span> <span data-ttu-id="ce1c1-117">如果被呼叫方法變更類別成員，則呼叫方法中的原始 class 執行個體也會變更。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-117">If the called method changes a class member, the original class instance in the calling method also changes.</span></span>  
  
 <span data-ttu-id="ce1c1-118">下例的輸出會說明其間的差異。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-118">The output of the following example illustrates the difference.</span></span> <span data-ttu-id="ce1c1-119">因為方法使用參數中的位址尋找指定的 class 執行個體欄位，所以對方法 `ClassTaker` 的呼叫會變更 class 執行個體的 `willIChange` 欄位值。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-119">The value of the `willIChange` field of the class instance is changed by the call to method `ClassTaker` because the method uses the address in the parameter to find the specified field of the class instance.</span></span> <span data-ttu-id="ce1c1-120">因為引數值是 struct 本身的複本，不是其位址的複本，所以對方法 `StructTaker` 的呼叫不會變更呼叫方法中的 struct 的 `willIChange` 欄位。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-120">The `willIChange` field of the struct in the calling method is not changed by the call to method `StructTaker` because the value of the argument is a copy of the struct itself, not a copy of its address.</span></span> <span data-ttu-id="ce1c1-121">`StructTaker` 變更複本，而複本在完成對 `StructTaker` 的呼叫時遺失。</span><span class="sxs-lookup"><span data-stu-id="ce1c1-121">`StructTaker` changes the copy, and the copy is lost when the call to `StructTaker` is completed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce1c1-122">範例</span><span class="sxs-lookup"><span data-stu-id="ce1c1-122">Example</span></span>  

 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a><span data-ttu-id="ce1c1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce1c1-123">See also</span></span>

- [<span data-ttu-id="ce1c1-124">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ce1c1-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ce1c1-125">類別</span><span class="sxs-lookup"><span data-stu-id="ce1c1-125">Classes</span></span>](./classes.md)
- [<span data-ttu-id="ce1c1-126">結構類型</span><span class="sxs-lookup"><span data-stu-id="ce1c1-126">Structure types</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="ce1c1-127">傳遞參數</span><span class="sxs-lookup"><span data-stu-id="ce1c1-127">Passing Parameters</span></span>](./passing-parameters.md)
