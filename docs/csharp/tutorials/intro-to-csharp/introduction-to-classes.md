---
title: 類別和物件 - C# 教學課程簡介
description: 建立您的第一個 C# 程式並探索物件導向概念
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 0955b0ac33b346b9880c8af70bd73cb458120f35
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434887"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="3d4ae-103">探索使用類別與物件的物件導向程式設計</span><span class="sxs-lookup"><span data-stu-id="3d4ae-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="3d4ae-104">此教學課程要求您必須有可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="3d4ae-105">.NET 教學課程 [Hello World 10 分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) 的指示，說明如何在 Windows、Linux 或 macOS 上設定您的本機開發環境。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="3d4ae-106">您可以在[熟悉開發工具](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="3d4ae-107">建立您的應用程式</span><span class="sxs-lookup"><span data-stu-id="3d4ae-107">Create your application</span></span>

<span data-ttu-id="3d4ae-108">使用終端機視窗，建立名為 *classes* 的目錄。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="3d4ae-109">您將在該目錄建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-109">You'll build your application there.</span></span> <span data-ttu-id="3d4ae-110">在主控台視窗中變更至該目錄並輸入 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="3d4ae-111">這個命令會建立您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-111">This command creates your application.</span></span> <span data-ttu-id="3d4ae-112">開啟 *Program.cs*。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-112">Open *Program.cs*.</span></span> <span data-ttu-id="3d4ae-113">其看起來應該如下：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-113">It should look like this:</span></span>

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

<span data-ttu-id="3d4ae-114">在此教學課程中，您將建立代表銀行帳戶的新型別。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="3d4ae-115">開發人員通常會在不同的文字檔中定義每個類別。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="3d4ae-116">隨著程式大小增加，這麼做會使它更易於管理。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="3d4ae-117">在 *classes* 目錄中，建立名為 *BankAccount.cs* 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="3d4ae-118">此檔案將包含 \***bank 帳戶**_ 的定義。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-118">This file will contain the definition of a \***bank account**_.</span></span> <span data-ttu-id="3d4ae-119">物件導向程式設計會以 _\*_類別_\*_ 的形式建立類型來組織程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-119">Object Oriented programming organizes code by creating types in the form of _*_classes_*_.</span></span> <span data-ttu-id="3d4ae-120">這些類別包含代表特定實體的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="3d4ae-121">`BankAccount` 類別代表銀行帳戶。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="3d4ae-122">程式碼會透過方法和屬性來實作特定的作業。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="3d4ae-123">在此教學課程中，銀行帳戶支援此行為：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="3d4ae-124">它具有能唯一識別銀行帳戶的 10 位數數字。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="3d4ae-125">它具有能儲存擁有者一個或多個名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="3d4ae-126">可擷取餘額。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="3d4ae-127">它接受存款。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-127">It accepts deposits.</span></span>
1. <span data-ttu-id="3d4ae-128">它接受提款。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="3d4ae-129">初始餘額必須為正數。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="3d4ae-130">提款不可使餘額成為負數。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="3d4ae-131">定義銀行帳戶類型</span><span class="sxs-lookup"><span data-stu-id="3d4ae-131">Define the bank account type</span></span>

<span data-ttu-id="3d4ae-132">您可以從建立能定義該行為之類別的基礎項目來開始。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="3d4ae-133">使用 _*file： new*\* 命令建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-133">Create a new file using the _*File:New*\* command.</span></span> <span data-ttu-id="3d4ae-134">將它命名為 *BankAccount.cs*。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="3d4ae-135">將下列程式碼新增至 *BankAccount.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-135">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="3d4ae-136">在繼續之前，讓我們先查看您所建置的內容。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="3d4ae-137">`namespace` 宣告能提供以邏輯方式組織程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="3d4ae-138">此教學課程的規模相對較小，所以您會將所有程式碼置於一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="3d4ae-139">`public class BankAccount` 能定義您要建立的類別 (或類型)。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="3d4ae-140">內的所有專案，以及在類別宣告之後的所有專案，都 `{` `}` 定義了類別的狀態和行為。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="3d4ae-141">類別有五個 \***成員**_ `BankAccount` 。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-141">There are five \***members**_ of the `BankAccount` class.</span></span> <span data-ttu-id="3d4ae-142">前三個是 _\*_屬性_\*_。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-142">The first three are _*_properties_*_.</span></span> <span data-ttu-id="3d4ae-143">屬性是資料元素，且可以具有強制執行驗證或其他規則的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="3d4ae-144">最後兩個是 _\*_方法_\*_。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-144">The last two are _*_methods_*_.</span></span> <span data-ttu-id="3d4ae-145">方法是執行單一函式的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="3d4ae-146">閱讀每個成員的名稱，應該能提供足夠的資訊，以供您或其他開發人員了解該類別的功能。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="3d4ae-147">開啟新帳戶</span><span class="sxs-lookup"><span data-stu-id="3d4ae-147">Open a new account</span></span>

<span data-ttu-id="3d4ae-148">第一個要實作的功能是開啟一個銀行帳戶。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="3d4ae-149">當客戶開啟帳戶時，他們必須提供初始餘額，以及該帳戶的一或多個擁有者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="3d4ae-150">建立類型的新物件， `BankAccount` 表示定義可指派這些值 _\*_的函_\*_ 式。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-150">Creating a new object of the `BankAccount` type means defining a _*_constructor_*_ that assigns those values.</span></span> <span data-ttu-id="3d4ae-151">「函式」（class _\*_）是名稱_\*_ 與類別相同的成員。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-151">A _*_constructor_*_ is a member that has the same name as the class.</span></span> <span data-ttu-id="3d4ae-152">它是用來初始化該類別類型的物件。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="3d4ae-153">將下列的函式加入至 `BankAccount` 類型。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="3d4ae-154">將下列程式碼放在宣告的上方 `MakeDeposit` ：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="3d4ae-155">當您使用建立物件時，會呼叫此函數 [`new`](../../language-reference/operators/new-operator.md) 。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="3d4ae-156">`Console.WriteLine("Hello World!");`以下列程式碼取代 _Program .cs \* 中的程式程式碼， (`<name>` 以您的名稱取代) ：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-156">Replace the line `Console.WriteLine("Hello World!");` in _Program.cs\* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="3d4ae-157">讓我們執行您到目前為止所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-157">Let's run what you've built so far.</span></span> <span data-ttu-id="3d4ae-158">如果您是使用 Visual Studio，請從 [**執行**] 功能表中選取 [**啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="3d4ae-159">如果您是使用命令列，請輸入 `dotnet run` 您已在其中建立專案的目錄。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="3d4ae-160">您是否注意到帳戶號碼是空白的？</span><span class="sxs-lookup"><span data-stu-id="3d4ae-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="3d4ae-161">讓我們來修正此情況。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-161">It's time to fix that.</span></span> <span data-ttu-id="3d4ae-162">帳戶號碼應該要在物件建構時指派。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="3d4ae-163">但帳戶號碼不應該由呼叫者負責建立。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="3d4ae-164">`BankAccount` 類別程式碼應該要知道如何指派新的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="3d4ae-165">最簡單的方法是以 10 位數的數字開始。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="3d4ae-166">建立每個新帳戶時就增加它。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-166">Increment it when each new account is created.</span></span> <span data-ttu-id="3d4ae-167">最後，在物件完成建構時儲存目前的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="3d4ae-168">將成員宣告加入至 `BankAccount` 類別。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="3d4ae-169">將下列程式程式碼放在類別開頭的左大括弧後面 `{` `BankAccount` ：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="3d4ae-170">這是一個資料成員。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-170">This is a data member.</span></span> <span data-ttu-id="3d4ae-171">它是 `private`，這表示它只能由 `BankAccount` 類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="3d4ae-172">這是將公共責任分開的方式 (例如，從私用執行) 的帳戶號碼， () 產生帳戶號碼的方式。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="3d4ae-173">它也是 `static`，這表示它是由所有 `BankAccount` 物件共用的。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="3d4ae-174">非靜態變數的值對於每個 `BankAccount` 物件的執行個體而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="3d4ae-175">將下列兩行新增至函式，以指派帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="3d4ae-176">將它們放在下面這一行 `this.Balance = initialBalance` ：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="3d4ae-177">輸入 `dotnet run` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="3d4ae-178">建立存款和提款</span><span class="sxs-lookup"><span data-stu-id="3d4ae-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="3d4ae-179">您的銀行帳戶必須能接受存款及提款，才算能正常運作。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="3d4ae-180">讓我們透過建立帳戶每一筆交易的日誌，來實作存款和提款。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="3d4ae-181">相較於單純地在每次交易時更新餘額，建立日誌能提供數個好處。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="3d4ae-182">該記錄可用來對所有交易進行稽核，以及管理每日餘額。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="3d4ae-183">藉由在必要時計算所有交易記錄的餘額，在任何單一交易中已修正的錯誤都會正確地在下一次計算中反映出來。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="3d4ae-184">讓我們從建立代表交易的新類型開始。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="3d4ae-185">這是一個不具任何責任的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="3d4ae-186">它需要幾個屬性。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-186">It needs a few properties.</span></span> <span data-ttu-id="3d4ae-187">建立名為 *Transaction.cs* 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="3d4ae-188">對其新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="3d4ae-189">現在，讓我們將 `Transaction` 物件的 <xref:System.Collections.Generic.List%601> 新增到 `BankAccount` 類別。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="3d4ae-190">在 *BankAccount.cs* 檔案中的函式之後，新增下列宣告：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="3d4ae-191"><xref:System.Collections.Generic.List%601> 類別需要您匯入不同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="3d4ae-192">將下列內容新增到 *BankAccount.cs* 的開頭：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="3d4ae-193">現在，讓我們正確地計算 `Balance` 。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-193">Now, let's correctly compute the `Balance`.</span></span> <span data-ttu-id="3d4ae-194">您可以藉由加總所有交易的值來找到目前的餘額。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-194">The current balance can be found by summing the values of all transactions.</span></span> <span data-ttu-id="3d4ae-195">由於程式碼目前，您只能取得帳戶的初始餘額，所以您必須更新 `Balance` 屬性。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-195">As the code is currently, you can only get the initial balance of the account, so you'll have to update the `Balance` property.</span></span> <span data-ttu-id="3d4ae-196">`public decimal Balance { get; }`以下列程式碼取代*BankAccount.cs*中的程式程式碼：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-196">Replace the line `public decimal Balance { get; }` in *BankAccount.cs* with the following code:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="3d4ae-197">此範例顯示 \***properties**_ 的重要層面。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-197">This example shows an important aspect of \***properties**_.</span></span> <span data-ttu-id="3d4ae-198">現在您會在另一個程式要求餘額時計算該值。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-198">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="3d4ae-199">您的計算會列舉所有交易，並提供總和作為目前的餘額。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-199">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="3d4ae-200">接下來，請實作 `MakeDeposit` 和 `MakeWithdrawal` 方法。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-200">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="3d4ae-201">這些方法會強制執行最後兩個規則：初始餘額必須為正數，且所有提款都不能產生負數的餘額。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-201">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="3d4ae-202">這會引入 _\*_例外_\*_ 狀況的概念。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-202">This introduces the concept of _*_exceptions_*_.</span></span> <span data-ttu-id="3d4ae-203">這是指出方法若無法完成其工作便應擲回例外狀況的標準方法。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-203">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="3d4ae-204">例外狀況的類型和與它相關的訊息會描述該錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-204">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="3d4ae-205">在這裡，如果存款的金額是負數，`MakeDeposit` 方法便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-205">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="3d4ae-206">`MakeWithdrawal`如果提款金額為負數，則方法會擲回例外狀況，或者，如果將提款結果套用負餘額，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-206">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="3d4ae-207">在清單的宣告之後，新增下列程式碼 `allTransactions` ：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-207">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="3d4ae-208">[`throw`](../../language-reference/keywords/throw.md)語句 _ 會*throws*擲回 \* 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-208">The [`throw`](../../language-reference/keywords/throw.md) statement _*throws*\* an exception.</span></span> <span data-ttu-id="3d4ae-209">目前區塊的執行會結束，而且控制權會移轉給呼叫堆疊中找到最初相符的 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-209">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="3d4ae-210">您會在稍後新增 `catch` 區塊來測試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-210">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="3d4ae-211">應該對建構函式進行一項變更來使它會新增初始交易，而不是直接更新餘額。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-211">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="3d4ae-212">由於您已撰寫 `MakeDeposit` 方法，請從建構函式呼叫它。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-212">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="3d4ae-213">完成的建構函式應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-213">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="3d4ae-214"><xref:System.DateTime.Now?displayProperty=nameWithType> 是會傳回目前日期和時間的屬性。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-214"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="3d4ae-215">若要測試這項工作，請在您的方法中新增一些存款和提款 `Main` ，並遵循建立新的程式碼 `BankAccount` ：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-215">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="3d4ae-216">接下來，請嘗試建立具有負餘額的帳戶，以測試您是否正在攔截錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-216">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="3d4ae-217">在您剛才新增的上述程式碼之後，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-217">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="3d4ae-218">您可以使用[ `try` 和 `catch` 語句](../../language-reference/keywords/try-catch.md)來標記可能會擲回例外狀況的程式碼區塊，並攔截您預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-218">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="3d4ae-219">您可以使用相同的技巧來測試擲回例外狀況的程式碼，以取得負餘額。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-219">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="3d4ae-220">在方法的結尾新增下列程式碼 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-220">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="3d4ae-221">儲存檔案並輸入 `dotnet run` 來嘗試它。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-221">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="3d4ae-222">挑戰 - 記錄所有交易</span><span class="sxs-lookup"><span data-stu-id="3d4ae-222">Challenge - log all transactions</span></span>

<span data-ttu-id="3d4ae-223">若要完成此教學課程，您可以撰寫會針對交易記錄建立 `string` 的 `GetAccountHistory` 方法。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-223">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="3d4ae-224">將此方法新增到 `BankAccount` 型別：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-224">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="3d4ae-225">此方法使用 <xref:System.Text.StringBuilder> 類別來設定針對每個交易包含單一行之字串的格式。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-225">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="3d4ae-226">您稍早已經在這些教學課程中看過字串格式設定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-226">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="3d4ae-227">一個新的字元是 `\t`。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-227">One new character is `\t`.</span></span> <span data-ttu-id="3d4ae-228">它會插入定位字元以設定輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-228">That inserts a tab to format the output.</span></span>

<span data-ttu-id="3d4ae-229">新增下列行以在 *Program.cs* 中測試它：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-229">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="3d4ae-230">執行您的程式以查看結果。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-230">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3d4ae-231">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3d4ae-231">Next steps</span></span>

<span data-ttu-id="3d4ae-232">如果您遇到困難，您可以 [在 GitHub 存放庫中](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes)看到此教學課程的來源。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-232">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="3d4ae-233">您可以繼續進行 [物件導向程式設計](object-oriented-programming.md) 教學課程。</span><span class="sxs-lookup"><span data-stu-id="3d4ae-233">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="3d4ae-234">您可以在下列文章中深入瞭解這些概念：</span><span class="sxs-lookup"><span data-stu-id="3d4ae-234">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="3d4ae-235">If 和 else 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d4ae-235">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="3d4ae-236">While 語句</span><span class="sxs-lookup"><span data-stu-id="3d4ae-236">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="3d4ae-237">Do 陳述式</span><span class="sxs-lookup"><span data-stu-id="3d4ae-237">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="3d4ae-238">For 語句</span><span class="sxs-lookup"><span data-stu-id="3d4ae-238">For statement</span></span>](../../language-reference/keywords/for.md)
