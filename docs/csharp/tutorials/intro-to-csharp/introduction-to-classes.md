---
title: 類別和物件 - C# 教學課程簡介
description: 建立您的第一個 C# 程式並探索物件導向概念
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 90abe3836292029ce7ebf26ae9be3253c4eface1
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756048"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="19209-103">探索使用類別與物件的物件導向程式設計</span><span class="sxs-lookup"><span data-stu-id="19209-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="19209-104">此教學課程要求您必須有可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="19209-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="19209-105">.NET 教學課程 [Hello World 10 分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) 的指示，說明如何在 Windows、Linux 或 macOS 上設定您的本機開發環境。</span><span class="sxs-lookup"><span data-stu-id="19209-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="19209-106">您可以在[熟悉開發工具](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="19209-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="19209-107">建立您的應用程式</span><span class="sxs-lookup"><span data-stu-id="19209-107">Create your application</span></span>

<span data-ttu-id="19209-108">使用終端機視窗，建立名為 *classes* 的目錄。</span><span class="sxs-lookup"><span data-stu-id="19209-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="19209-109">您將在該目錄建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="19209-109">You'll build your application there.</span></span> <span data-ttu-id="19209-110">在主控台視窗中變更至該目錄並輸入 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="19209-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="19209-111">這個命令會建立您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="19209-111">This command creates your application.</span></span> <span data-ttu-id="19209-112">開啟 *Program.cs*。</span><span class="sxs-lookup"><span data-stu-id="19209-112">Open *Program.cs*.</span></span> <span data-ttu-id="19209-113">其看起來應該如下：</span><span class="sxs-lookup"><span data-stu-id="19209-113">It should look like this:</span></span>

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

<span data-ttu-id="19209-114">在此教學課程中，您將建立代表銀行帳戶的新型別。</span><span class="sxs-lookup"><span data-stu-id="19209-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="19209-115">開發人員通常會在不同的文字檔中定義每個類別。</span><span class="sxs-lookup"><span data-stu-id="19209-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="19209-116">隨著程式大小增加，這麼做會使它更易於管理。</span><span class="sxs-lookup"><span data-stu-id="19209-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="19209-117">在 *classes* 目錄中，建立名為 *BankAccount.cs* 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="19209-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="19209-118">這個檔案會包含***銀行帳戶***的定義。</span><span class="sxs-lookup"><span data-stu-id="19209-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="19209-119">物件導向程式設計會以***類別***的形式建立類型來組織程式碼。</span><span class="sxs-lookup"><span data-stu-id="19209-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="19209-120">這些類別包含代表特定實體的程式碼。</span><span class="sxs-lookup"><span data-stu-id="19209-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="19209-121">`BankAccount` 類別代表銀行帳戶。</span><span class="sxs-lookup"><span data-stu-id="19209-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="19209-122">程式碼會透過方法和屬性來實作特定的作業。</span><span class="sxs-lookup"><span data-stu-id="19209-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="19209-123">在此教學課程中，銀行帳戶支援此行為：</span><span class="sxs-lookup"><span data-stu-id="19209-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="19209-124">它具有能唯一識別銀行帳戶的 10 位數數字。</span><span class="sxs-lookup"><span data-stu-id="19209-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="19209-125">它具有能儲存擁有者一個或多個名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="19209-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="19209-126">可擷取餘額。</span><span class="sxs-lookup"><span data-stu-id="19209-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="19209-127">它接受存款。</span><span class="sxs-lookup"><span data-stu-id="19209-127">It accepts deposits.</span></span>
1. <span data-ttu-id="19209-128">它接受提款。</span><span class="sxs-lookup"><span data-stu-id="19209-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="19209-129">初始餘額必須為正數。</span><span class="sxs-lookup"><span data-stu-id="19209-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="19209-130">提款不可使餘額成為負數。</span><span class="sxs-lookup"><span data-stu-id="19209-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="19209-131">定義銀行帳戶類型</span><span class="sxs-lookup"><span data-stu-id="19209-131">Define the bank account type</span></span>

<span data-ttu-id="19209-132">您可以從建立能定義該行為之類別的基礎項目來開始。</span><span class="sxs-lookup"><span data-stu-id="19209-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="19209-133">使用 **file： new** 命令建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="19209-133">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="19209-134">將它命名為 *BankAccount.cs*。</span><span class="sxs-lookup"><span data-stu-id="19209-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="19209-135">將下列程式碼新增至 *BankAccount.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="19209-135">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="19209-136">在繼續之前，讓我們先查看您所建置的內容。</span><span class="sxs-lookup"><span data-stu-id="19209-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="19209-137">`namespace` 宣告能提供以邏輯方式組織程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="19209-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="19209-138">此教學課程的規模相對較小，所以您會將所有程式碼置於一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="19209-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="19209-139">`public class BankAccount` 能定義您要建立的類別 (或類型)。</span><span class="sxs-lookup"><span data-stu-id="19209-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="19209-140">內的所有專案，以及在類別宣告之後的所有專案，都 `{` `}` 定義了類別的狀態和行為。</span><span class="sxs-lookup"><span data-stu-id="19209-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="19209-141">`BankAccount` 類別有五個***成員***。</span><span class="sxs-lookup"><span data-stu-id="19209-141">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="19209-142">前三個為***屬性***。</span><span class="sxs-lookup"><span data-stu-id="19209-142">The first three are ***properties***.</span></span> <span data-ttu-id="19209-143">屬性是資料元素，且可以具有強制執行驗證或其他規則的程式碼。</span><span class="sxs-lookup"><span data-stu-id="19209-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="19209-144">後兩個為***方法***。</span><span class="sxs-lookup"><span data-stu-id="19209-144">The last two are ***methods***.</span></span> <span data-ttu-id="19209-145">方法是執行單一函式的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="19209-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="19209-146">閱讀每個成員的名稱，應該能提供足夠的資訊，以供您或其他開發人員了解該類別的功能。</span><span class="sxs-lookup"><span data-stu-id="19209-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="19209-147">開啟新帳戶</span><span class="sxs-lookup"><span data-stu-id="19209-147">Open a new account</span></span>

<span data-ttu-id="19209-148">第一個要實作的功能是開啟一個銀行帳戶。</span><span class="sxs-lookup"><span data-stu-id="19209-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="19209-149">當客戶開啟帳戶時，他們必須提供初始餘額，以及該帳戶的一或多個擁有者的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="19209-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="19209-150">建立一個 `BankAccount` 類型的新物件，表示定義一個能指派那些值的***建構函式***。</span><span class="sxs-lookup"><span data-stu-id="19209-150">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="19209-151">***建構函式***是具有和該類別相同名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="19209-151">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="19209-152">它是用來初始化該類別類型的物件。</span><span class="sxs-lookup"><span data-stu-id="19209-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="19209-153">將下列的函式加入至 `BankAccount` 類型。</span><span class="sxs-lookup"><span data-stu-id="19209-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="19209-154">將下列程式碼放在宣告的上方 `MakeDeposit` ：</span><span class="sxs-lookup"><span data-stu-id="19209-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="19209-155">當您使用建立物件時，會呼叫此函數 [`new`](../../language-reference/operators/new-operator.md) 。</span><span class="sxs-lookup"><span data-stu-id="19209-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="19209-156">以 `Console.WriteLine("Hello World!");` 下列程式碼取代 *Program.cs* 中的程式程式碼 (取代 `<name>` 為您的名稱) ：</span><span class="sxs-lookup"><span data-stu-id="19209-156">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="19209-157">讓我們執行您到目前為止所建立的工作。</span><span class="sxs-lookup"><span data-stu-id="19209-157">Let's run what you've built so far.</span></span> <span data-ttu-id="19209-158">如果您是使用 Visual Studio，請從 [**執行**] 功能表中選取 [**啟動但不進行調試**]。</span><span class="sxs-lookup"><span data-stu-id="19209-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="19209-159">如果您是使用命令列，請輸入 `dotnet run` 您已在其中建立專案的目錄。</span><span class="sxs-lookup"><span data-stu-id="19209-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="19209-160">您是否注意到帳戶號碼是空白的？</span><span class="sxs-lookup"><span data-stu-id="19209-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="19209-161">讓我們來修正此情況。</span><span class="sxs-lookup"><span data-stu-id="19209-161">It's time to fix that.</span></span> <span data-ttu-id="19209-162">帳戶號碼應該要在物件建構時指派。</span><span class="sxs-lookup"><span data-stu-id="19209-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="19209-163">但帳戶號碼不應該由呼叫者負責建立。</span><span class="sxs-lookup"><span data-stu-id="19209-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="19209-164">`BankAccount` 類別程式碼應該要知道如何指派新的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="19209-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="19209-165">最簡單的方法是以 10 位數的數字開始。</span><span class="sxs-lookup"><span data-stu-id="19209-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="19209-166">建立每個新帳戶時就增加它。</span><span class="sxs-lookup"><span data-stu-id="19209-166">Increment it when each new account is created.</span></span> <span data-ttu-id="19209-167">最後，在物件完成建構時儲存目前的帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="19209-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="19209-168">將成員宣告加入至 `BankAccount` 類別。</span><span class="sxs-lookup"><span data-stu-id="19209-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="19209-169">將下列程式程式碼放在類別開頭的左大括弧後面 `{` `BankAccount` ：</span><span class="sxs-lookup"><span data-stu-id="19209-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="19209-170">這是一個資料成員。</span><span class="sxs-lookup"><span data-stu-id="19209-170">This is a data member.</span></span> <span data-ttu-id="19209-171">它是 `private`，這表示它只能由 `BankAccount` 類別中的程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="19209-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="19209-172">這是將公共責任分開的方式 (例如，從私用執行) 的帳戶號碼， () 產生帳戶號碼的方式。</span><span class="sxs-lookup"><span data-stu-id="19209-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="19209-173">它也是 `static`，這表示它是由所有 `BankAccount` 物件共用的。</span><span class="sxs-lookup"><span data-stu-id="19209-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="19209-174">非靜態變數的值對於每個 `BankAccount` 物件的執行個體而言都是唯一的。</span><span class="sxs-lookup"><span data-stu-id="19209-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="19209-175">將下列兩行新增至函式，以指派帳戶號碼。</span><span class="sxs-lookup"><span data-stu-id="19209-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="19209-176">將它們放在下面這一行 `this.Balance = initialBalance` ：</span><span class="sxs-lookup"><span data-stu-id="19209-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="19209-177">輸入 `dotnet run` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="19209-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="19209-178">建立存款和提款</span><span class="sxs-lookup"><span data-stu-id="19209-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="19209-179">您的銀行帳戶必須能接受存款及提款，才算能正常運作。</span><span class="sxs-lookup"><span data-stu-id="19209-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="19209-180">讓我們透過建立帳戶每一筆交易的日誌，來實作存款和提款。</span><span class="sxs-lookup"><span data-stu-id="19209-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="19209-181">相較於單純地在每次交易時更新餘額，建立日誌能提供數個好處。</span><span class="sxs-lookup"><span data-stu-id="19209-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="19209-182">該記錄可用來對所有交易進行稽核，以及管理每日餘額。</span><span class="sxs-lookup"><span data-stu-id="19209-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="19209-183">藉由在必要時計算所有交易記錄的餘額，在任何單一交易中已修正的錯誤都會正確地在下一次計算中反映出來。</span><span class="sxs-lookup"><span data-stu-id="19209-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="19209-184">讓我們從建立代表交易的新類型開始。</span><span class="sxs-lookup"><span data-stu-id="19209-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="19209-185">這是一個不具任何責任的簡單類型。</span><span class="sxs-lookup"><span data-stu-id="19209-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="19209-186">它需要幾個屬性。</span><span class="sxs-lookup"><span data-stu-id="19209-186">It needs a few properties.</span></span> <span data-ttu-id="19209-187">建立名為 *Transaction.cs* 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="19209-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="19209-188">對其新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="19209-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="19209-189">現在，讓我們將 `Transaction` 物件的 <xref:System.Collections.Generic.List%601> 新增到 `BankAccount` 類別。</span><span class="sxs-lookup"><span data-stu-id="19209-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="19209-190">在 *BankAccount.cs* 檔案中的函式之後，新增下列宣告：</span><span class="sxs-lookup"><span data-stu-id="19209-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="19209-191"><xref:System.Collections.Generic.List%601> 類別需要您匯入不同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="19209-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="19209-192">將下列內容新增到 *BankAccount.cs* 的開頭：</span><span class="sxs-lookup"><span data-stu-id="19209-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="19209-193">現在，讓我們變更 `Balance` 的報告方式。</span><span class="sxs-lookup"><span data-stu-id="19209-193">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="19209-194">報告可以透過針對所有交易的值進行加總來取得。</span><span class="sxs-lookup"><span data-stu-id="19209-194">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="19209-195">將 `BankAccount` 類別中 `Balance` 的宣告修改成如下內容：</span><span class="sxs-lookup"><span data-stu-id="19209-195">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="19209-196">此範例顯示出***屬性***的一個重要層面。</span><span class="sxs-lookup"><span data-stu-id="19209-196">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="19209-197">現在您會在另一個程式要求餘額時計算該值。</span><span class="sxs-lookup"><span data-stu-id="19209-197">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="19209-198">您的計算會列舉所有交易，並提供總和作為目前的餘額。</span><span class="sxs-lookup"><span data-stu-id="19209-198">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="19209-199">接下來，請實作 `MakeDeposit` 和 `MakeWithdrawal` 方法。</span><span class="sxs-lookup"><span data-stu-id="19209-199">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="19209-200">這些方法會強制執行最後兩個規則：初始餘額必須為正數，且所有提款都不能產生負數的餘額。</span><span class="sxs-lookup"><span data-stu-id="19209-200">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="19209-201">這也引進了***例外狀況***的概念。</span><span class="sxs-lookup"><span data-stu-id="19209-201">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="19209-202">這是指出方法若無法完成其工作便應擲回例外狀況的標準方法。</span><span class="sxs-lookup"><span data-stu-id="19209-202">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="19209-203">例外狀況的類型和與它相關的訊息會描述該錯誤。</span><span class="sxs-lookup"><span data-stu-id="19209-203">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="19209-204">在這裡，如果存款的金額是負數，`MakeDeposit` 方法便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="19209-204">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="19209-205">`MakeWithdrawal`如果提款金額為負數，則方法會擲回例外狀況，或者，如果將提款結果套用負餘額，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="19209-205">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="19209-206">在清單的宣告之後，新增下列程式碼 `allTransactions` ：</span><span class="sxs-lookup"><span data-stu-id="19209-206">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="19209-207">語句會擲回 [`throw`](../../language-reference/keywords/throw.md) 例外狀況。 **throws**</span><span class="sxs-lookup"><span data-stu-id="19209-207">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="19209-208">目前區塊的執行會結束，而且控制權會移轉給呼叫堆疊中找到最初相符的 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="19209-208">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="19209-209">您會在稍後新增 `catch` 區塊來測試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="19209-209">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="19209-210">應該對建構函式進行一項變更來使它會新增初始交易，而不是直接更新餘額。</span><span class="sxs-lookup"><span data-stu-id="19209-210">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="19209-211">由於您已撰寫 `MakeDeposit` 方法，請從建構函式呼叫它。</span><span class="sxs-lookup"><span data-stu-id="19209-211">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="19209-212">完成的建構函式應該看起來如下：</span><span class="sxs-lookup"><span data-stu-id="19209-212">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="19209-213"><xref:System.DateTime.Now?displayProperty=nameWithType> 是會傳回目前日期和時間的屬性。</span><span class="sxs-lookup"><span data-stu-id="19209-213"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="19209-214">若要測試這項工作，請在您的方法中新增一些存款和提款 `Main` ，並遵循建立新的程式碼 `BankAccount` ：</span><span class="sxs-lookup"><span data-stu-id="19209-214">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="19209-215">接下來，請嘗試建立具有負餘額的帳戶，以測試您是否正在攔截錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="19209-215">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="19209-216">在您剛才新增的上述程式碼之後，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="19209-216">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="19209-217">您可以使用[ `try` 和 `catch` 語句](../../language-reference/keywords/try-catch.md)來標記可能會擲回例外狀況的程式碼區塊，並攔截您預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="19209-217">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="19209-218">您可以使用相同的技巧來測試擲回例外狀況的程式碼，以取得負餘額。</span><span class="sxs-lookup"><span data-stu-id="19209-218">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="19209-219">在方法的結尾新增下列程式碼 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="19209-219">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="19209-220">儲存檔案並輸入 `dotnet run` 來嘗試它。</span><span class="sxs-lookup"><span data-stu-id="19209-220">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="19209-221">挑戰 - 記錄所有交易</span><span class="sxs-lookup"><span data-stu-id="19209-221">Challenge - log all transactions</span></span>

<span data-ttu-id="19209-222">若要完成此教學課程，您可以撰寫會針對交易記錄建立 `string` 的 `GetAccountHistory` 方法。</span><span class="sxs-lookup"><span data-stu-id="19209-222">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="19209-223">將此方法新增到 `BankAccount` 型別：</span><span class="sxs-lookup"><span data-stu-id="19209-223">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="19209-224">此方法使用 <xref:System.Text.StringBuilder> 類別來設定針對每個交易包含單一行之字串的格式。</span><span class="sxs-lookup"><span data-stu-id="19209-224">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="19209-225">您稍早已經在這些教學課程中看過字串格式設定的程式碼。</span><span class="sxs-lookup"><span data-stu-id="19209-225">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="19209-226">一個新的字元是 `\t`。</span><span class="sxs-lookup"><span data-stu-id="19209-226">One new character is `\t`.</span></span> <span data-ttu-id="19209-227">它會插入定位字元以設定輸出的格式。</span><span class="sxs-lookup"><span data-stu-id="19209-227">That inserts a tab to format the output.</span></span>

<span data-ttu-id="19209-228">新增下列行以在 *Program.cs* 中測試它：</span><span class="sxs-lookup"><span data-stu-id="19209-228">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="19209-229">執行您的程式以查看結果。</span><span class="sxs-lookup"><span data-stu-id="19209-229">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="19209-230">後續步驟</span><span class="sxs-lookup"><span data-stu-id="19209-230">Next steps</span></span>

<span data-ttu-id="19209-231">如果您遇到困難，您可以 [在 GitHub 存放庫中](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes)看到此教學課程的來源。</span><span class="sxs-lookup"><span data-stu-id="19209-231">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="19209-232">您可以繼續進行 [物件導向程式設計](object-oriented-programming.md) 教學課程。</span><span class="sxs-lookup"><span data-stu-id="19209-232">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="19209-233">您可以在下列文章中深入瞭解這些概念：</span><span class="sxs-lookup"><span data-stu-id="19209-233">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="19209-234">If 和 else 陳述式</span><span class="sxs-lookup"><span data-stu-id="19209-234">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="19209-235">While 語句</span><span class="sxs-lookup"><span data-stu-id="19209-235">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="19209-236">Do 陳述式</span><span class="sxs-lookup"><span data-stu-id="19209-236">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="19209-237">For 語句</span><span class="sxs-lookup"><span data-stu-id="19209-237">For statement</span></span>](../../language-reference/keywords/for.md)
