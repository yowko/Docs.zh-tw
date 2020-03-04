---
title: 類別和物件 - C# 教學課程簡介
description: 建立您的第一個 C# 程式並探索物件導向概念
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 5715124a307c7b7fe41b584df82dd328c873ae29
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240076"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="73082-103">探索使用類別與物件的物件導向程式設計</span><span class="sxs-lookup"><span data-stu-id="73082-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="73082-104">此教學課程要求您必須有可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="73082-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="73082-105">.NET 教學課程[Hello World 在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)，有在 Windows、Linux 或 macOS 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="73082-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="73082-106">您可以在[熟悉開發工具](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="73082-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="73082-107">建立您的應用程式</span><span class="sxs-lookup"><span data-stu-id="73082-107">Create your application</span></span>

<span data-ttu-id="73082-108">使用終端機視窗，建立名為 *classes* 的目錄。</span><span class="sxs-lookup"><span data-stu-id="73082-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="73082-109">您將在該目錄建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="73082-109">You'll build your application there.</span></span> <span data-ttu-id="73082-110">在主控台視窗中變更至該目錄並輸入 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="73082-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="73082-111">這個命令會建立您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="73082-111">This command creates your application.</span></span> <span data-ttu-id="73082-112">開啟 *Program.cs*。</span><span class="sxs-lookup"><span data-stu-id="73082-112">Open *Program.cs*.</span></span> <span data-ttu-id="73082-113">它看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="73082-113">It should look like this:</span></span>

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

<span data-ttu-id="73082-114">在此教學課程中，您將建立代表銀行帳戶的新型別。</span><span class="sxs-lookup"><span data-stu-id="73082-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="73082-115">開發人員通常會在不同的文字檔中定義每個類別。</span><span class="sxs-lookup"><span data-stu-id="73082-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="73082-116">隨著程式大小增加，這麼做會使它更易於管理。</span><span class="sxs-lookup"><span data-stu-id="73082-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="73082-117">在 *classes* 目錄中，建立名為 *BankAccount.cs* 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="73082-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span> 

<span data-ttu-id="73082-118">這個檔案會包含***銀行帳戶***的定義。</span><span class="sxs-lookup"><span data-stu-id="73082-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="73082-119">物件導向程式設計會以***類別***的形式建立類型來組織程式碼。</span><span class="sxs-lookup"><span data-stu-id="73082-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="73082-120">這些類別包含代表特定實體的程式碼。</span><span class="sxs-lookup"><span data-stu-id="73082-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="73082-121">`BankAccount` 類別代表銀行帳戶。</span><span class="sxs-lookup"><span data-stu-id="73082-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="73082-122">程式碼會透過方法和屬性來實作特定的作業。</span><span class="sxs-lookup"><span data-stu-id="73082-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="73082-123">在此教學課程中，銀行帳戶支援此行為：</span><span class="sxs-lookup"><span data-stu-id="73082-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="73082-124">它具有能唯一識別銀行帳戶的 10 位數數字。</span><span class="sxs-lookup"><span data-stu-id="73082-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="73082-125">它具有能儲存擁有者一個或多個名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="73082-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="73082-126">可擷取餘額。</span><span class="sxs-lookup"><span data-stu-id="73082-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="73082-127">它接受存款。</span><span class="sxs-lookup"><span data-stu-id="73082-127">It accepts deposits.</span></span>
1. <span data-ttu-id="73082-128">它接受提款。</span><span class="sxs-lookup"><span data-stu-id="73082-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="73082-129">初始餘額必須為正數。</span><span class="sxs-lookup"><span data-stu-id="73082-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="73082-130">提款不可使餘額成為負數。</span><span class="sxs-lookup"><span data-stu-id="73082-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="73082-131">定義銀行帳戶類型</span><span class="sxs-lookup"><span data-stu-id="73082-131">Define the bank account type</span></span>

<span data-ttu-id="73082-132">您可以從建立能定義該行為之類別的基礎項目來開始。</span><span class="sxs-lookup"><span data-stu-id="73082-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="73082-133">內容應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="73082-133">It would look like this:</span></span>

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

<span data-ttu-id="73082-134">在繼續之前，讓我們先查看您所建置的內容。</span><span class="sxs-lookup"><span data-stu-id="73082-134">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="73082-135">`namespace` 宣告能提供以邏輯方式組織程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="73082-135">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="73082-136">此教學課程的規模相對較小，所以您會將所有程式碼置於一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="73082-136">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span> 

<span data-ttu-id="73082-137">`public class BankAccount` 能定義您要建立的類別 (或類型)。</span><span class="sxs-lookup"><span data-stu-id="73082-137">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="73082-138">在類別宣告之後，`{` 和 `}` 內的所有專案都會定義類別的狀態和行為。</span><span class="sxs-lookup"><span data-stu-id="73082-138">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="73082-139">***類別有五個***成員`BankAccount`。</span><span class="sxs-lookup"><span data-stu-id="73082-139">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="73082-140">前三個為***屬性***。</span><span class="sxs-lookup"><span data-stu-id="73082-140">The first three are ***properties***.</span></span> <span data-ttu-id="73082-141">屬性是資料元素，且可以具有強制執行驗證或其他規則的程式碼。</span><span class="sxs-lookup"><span data-stu-id="73082-141">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="73082-142">後兩個為***方法***。</span><span class="sxs-lookup"><span data-stu-id="73082-142">The last two are ***methods***.</span></span> <span data-ttu-id="73082-143">方法是執行單一函式的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="73082-143">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="73082-144">閱讀每個成員的名稱，應該能提供足夠的資訊，以供您或其他開發人員了解該類別的功能。</span><span class="sxs-lookup"><span data-stu-id="73082-144">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="73082-145">開啟新帳戶</span><span class="sxs-lookup"><span data-stu-id="73082-145">Open a new account</span></span>

<span data-ttu-id="73082-146">第一個要實作的功能是開啟一個銀行帳戶。</span><span class="sxs-lookup"><span data-stu-id="73082-146">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="73082-147">當客戶開啟帳戶時，他們必須提供初始餘額，以及該帳戶的一或多個擁有者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="73082-147">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span> 

<span data-ttu-id="73082-148">建立一個 `BankAccount` 類型的新物件，表示定義一個能指派那些值的***建構函式***。</span><span class="sxs-lookup"><span data-stu-id="73082-148">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="73082-149">***建構函式***是具有和該類別相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="73082-149">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="73082-150">它是用來初始化該類別類型的物件。</span><span class="sxs-lookup"><span data-stu-id="73082-150">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="73082-151">將下列建構函式新增到 `BankAccount` 類型：</span><span class="sxs-lookup"><span data-stu-id="73082-151">Add the following constructor to the `BankAccount` type:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="73082-152">當您使用 [`new`](../../language-reference/operators/new-operator.md) 建立物件時，系統便會呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="73082-152">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="73082-153">使用下列程式碼取代*Program.cs*中的行 `Console.WriteLine("Hello World!");` （以您的名稱取代 `<name>`）：</span><span class="sxs-lookup"><span data-stu-id="73082-153">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="73082-154">輸入 `dotnet run` 看看會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="73082-154">Type `dotnet run` to see what happens.</span></span>  

<span data-ttu-id="73082-155">您是否注意到帳戶號碼是空白的？</span><span class="sxs-lookup"><span data-stu-id="73082-155">Did you notice that the account number is blank?</span></span> <span data-ttu-id="73082-156">讓我們來修正此情況。</span><span class="sxs-lookup"><span data-stu-id="73082-156">It's time to fix that.</span></span> <span data-ttu-id="73082-157">帳戶號碼應該要在物件建構時指派。</span><span class="sxs-lookup"><span data-stu-id="73082-157">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="73082-158">但帳戶號碼不應該由呼叫者負責建立。</span><span class="sxs-lookup"><span data-stu-id="73082-158">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="73082-159">`BankAccount` 類別程式碼應該要知道如何指派新的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="73082-159">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="73082-160">最簡單的方法是以 10 位數的數字開始。</span><span class="sxs-lookup"><span data-stu-id="73082-160">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="73082-161">建立每個新帳戶時就增加它。</span><span class="sxs-lookup"><span data-stu-id="73082-161">Increment it when each new account is created.</span></span> <span data-ttu-id="73082-162">最後，在物件完成建構時儲存目前的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="73082-162">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="73082-163">將下列成員宣告新增到 `BankAccount` 類別：</span><span class="sxs-lookup"><span data-stu-id="73082-163">Add the following member declaration to the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="73082-164">這是一個資料成員。</span><span class="sxs-lookup"><span data-stu-id="73082-164">This is a data member.</span></span> <span data-ttu-id="73082-165">它是 `private`，這表示它只能由 `BankAccount` 類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="73082-165">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="73082-166">這是一種將公開責任（如擁有帳戶號碼）與私用實施（產生帳戶號碼的方式）分開的方式。</span><span class="sxs-lookup"><span data-stu-id="73082-166">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="73082-167">它也是 `static`，這表示它是由所有 `BankAccount` 物件共用的。</span><span class="sxs-lookup"><span data-stu-id="73082-167">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="73082-168">非靜態變數的值對於每個 `BankAccount` 物件的執行個體而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="73082-168">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="73082-169">將下列兩行新增到建構函式來指派帳戶號碼：</span><span class="sxs-lookup"><span data-stu-id="73082-169">Add the following two lines to the constructor to assign the account number:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="73082-170">輸入 `dotnet run` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="73082-170">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="73082-171">建立存款和提款</span><span class="sxs-lookup"><span data-stu-id="73082-171">Create deposits and withdrawals</span></span>

<span data-ttu-id="73082-172">您的銀行帳戶必須能接受存款及提款，才算能正常運作。</span><span class="sxs-lookup"><span data-stu-id="73082-172">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="73082-173">讓我們透過建立帳戶每一筆交易的日誌，來實作存款和提款。</span><span class="sxs-lookup"><span data-stu-id="73082-173">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="73082-174">相較於單純地在每次交易時更新餘額，建立日誌能提供數個好處。</span><span class="sxs-lookup"><span data-stu-id="73082-174">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="73082-175">該記錄可用來對所有交易進行稽核，以及管理每日餘額。</span><span class="sxs-lookup"><span data-stu-id="73082-175">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="73082-176">藉由在必要時計算所有交易記錄的餘額，在任何單一交易中已修正的錯誤都會正確地在下一次計算中反映出來。</span><span class="sxs-lookup"><span data-stu-id="73082-176">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="73082-177">讓我們從建立代表交易的新類型開始。</span><span class="sxs-lookup"><span data-stu-id="73082-177">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="73082-178">這是一個不具任何責任的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="73082-178">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="73082-179">它需要幾個屬性。</span><span class="sxs-lookup"><span data-stu-id="73082-179">It needs a few properties.</span></span> <span data-ttu-id="73082-180">建立名為 *Transaction.cs* 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="73082-180">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="73082-181">對其新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="73082-181">Add the following code to it:</span></span>

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

<span data-ttu-id="73082-182">現在，讓我們將 <xref:System.Collections.Generic.List%601> 物件的 `Transaction` 新增到 `BankAccount` 類別。</span><span class="sxs-lookup"><span data-stu-id="73082-182">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="73082-183">新增下列宣告：</span><span class="sxs-lookup"><span data-stu-id="73082-183">Add the following declaration:</span></span>

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<span data-ttu-id="73082-184"><xref:System.Collections.Generic.List%601> 類別需要您匯入不同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="73082-184">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="73082-185">將下列內容新增到 *BankAccount.cs* 的開頭：</span><span class="sxs-lookup"><span data-stu-id="73082-185">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="73082-186">現在，讓我們變更 `Balance` 的報告方式。</span><span class="sxs-lookup"><span data-stu-id="73082-186">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="73082-187">報告可以透過針對所有交易的值進行加總來取得。</span><span class="sxs-lookup"><span data-stu-id="73082-187">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="73082-188">將 `Balance` 類別中 `BankAccount` 的宣告修改成如下內容：</span><span class="sxs-lookup"><span data-stu-id="73082-188">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

<span data-ttu-id="73082-189">此範例顯示出***屬性***的一個重要層面。</span><span class="sxs-lookup"><span data-stu-id="73082-189">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="73082-190">現在您會在另一個程式要求餘額時計算該值。</span><span class="sxs-lookup"><span data-stu-id="73082-190">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="73082-191">您的計算會列舉所有交易，並提供總和作為目前的餘額。</span><span class="sxs-lookup"><span data-stu-id="73082-191">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="73082-192">接下來，請實作 `MakeDeposit` 和 `MakeWithdrawal` 方法。</span><span class="sxs-lookup"><span data-stu-id="73082-192">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="73082-193">這些方法會強制執行最後兩個規則：初始餘額必須為正數，且所有提款都不能產生負數的餘額。</span><span class="sxs-lookup"><span data-stu-id="73082-193">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span> 

<span data-ttu-id="73082-194">這也引進了***例外狀況***的概念。</span><span class="sxs-lookup"><span data-stu-id="73082-194">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="73082-195">這是指出方法若無法完成其工作便應擲回例外狀況的標準方法。</span><span class="sxs-lookup"><span data-stu-id="73082-195">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="73082-196">例外狀況的類型和與它相關的訊息會描述該錯誤。</span><span class="sxs-lookup"><span data-stu-id="73082-196">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="73082-197">在這裡，如果存款的金額是負數，`MakeDeposit` 方法便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73082-197">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="73082-198">如果提款金額是負數，或如果套用提款金額會造成負數的餘額，則 `MakeWithdrawal` 方法會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="73082-198">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance:</span></span>

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

<span data-ttu-id="73082-199">[`throw`](../../language-reference/keywords/throw.md) 陳述式會**擲回**例外狀況。</span><span class="sxs-lookup"><span data-stu-id="73082-199">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="73082-200">目前區塊的執行會結束，而且控制權會移轉給呼叫堆疊中找到最初相符的 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="73082-200">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="73082-201">您會在稍後新增 `catch` 區塊來測試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="73082-201">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="73082-202">應該對建構函式進行一項變更來使它會新增初始交易，而不是直接更新餘額。</span><span class="sxs-lookup"><span data-stu-id="73082-202">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="73082-203">由於您已撰寫 `MakeDeposit` 方法，請從建構函式呼叫它。</span><span class="sxs-lookup"><span data-stu-id="73082-203">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="73082-204">完成的建構函式應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="73082-204">The finished constructor should look like this:</span></span>

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<span data-ttu-id="73082-205"><xref:System.DateTime.Now?displayProperty=nameWithType> 是會傳回目前日期和時間的屬性。</span><span class="sxs-lookup"><span data-stu-id="73082-205"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="73082-206">透過在您的 `Main` 方法中新增一些存款和提款來測試此屬性：</span><span class="sxs-lookup"><span data-stu-id="73082-206">Test this by adding a few deposits and withdrawals in your `Main` method:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="73082-207">接下來，透過建立具有負數餘額的帳戶，來測試是否能攔截到錯誤情況：</span><span class="sxs-lookup"><span data-stu-id="73082-207">Next, test that you are catching error conditions by trying to create an account with a negative balance:</span></span>

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="73082-208">使用 [`try` 與 `catch` 陳述式](../../language-reference/keywords/try-catch.md)來標記可能會擲回例外狀況的程式碼區塊，並攔截您所預期的那些錯誤。</span><span class="sxs-lookup"><span data-stu-id="73082-208">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="73082-209">您可以使用同樣的技巧來測試會針對負數餘額擲回例外狀況的程式碼：</span><span class="sxs-lookup"><span data-stu-id="73082-209">You can use the same technique to test the code that throws an exception for a negative balance:</span></span>

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

<span data-ttu-id="73082-210">儲存檔案並輸入 `dotnet run` 來嘗試它。</span><span class="sxs-lookup"><span data-stu-id="73082-210">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="73082-211">挑戰 - 記錄所有交易</span><span class="sxs-lookup"><span data-stu-id="73082-211">Challenge - log all transactions</span></span>

<span data-ttu-id="73082-212">若要完成此教學課程，您可以撰寫會針對交易記錄建立 `GetAccountHistory` 的 `string` 方法。</span><span class="sxs-lookup"><span data-stu-id="73082-212">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="73082-213">將此方法新增到 `BankAccount` 型別：</span><span class="sxs-lookup"><span data-stu-id="73082-213">Add this method to the `BankAccount` type:</span></span>

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

<span data-ttu-id="73082-214">此方法使用 <xref:System.Text.StringBuilder> 類別來設定針對每個交易包含單一行之字串的格式。</span><span class="sxs-lookup"><span data-stu-id="73082-214">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="73082-215">您稍早已經在這些教學課程中看過字串格式設定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="73082-215">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="73082-216">一個新的字元是 `\t`。</span><span class="sxs-lookup"><span data-stu-id="73082-216">One new character is `\t`.</span></span> <span data-ttu-id="73082-217">它會插入定位字元以設定輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="73082-217">That inserts a tab to format the output.</span></span>

<span data-ttu-id="73082-218">新增下列行以在 *Program.cs* 中測試它：</span><span class="sxs-lookup"><span data-stu-id="73082-218">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="73082-219">輸入 `dotnet run` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="73082-219">Type `dotnet run` to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="73082-220">後續步驟</span><span class="sxs-lookup"><span data-stu-id="73082-220">Next steps</span></span>

<span data-ttu-id="73082-221">如果您停滯，可以[在我們的 GitHub 存放庫中](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/)看到本教學課程的來源。</span><span class="sxs-lookup"><span data-stu-id="73082-221">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/samples/tree/master/csharp/classes-quickstart/).</span></span>

<span data-ttu-id="73082-222">恭喜，您已完成所有 C# 簡介教學課程。</span><span class="sxs-lookup"><span data-stu-id="73082-222">Congratulations, you've finished all our introduction to C# tutorials.</span></span> <span data-ttu-id="73082-223">如果您想要深入瞭解，請嘗試我們的[教學](../index.md)課程。</span><span class="sxs-lookup"><span data-stu-id="73082-223">If you're eager to learn more, try more of our [tutorials](../index.md).</span></span>
