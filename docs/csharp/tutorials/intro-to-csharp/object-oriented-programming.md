---
title: 物件導向程式設計 (C#)
description: 'C # 提供物件導向程式設計的完整支援，包括抽象、封裝、繼承和多型。'
ms.date: 09/30/2020
ms.openlocfilehash: b778b7c42bbfb1f20bdd2d83b9cb10512ea3f41b
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794842"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="c5e6c-103">Object-Oriented c # 程式設計 (c # ) </span><span class="sxs-lookup"><span data-stu-id="c5e6c-103">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="c5e6c-104">C # 是物件導向的語言。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-104">C# is an object-oriented language.</span></span> <span data-ttu-id="c5e6c-105">物件導向程式設計中所使用的四個關鍵技術包括：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-105">Four of the key techniques used in object-oriented programming are:</span></span>

- <span data-ttu-id="c5e6c-106">*抽象* 表示隱藏型別取用者不必要的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-106">*Abstraction* means hiding the unnecessary details from type consumers.</span></span>
- <span data-ttu-id="c5e6c-107">「封裝」指的是將一組相關的屬性、方法和其他成員，視為單一單位或物件。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-107">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="c5e6c-108">「繼承」則是描述依據現有類別來建立新類別的能力。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-108">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="c5e6c-109">「多型」指的是您可以有多個交替使用的類別，即使每個類別是以不同的方式來實作相同的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-109">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="c5e6c-110">在上述教學課程中，您看到的 [類別簡介](introduction-to-classes.md) 包括 *抽象* 和 *封裝*。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-110">In the preceding tutorial, [introduction to classes](introduction-to-classes.md) you saw both *abstraction* and *encapsulation*.</span></span> <span data-ttu-id="c5e6c-111">`BankAccount`類別提供了銀行帳戶概念的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-111">The `BankAccount` class provided an abstraction for the concept of a bank account.</span></span> <span data-ttu-id="c5e6c-112">您可以修改其執行，而不會影響使用該類別的任何程式碼 `BankAccount` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-112">You could modify its implementation without affecting any of the code that used the `BankAccount` class.</span></span> <span data-ttu-id="c5e6c-113">`BankAccount`和類別都 `Transaction` 提供在程式碼中描述這些概念所需元件的封裝。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-113">Both the `BankAccount` and `Transaction` classes provide encapsulation of the components needed to describe those concepts in code.</span></span>

<span data-ttu-id="c5e6c-114">在本教學課程中，您將擴充該應用程式，以利用 *繼承* 和 *多* 型的方式來新增新功能。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-114">In this tutorial, you'll extend that application to make use of *inheritance* and *polymorphism* to add new features.</span></span> <span data-ttu-id="c5e6c-115">您也會將功能加入至 `BankAccount` 類別，以利用您在上一個教學課程中學到的 *抽象概念* 和 *封裝* 技術。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-115">You'll also add features to the `BankAccount` class, taking advantage of the *abstraction* and *encapsulation* techniques you learned in the preceding tutorial.</span></span>

## <a name="create-different-types-of-accounts"></a><span data-ttu-id="c5e6c-116">建立不同類型的帳戶</span><span class="sxs-lookup"><span data-stu-id="c5e6c-116">Create different types of accounts</span></span>

<span data-ttu-id="c5e6c-117">建立此程式之後，您會收到將功能新增至其中的要求。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-117">After building this program, you get requests to add features to it.</span></span> <span data-ttu-id="c5e6c-118">它適用于只有一個銀行帳戶類型的情況。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-118">It works great in the situation where there is only one bank account type.</span></span> <span data-ttu-id="c5e6c-119">經過一段時間之後，需要變更，並要求相關的帳戶類型：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-119">Over time, needs change, and related account types are requested:</span></span>

- <span data-ttu-id="c5e6c-120">在每個月結束時累算興趣的利息收益帳戶。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-120">An interest earning account that accrues interest at the end of each month.</span></span>
- <span data-ttu-id="c5e6c-121">可以有負數餘額的信用額度，但如果有餘額，每個月會有相關的費用。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-121">A line of credit that can have a negative balance, but when there's a balance, there's an interest charge each month.</span></span>
- <span data-ttu-id="c5e6c-122">預先付費的禮物卡帳戶，以單一存款開頭，且僅可供付費。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-122">A pre-paid gift card account that starts with a single deposit, and only can be paid off.</span></span> <span data-ttu-id="c5e6c-123">您可以在每個月開始時重新填一次。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-123">It can be refilled once at the start of each month.</span></span>

<span data-ttu-id="c5e6c-124">所有這些不同的帳戶都類似于稍 `BankAccount` 早教學課程中所定義的類別。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-124">All of these different accounts are similar to `BankAccount` class defined in the earlier tutorial.</span></span> <span data-ttu-id="c5e6c-125">您可以複製該程式碼、重新命名類別，並進行修改。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-125">You could copy that code, rename the classes, and make modifications.</span></span> <span data-ttu-id="c5e6c-126">這項技術會在短期內運作，但在一段時間內會有更多工作。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-126">That technique would work in the short term, but it would be more work over time.</span></span> <span data-ttu-id="c5e6c-127">任何變更都會複製到所有受影響的類別。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-127">Any changes would be copied across all the affected classes.</span></span>

<span data-ttu-id="c5e6c-128">相反地，您可以建立新的銀行帳戶類型，從 `BankAccount` 先前教學課程中建立的類別繼承方法和資料。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-128">Instead, you can create new bank account types that inherit methods and data from the `BankAccount` class created in the preceding tutorial.</span></span> <span data-ttu-id="c5e6c-129">這些新的類別可以 `BankAccount` 使用每種類型所需的特定行為來擴充類別：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-129">These new classes can extend the `BankAccount` class with the specific behavior needed for each type:</span></span>

```csharp
public class InterestEarningAccount : BankAccount
{
}

public class LineOfCreditAccount : BankAccount
{
}

public class GiftCardAccount : BankAccount
{
}
```

<span data-ttu-id="c5e6c-130">每個類別都會 *繼承* 其共用 *基類*（類別）的共用行為 `BankAccount` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-130">Each of these classes *inherits* the shared behavior from their shared *base class*, the `BankAccount` class.</span></span> <span data-ttu-id="c5e6c-131">針對每個 *衍生類別* 中的新功能和不同的功能撰寫實作為。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-131">Write the implementations for new and different functionality in each of the *derived classes*.</span></span>  <span data-ttu-id="c5e6c-132">這些衍生類別已經具有類別中定義的所有行為 `BankAccount` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-132">These derived classes already have all the behavior defined in the `BankAccount` class.</span></span>

<span data-ttu-id="c5e6c-133">在不同的原始程式檔中建立每個新類別是很好的作法。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-133">It's a good practice to create each new class in a different source file.</span></span> <span data-ttu-id="c5e6c-134">在 [Visual Studio](https://visualstudio.com)中，您可以在專案上按一下滑鼠右鍵，然後選取 [ *加入類別* ]，在新的檔案中加入新的類別。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-134">In [Visual Studio](https://visualstudio.com), you can right-click on the project, and select *add class* to add a new class in a new file.</span></span> <span data-ttu-id="c5e6c-135">在 [Visual Studio Code](https://code.visualstudio.com)中， *選取 [* 檔案]，然後選取 [ *新增* ] 以建立新的原始檔。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-135">In [Visual Studio Code](https://code.visualstudio.com), select *File* then *New* to create a new source file.</span></span> <span data-ttu-id="c5e6c-136">在任一項工具中，將檔案命名以符合類別： *InterestEarningAccount.cs*、 *LineOfCreditAccount.cs* 和 *GiftCardAccount.cs*。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-136">In either tool, name the file to match the class: *InterestEarningAccount.cs*, *LineOfCreditAccount.cs*, and *GiftCardAccount.cs*.</span></span>

<span data-ttu-id="c5e6c-137">當您建立如先前範例所示的類別時，您會發現沒有任何衍生類別會進行編譯。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-137">When you create the classes as shown in the preceding sample, you'll find that none of your derived classes compile.</span></span> <span data-ttu-id="c5e6c-138">函式負責初始化物件。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-138">A constructor is responsible for initializing an object.</span></span> <span data-ttu-id="c5e6c-139">衍生類別的函式必須初始化衍生類別，並提供如何初始化衍生類別中所包含之基類物件的指示。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-139">A derived class constructor must initialize the derived class, and provide instructions on how to initialize the base class object included in the derived class.</span></span> <span data-ttu-id="c5e6c-140">適當的初始化通常會發生，而不需要任何額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-140">The proper initialization normally happens without any extra code.</span></span> <span data-ttu-id="c5e6c-141">類別會使用下列簽章宣告一個公用的函式 `BankAccount` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-141">The `BankAccount` class declares one public constructor with the following signature:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
```

<span data-ttu-id="c5e6c-142">當您自行定義函式時，編譯器不會產生預設的函式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-142">The compiler doesn't generate a default constructor when you define a constructor yourself.</span></span> <span data-ttu-id="c5e6c-143">這表示每個衍生類別都必須明確呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-143">That means each derived class must explicitly call this constructor.</span></span> <span data-ttu-id="c5e6c-144">您可以宣告可將引數傳遞至基類的函式的函式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-144">You declare a constructor that can pass arguments to the base class constructor.</span></span>  <span data-ttu-id="c5e6c-145">下列程式碼顯示的函式 `InterestEarningAccount` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-145">The following code shows the constructor for the `InterestEarningAccount`:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="DerivedConstructor":::

<span data-ttu-id="c5e6c-146">這個新的函式的參數符合基類函式的參數類型和名稱。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-146">The parameters to this new constructor match the parameter type and names of the base class constructor.</span></span> <span data-ttu-id="c5e6c-147">您可以使用 `: base()` 語法來表示呼叫基類的函式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-147">You use the `: base()` syntax to indicate a call to a base class constructor.</span></span> <span data-ttu-id="c5e6c-148">某些類別會定義多個函式，而此語法可讓您挑選您要呼叫的基類函式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-148">Some classes define multiple constructors, and this syntax enables you to pick which base class constructor you call.</span></span> <span data-ttu-id="c5e6c-149">更新這些函式之後，您可以為每個衍生類別開發程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-149">Once you've updated the constructors, you can develop the code for each of the derived classes.</span></span> <span data-ttu-id="c5e6c-150">新類別的需求可陳述如下：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-150">The requirements for the new classes can be stated as follows:</span></span>

- <span data-ttu-id="c5e6c-151">利息收益帳戶：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-151">An interest earning account:</span></span>
  - <span data-ttu-id="c5e6c-152">將取得每月的點數（以月為結束餘額）。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-152">Will get a credit of 2% of the month-ending-balance.</span></span>
- <span data-ttu-id="c5e6c-153">信用額度：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-153">A line of credit:</span></span>
  - <span data-ttu-id="c5e6c-154">可以有負數餘額，但絕對值不能大於點數限制。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-154">Can have a negative balance, but not be greater in absolute value than the credit limit.</span></span>
  - <span data-ttu-id="c5e6c-155">每個月都會產生利息費，而月底餘額不是0。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-155">Will incur an interest charge each month where the end of month balance isn't 0.</span></span>
  - <span data-ttu-id="c5e6c-156">會在每次提款時產生費用，並超過點數限制。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-156">Will incur a fee on each withdrawal that goes over the credit limit.</span></span>
- <span data-ttu-id="c5e6c-157">禮品卡帳戶：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-157">A gift card account:</span></span>
  - <span data-ttu-id="c5e6c-158">可以在每個月的最後一天，以指定的數量一次重新填入。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-158">Can be refilled with a specified amount once each month, on the last day of the month.</span></span>

<span data-ttu-id="c5e6c-159">您可以看到這些帳戶類型的三個都有一個動作會在每個月的結尾處進行。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-159">You can see that all three of these account types have an action that takes places at the end of each month.</span></span> <span data-ttu-id="c5e6c-160">不過，每個帳戶類型都會執行不同的工作。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-160">However, each account type does different tasks.</span></span> <span data-ttu-id="c5e6c-161">您可以使用 *多* 型來執行此程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-161">You use *polymorphism* to implement this code.</span></span> <span data-ttu-id="c5e6c-162">`virtual`在類別中建立單一方法 `BankAccount` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-162">Create a single `virtual` method in the `BankAccount` class:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="DeclareMonthEndTransactions":::

<span data-ttu-id="c5e6c-163">上述程式碼示範如何使用 `virtual` 關鍵字來宣告基類中的方法，衍生類別可能會提供不同的執行方式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-163">The preceding code shows how you use the `virtual` keyword to declare a method in the base class that a derived class may provide a different implementation for.</span></span> <span data-ttu-id="c5e6c-164">`virtual`方法是一種方法，其中任何衍生的類別都可以選擇重新進行。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-164">A `virtual` method is a method where any derived class may choose to reimplement.</span></span> <span data-ttu-id="c5e6c-165">衍生的類別會使用 `override` 關鍵字來定義新的實作為。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-165">The derived classes use the `override` keyword to define the new implementation.</span></span> <span data-ttu-id="c5e6c-166">通常您會將此稱為「覆寫基類實」。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-166">Typically you refer to this as "overriding the base class implementation".</span></span> <span data-ttu-id="c5e6c-167">`virtual`關鍵字會指定衍生類別可能會覆寫行為。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-167">The `virtual` keyword specifies that derived classes may override the behavior.</span></span> <span data-ttu-id="c5e6c-168">您也可以宣告 `abstract` 衍生類別必須覆寫行為的方法。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-168">You can also declare `abstract` methods where derived classes must override the behavior.</span></span> <span data-ttu-id="c5e6c-169">基類不提供方法的執行 `abstract` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-169">The base class does not provide an implementation for an `abstract` method.</span></span> <span data-ttu-id="c5e6c-170">接下來，您必須為您所建立的兩個新類別定義執行。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-170">Next, you need to define the implementation for two of the new classes you've created.</span></span> <span data-ttu-id="c5e6c-171">從開始 `InterestEarningAccount` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-171">Start with the `InterestEarningAccount`:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="ApplyMonthendInterest":::

<span data-ttu-id="c5e6c-172">將下列程式碼加入至 `LineOfCreditAccount` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-172">Add the following code to the `LineOfCreditAccount`.</span></span> <span data-ttu-id="c5e6c-173">此程式碼會否定餘額，以計算從帳戶中撤銷的正面利息費用：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-173">The code negates the balance to compute a positive interest charge that is withdrawn from the account:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ApplyMonthendInterest":::

<span data-ttu-id="c5e6c-174">此 `GiftCardAccount` 類別需要兩個變更，才能執行其 month end 功能。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-174">The `GiftCardAccount` class needs two changes to implement its month-end functionality.</span></span> <span data-ttu-id="c5e6c-175">首先，修改函式以包含每個月新增的選擇性數量：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-175">First, modify the constructor to include an optional amount to add each month:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="GiftCardAccountConstruction":::

<span data-ttu-id="c5e6c-176">此函式會提供值的預設值 `monthlyDeposit` ，因此呼叫者可以省略，而 `0` 不是每月的存款。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-176">The constructor provides a default value for the `monthlyDeposit` value so callers can omit a `0` for no monthly deposit.</span></span> <span data-ttu-id="c5e6c-177">接下來，覆寫 `PerformMonthEndTransactions` 方法以新增每月存款（如果它在函式中設定為非零的值）：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-177">Next, override the `PerformMonthEndTransactions` method to add the monthly deposit, if it was set to a non-zero value in the constructor:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="AddMonthlyDeposit":::

<span data-ttu-id="c5e6c-178">覆寫會在此函式中套用每月存款集。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-178">The override applies the monthly deposit set in the constructor.</span></span> <span data-ttu-id="c5e6c-179">將下列程式碼加入至 `Main` 方法，以測試 `GiftCardAccount` 和的這些變更 `InterestEarningAccount` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-179">Add the following code to the `Main` method to test these changes for the `GiftCardAccount` and the `InterestEarningAccount`:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="FirstTests":::

<span data-ttu-id="c5e6c-180">確認結果。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-180">Verify the results.</span></span> <span data-ttu-id="c5e6c-181">現在，為下列各項新增一組類似的測試程式碼 `LineOfCreditAccount` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-181">Now, add a similar set of test code for the `LineOfCreditAccount`:</span></span>

```
    var lineOfCredit = new LineOfCreditAccount("line of credit", 0);
    // How much is too much to borrow?
    lineOfCredit.MakeWithdrawal(1000m, DateTime.Now, "Take out monthly advance");
    lineOfCredit.MakeDeposit(50m, DateTime.Now, "Pay back small amount");
    lineOfCredit.MakeWithdrawal(5000m, DateTime.Now, "Emergency funds for repairs");
    lineOfCredit.MakeDeposit(150m, DateTime.Now, "Partial restoration on repairs");
    lineOfCredit.PerformMonthEndTransactions();
    Console.WriteLine(lineOfCredit.GetAccountHistory());
 ```

<span data-ttu-id="c5e6c-182">當您新增上述程式碼並執行程式時，將會看到類似下列的錯誤：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-182">When you add the preceding code and run the program, you'll see something like the following error:</span></span>

```console
Unhandled exception. System.ArgumentOutOfRangeException: Amount of deposit must be positive (Parameter 'amount')
   at OOProgramming.BankAccount.MakeDeposit(Decimal amount, DateTime date, String note) in BankAccount.cs:line 42
   at OOProgramming.BankAccount..ctor(String name, Decimal initialBalance) in BankAccount.cs:line 31
   at OOProgramming.LineOfCreditAccount..ctor(String name, Decimal initialBalance) in LineOfCreditAccount.cs:line 9
   at OOProgramming.Program.Main(String[] args) in Program.cs:line 29
```

> [!NOTE]
> <span data-ttu-id="c5e6c-183">實際的輸出會包含專案之資料夾的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-183">The actual output includes the full path to the folder with the project.</span></span> <span data-ttu-id="c5e6c-184">為了簡潔起見，已省略資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-184">The folder names were omitted for brevity.</span></span> <span data-ttu-id="c5e6c-185">此外，根據您的程式碼格式，行號可能稍有不同。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-185">Also, depending on your code format, the line numbers may be slightly different.</span></span>

<span data-ttu-id="c5e6c-186">此程式碼會失敗，因為 `BankAccount` 假設初始餘額必須大於0。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-186">This code fails because the `BankAccount` assumes that the initial balance must be greater than 0.</span></span> <span data-ttu-id="c5e6c-187">在類別中內建的另一個假設 `BankAccount` 是，餘額不能為負數。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-187">Another assumption baked into the `BankAccount` class is that the balance can't go negative.</span></span> <span data-ttu-id="c5e6c-188">相反地，overdraws 帳戶的任何提款都會遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-188">Instead, any withdrawal that overdraws the account is rejected.</span></span> <span data-ttu-id="c5e6c-189">這兩個假設都需要變更。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-189">Both of those assumptions need to change.</span></span> <span data-ttu-id="c5e6c-190">信用額度帳戶的行從0開始，而且通常會有負餘額。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-190">The line of credit account starts at 0, and generally will have a negative balance.</span></span> <span data-ttu-id="c5e6c-191">此外，如果客戶借用太多錢，則會產生費用。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-191">Also, if a customer borrows too much money, they incur a fee.</span></span> <span data-ttu-id="c5e6c-192">交易會被接受，而只是成本更高。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-192">The transaction is accepted, it just costs more.</span></span> <span data-ttu-id="c5e6c-193">第一個規則可以藉由將選擇性引數新增至 `BankAccount` 指定最小餘額的函式來執行。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-193">The first rule can be implemented by adding an optional argument to the `BankAccount` constructor that specifies the minimum balance.</span></span> <span data-ttu-id="c5e6c-194">預設為 `0`。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-194">The default is `0`.</span></span> <span data-ttu-id="c5e6c-195">第二個規則需要能讓衍生類別修改預設演算法的機制。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-195">The second rule requires a mechanism that enables derived classes to modify the default algorithm.</span></span> <span data-ttu-id="c5e6c-196">就某種意義而言，基類「會詢問」衍生型別透支時應該發生的情況。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-196">In a sense, the base class "asks" the derived type what should happen when there's an overdraft.</span></span> <span data-ttu-id="c5e6c-197">預設行為是藉由擲回例外狀況來拒絕交易。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-197">The default behavior is to reject the transaction by throwing an exception.</span></span>

<span data-ttu-id="c5e6c-198">首先，讓我們加入第二個包含選擇性參數的函式 `minimumBalance` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-198">Let's start by adding a second constructor that includes an optional `minimumBalance` parameter.</span></span> <span data-ttu-id="c5e6c-199">這個新的函式會執行現有的函式所執行的所有動作。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-199">This new constructor does all the actions done by the existing constructor.</span></span> <span data-ttu-id="c5e6c-200">此外，它也會設定最小餘額屬性。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-200">Also, it sets the minimum balance property.</span></span> <span data-ttu-id="c5e6c-201">您可以複製現有的函式主體。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-201">You could copy the body of the existing constructor.</span></span> <span data-ttu-id="c5e6c-202">但這表示未來有兩個要變更的位置。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-202">but that means two locations to change in the future.</span></span> <span data-ttu-id="c5e6c-203">相反地，您可以使用函式 *連結* 來呼叫另一個函式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-203">Instead, you can use *constructor chaining* to have one constructor call another.</span></span> <span data-ttu-id="c5e6c-204">下列程式碼顯示兩個函式和新的額外欄位：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-204">The following code shows the two constructors and the new additional field:</span></span>

 :::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="ConstructorModifications":::

<span data-ttu-id="c5e6c-205">上述程式碼顯示兩個新的技巧。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-205">The preceding code shows two new techniques.</span></span> <span data-ttu-id="c5e6c-206">首先， `minimumBalance` 欄位會標示為 `readonly` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-206">First, the `minimumBalance` field is marked as `readonly`.</span></span> <span data-ttu-id="c5e6c-207">這表示在建立物件之後，就無法變更此值。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-207">That means the value cannot be changed after the object is constructed.</span></span> <span data-ttu-id="c5e6c-208">一旦 `BankAccount` 建立之後，就 `minimumBalance` 無法變更。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-208">Once a `BankAccount` is created, the `minimumBalance` can't change.</span></span> <span data-ttu-id="c5e6c-209">其次，採用兩個參數的函式會使用 `: this(name, initialBalance, 0) { }` 做為其實作為。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-209">Second, the constructor that takes two parameters uses `: this(name, initialBalance, 0) { }` as its implementation.</span></span> <span data-ttu-id="c5e6c-210">`: this()`運算式會呼叫另一個具有三個參數的函式。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-210">The `: this()` expression calls the other constructor, the one with three parameters.</span></span> <span data-ttu-id="c5e6c-211">雖然用戶端程式代碼可以選擇許多個函式的其中一個，但是這項技術可讓您在初始化物件時進行單一初始化。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-211">This technique allows you to have a single implementation for initializing an object even though client code can choose one of many constructors.</span></span>

<span data-ttu-id="c5e6c-212">`MakeDeposit`只有在初始餘額大於時，才會呼叫此實作為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-212">This implementation calls `MakeDeposit` only if the initial balance is greater than `0`.</span></span> <span data-ttu-id="c5e6c-213">這會保留存款必須是正數的規則，但會讓點數帳戶以餘額開啟 `0` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-213">That preserves the rule that deposits must be positive, yet lets the credit account open with a `0` balance.</span></span>

<span data-ttu-id="c5e6c-214">既然 `BankAccount` 類別具有最小餘額的唯讀欄位，最後的變更是 `0` `minimumBalance` 在方法中將硬式程式碼變更為 `MakeWithdrawal` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-214">Now that the `BankAccount` class has a read-only field for the minimum balance, the final change is to change the hard code `0` to `minimumBalance` in the `MakeWithdrawal` method:</span></span>

```csharp
if (Balance - amount < minimumBalance)
```

<span data-ttu-id="c5e6c-215">擴充類別之後 `BankAccount` ，您可以修改函式 `LineOfCreditAccount` 來呼叫新的基底函式，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-215">After extending the `BankAccount` class, you can modify the `LineOfCreditAccount` constructor to call the new base constructor, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ConstructLineOfCredit":::

<span data-ttu-id="c5e6c-216">請注意，此函式會 `LineOfCreditAccount` 變更參數的正負號， `creditLimit` 使其符合參數的意義 `minimumBalance` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-216">Notice that the `LineOfCreditAccount` constructor changes the sign of the `creditLimit` parameter so it matches the meaning of the `minimumBalance` parameter.</span></span>

## <a name="different-overdraft-rules"></a><span data-ttu-id="c5e6c-217">不同的透支規則</span><span class="sxs-lookup"><span data-stu-id="c5e6c-217">Different overdraft rules</span></span>

<span data-ttu-id="c5e6c-218">最後一個要新增的功能，可讓您 `LineOfCreditAccount` 收取超過信用額度的費用，而不會拒絕交易。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-218">The last feature to add enables the `LineOfCreditAccount` to charge a fee for going over the credit limit instead of refusing the transaction.</span></span>

<span data-ttu-id="c5e6c-219">其中一個技術是定義虛擬函式，您可以在其中執行所需的行為。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-219">One technique is to define a virtual function where you implement the required behavior.</span></span> <span data-ttu-id="c5e6c-220">類別會將 `BankAccount` `MakeWithdrawal` 方法重構為兩個方法。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-220">The `BankAccount` class refactors the `MakeWithdrawal` method into two methods.</span></span> <span data-ttu-id="c5e6c-221">當提款將餘額降到低於最小值時，新的方法會執行指定的動作。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-221">The new method does the specified action when the withdrawal takes the balance below the minimum.</span></span> <span data-ttu-id="c5e6c-222">現有的 `MakeWithdrawal` 方法具有下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-222">The existing `MakeWithdrawal` method has the following code:</span></span>

```csharp
public void MakeWithdrawal(decimal amount, DateTime date, string note)
{
    if (amount <= 0)
    {
        throw new ArgumentOutOfRangeException(nameof(amount), "Amount of withdrawal must be positive");
    }
    if (Balance - amount < minimumBalance)
    {
        throw new InvalidOperationException("Not sufficient funds for this withdrawal");
    }
    var withdrawal = new Transaction(-amount, date, note);
    allTransactions.Add(withdrawal);
}
```

<span data-ttu-id="c5e6c-223">使用下列程式碼將其取代：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-223">Replace it with the following code:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="RefactoredMakeWithdrawal":::

<span data-ttu-id="c5e6c-224">加入的方法是 `protected` ，這表示它只能從衍生類別呼叫。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-224">The added method is `protected`, which means that it can be called only from derived classes.</span></span> <span data-ttu-id="c5e6c-225">該宣告可防止其他用戶端呼叫該方法。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-225">That declaration prevents other clients from calling the method.</span></span> <span data-ttu-id="c5e6c-226">此外 `virtual` ，衍生類別也可以變更行為。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-226">It's also `virtual` so that derived classes can change the behavior.</span></span> <span data-ttu-id="c5e6c-227">傳回型別為 `Transaction?` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-227">The return type is a `Transaction?`.</span></span> <span data-ttu-id="c5e6c-228">`?`批註表示方法可能會傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-228">The `?` annotation indicates that the method may return `null`.</span></span> <span data-ttu-id="c5e6c-229">在中新增下列實行 `LineOfCreditAccount` ，以在超過提款限制時收取費用：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-229">Add the following implementation in the `LineOfCreditAccount` to charge a fee when the withdrawal limit is exceeded:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="AddOverdraftFee":::

<span data-ttu-id="c5e6c-230">Overdrawn 帳戶時，覆寫會傳回費用交易。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-230">The override returns a fee transaction when the account is overdrawn.</span></span> <span data-ttu-id="c5e6c-231">如果提款未超過限制，則方法會傳回 `null` 交易。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-231">If the withdrawal doesn't go over the limit, the method returns a `null` transaction.</span></span> <span data-ttu-id="c5e6c-232">這表示不會有任何費用。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-232">That indicates there's no fee.</span></span> <span data-ttu-id="c5e6c-233">將下列程式碼新增至 `Main` 類別中的方法，以測試這些變更 `Program` ：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-233">Test these changes by adding the following code to your `Main` method in the `Program` class:</span></span>

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="TestLineOfCredit":::

<span data-ttu-id="c5e6c-234">執行程式，並檢查結果。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-234">Run the program, and check the results.</span></span>

## <a name="summary"></a><span data-ttu-id="c5e6c-235">摘要</span><span class="sxs-lookup"><span data-stu-id="c5e6c-235">Summary</span></span>

<span data-ttu-id="c5e6c-236">如果您遇到困難，您可以 [在 GitHub 存放庫中](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/object-oriented-programming)看到此教學課程的來源。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-236">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/object-oriented-programming).</span></span>

<span data-ttu-id="c5e6c-237">本教學課程示範 Object-Oriented 程式設計中使用的許多技術：</span><span class="sxs-lookup"><span data-stu-id="c5e6c-237">This tutorial demonstrated many of the techniques used in Object-Oriented programming:</span></span>

- <span data-ttu-id="c5e6c-238">當您在每個類別中保留許多詳細資料時，就會使用 *抽象概念* `private` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-238">You used *Abstraction* when you kept many details `private` in each class.</span></span>
- <span data-ttu-id="c5e6c-239">當您針對每個不同的帳戶類型定義了類別時，就會使用 *封裝* 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-239">You used *Encapsulation* when you defined classes for each of the different account types.</span></span> <span data-ttu-id="c5e6c-240">這些類別描述了該帳戶類型的行為。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-240">Those classes described the behavior for that type of account.</span></span>
- <span data-ttu-id="c5e6c-241">當您利用已在類別中建立的實存程式碼時，就會使用 *繼承* `BankAccount` 。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-241">You used *Inheritance* when you leveraged the implementation already created in the `BankAccount` class to save code.</span></span>
- <span data-ttu-id="c5e6c-242">當您建立 `virtual` 衍生類別可覆寫的方法，以建立該帳戶類型的特定行為時，您會使用多型。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-242">You used *Polymorphism* when you created `virtual` methods that derived classes could override to create specific behavior for that account type.</span></span>

<span data-ttu-id="c5e6c-243">恭喜，您已完成所有的 c # 教學課程簡介。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-243">Congratulations, you've finished all of our introduction to C# tutorials.</span></span> <span data-ttu-id="c5e6c-244">若要深入瞭解，請嘗試更多 [教學](../index.md)課程。</span><span class="sxs-lookup"><span data-stu-id="c5e6c-244">To learn more, try more of our [tutorials](../index.md).</span></span>
