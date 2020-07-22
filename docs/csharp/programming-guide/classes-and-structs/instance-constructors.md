---
title: 執行個體建構函式 - C# 程式設計手冊
description: '當您使用新的運算式來建立類別的物件時，c # 中的實例函式會建立並初始化任何實例成員變數。'
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: d70e786446fb198afb4e0311757cacb65b706f47
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864198"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="8fc22-103">執行個體建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8fc22-103">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="8fc22-104">當您使用 [new](../../language-reference/operators/new-operator.md) 運算式來建立 [class](../../language-reference/keywords/class.md) 物件時，可使用執行個體建構函式來建立和初始化任何執行個體成員變數。</span><span class="sxs-lookup"><span data-stu-id="8fc22-104">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="8fc22-105">若要初始化[靜態](../../language-reference/keywords/static.md)類別或非靜態類別中的靜態變數，您可定義靜態建構函式。</span><span class="sxs-lookup"><span data-stu-id="8fc22-105">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="8fc22-106">如需詳細資訊，請參閱[靜態建構函式](./static-constructors.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc22-106">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="8fc22-107">下列範例顯示執行個體建構函式：</span><span class="sxs-lookup"><span data-stu-id="8fc22-107">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="8fc22-108">為了清楚起見，這個類別會包含公用欄位。</span><span class="sxs-lookup"><span data-stu-id="8fc22-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="8fc22-109">我們不建議您在程式設計中使用公用欄位，因為這麼做會允許程式中的任何方法，在不受限制及未經驗證的情況下，存取物件的內部運作。</span><span class="sxs-lookup"><span data-stu-id="8fc22-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="8fc22-110">資料成員一般應為私用，而且只應透過類別方法和屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="8fc22-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="8fc22-111">每當建立以 `Coords` 類別為基礎的物件時，即會呼叫這個執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="8fc22-111">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="8fc22-112">像這種不接受任何引數的建構函式，稱為「無參數建構函式」\*\*。</span><span class="sxs-lookup"><span data-stu-id="8fc22-112">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="8fc22-113">不過，提供額外的建構函式通常很實用。</span><span class="sxs-lookup"><span data-stu-id="8fc22-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="8fc22-114">比方說，我們可以將建構函式新增至 `Coords` 類別，以指定資料成員的起始值：</span><span class="sxs-lookup"><span data-stu-id="8fc22-114">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="8fc22-115">如此即可建立含有預設值或特定初始值的 `Coords` 物件，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8fc22-115">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="8fc22-116">如果類別不含建構函式，則會自動產生無參數建構函式，並使用預設值來初始化物件欄位。</span><span class="sxs-lookup"><span data-stu-id="8fc22-116">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="8fc22-117">例如，系統會將 [int](../../language-reference/builtin-types/integral-numeric-types.md) 初始化為 0。</span><span class="sxs-lookup"><span data-stu-id="8fc22-117">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="8fc22-118">如需類型預設值的詳細資訊，請參閱[c # 類型的預設值](../../language-reference/builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc22-118">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="8fc22-119">因此，由於 `Coords` 類別的無參數建構函式會將所有資料成員初始化為零，所以您可以將其完全移除，而不需變更類別的運作方式。</span><span class="sxs-lookup"><span data-stu-id="8fc22-119">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="8fc22-120">本主題稍後的範例 1 提供使用多個建構函式的完整範例；範例 2 則提供自動產生建構函式的範例。</span><span class="sxs-lookup"><span data-stu-id="8fc22-120">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="8fc22-121">執行個體建構函式也可用來呼叫基底類別的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="8fc22-121">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="8fc22-122">類別建構函式可以透過初始設定式，來叫用基底類別的建構函式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8fc22-122">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="8fc22-123">在此範例中，`Circle` 類別會將代表半徑和高度的值傳遞給 `Shape` 所提供的建構函式，進而衍生 `Circle`。</span><span class="sxs-lookup"><span data-stu-id="8fc22-123">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="8fc22-124">本主題的範例 3 會示範使用 `Shape` 和 `Circle` 的完整範例。</span><span class="sxs-lookup"><span data-stu-id="8fc22-124">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="8fc22-125">範例 1</span><span class="sxs-lookup"><span data-stu-id="8fc22-125">Example 1</span></span>  
 <span data-ttu-id="8fc22-126">下列範例示範的類別具有兩個類別建構函式，一個不含引數，一個具有兩個引數。</span><span class="sxs-lookup"><span data-stu-id="8fc22-126">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="8fc22-127">範例 2</span><span class="sxs-lookup"><span data-stu-id="8fc22-127">Example 2</span></span>  
 <span data-ttu-id="8fc22-128">在此範例中，`Person` 類別並沒有任何建構函式；在這種情況下，系統就會自動提供無參數建構函式，並將欄位初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="8fc22-128">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="8fc22-129">請注意，`age` 的預設值是 `0`，而 `name` 的預設值是 `null`。</span><span class="sxs-lookup"><span data-stu-id="8fc22-129">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="8fc22-130">範例 3</span><span class="sxs-lookup"><span data-stu-id="8fc22-130">Example 3</span></span>  
 <span data-ttu-id="8fc22-131">下列範例示範如何使用基底類別初始設定式。</span><span class="sxs-lookup"><span data-stu-id="8fc22-131">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="8fc22-132">`Circle` 類別衍生自一般類別 `Shape`，而 `Cylinder` 類別衍生自`Circle` 類別。</span><span class="sxs-lookup"><span data-stu-id="8fc22-132">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="8fc22-133">每個衍生類別上的建構函式會使用其基底類別初始設定式。</span><span class="sxs-lookup"><span data-stu-id="8fc22-133">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="8fc22-134">如需更多基底類別建構函式的叫用範例，請參閱 [virtual](../../language-reference/keywords/virtual.md)、[override](../../language-reference/keywords/override.md) 和 [base](../../language-reference/keywords/base.md)。</span><span class="sxs-lookup"><span data-stu-id="8fc22-134">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc22-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fc22-135">See also</span></span>

- [<span data-ttu-id="8fc22-136">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8fc22-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8fc22-137">類別和結構</span><span class="sxs-lookup"><span data-stu-id="8fc22-137">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="8fc22-138">建構函式</span><span class="sxs-lookup"><span data-stu-id="8fc22-138">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="8fc22-139">完成項</span><span class="sxs-lookup"><span data-stu-id="8fc22-139">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="8fc22-140">static</span><span class="sxs-lookup"><span data-stu-id="8fc22-140">static</span></span>](../../language-reference/keywords/static.md)
