---
title: "快速入門 - 類別簡介 - C# 指南"
description: "建立您的第一個 C# 程式並探索物件導向概念"
author: billwagner
ms.author: wiwagn
ms.date: 10/11/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4e15b1b12b9420ca1781eca3f2578fa24c9ec82a
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="introduction-to-classes"></a>類別簡介

本快速入門需要您具備可用於開發的電腦。 .NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。 您可以在[本機快速入門簡介](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。

## <a name="create-your-application"></a>建立您的應用程式

使用終端機視窗，建立名為 **classes** 的目錄。 您將在該目錄建立應用程式。 在主控台視窗中變更至該目錄並輸入 `dotnet new console`。 這個命令會建立您的應用程式。 開啟 **Program.cs**。 內容應該看起來如下：

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

在此快速入門中，您將建立代表銀行帳戶的新類型。 開發人員通常會在不同的文字檔中定義每個類別。 隨著程式大小增加，這麼做會使它更易於管理。  在 **classes** 目錄中，建立名為 **BankAccount.cs** 的新檔案。 

這個檔案會包含***銀行帳戶***的定義。 物件導向程式設計會以***類別***的形式建立類型來組織程式碼。 這些類別包含代表特定實體的程式碼。 `BankAccount` 類別代表銀行帳戶。 程式碼會透過方法和屬性來實作特定的作業。 在此快速入門中，銀行帳戶支援此行為：

1. 它具有能唯一識別銀行帳戶的 10 位數數字。
1. 它具有能儲存擁有者一個或多個名稱的字串。
1. 可擷取餘額。
1. 它接受存款。
1. 它接受提款。
1. 初始餘額必須為正數。
1. 提款不可使餘額成為負數。

## <a name="define-the-bank-account-type"></a>定義銀行帳戶類型

您可以從建立能定義該行為之類別的基礎項目來開始。 內容應該看起來如下：

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

在繼續之前，讓我們先查看您所建置的內容。  `namespace` 宣告能提供以邏輯方式組織程式碼的方式。 此快速入門的規模相對較小，所以您會將所有程式碼置於一個命名空間。 

`public class BankAccount` 能定義您要建立的類別 (或類型)。 類別宣告後面的 `{` 和 `}` 之內的所有內容，皆定義該類別的行為。 `BankAccount` 類別有五個***成員***。 前三個為***屬性***。 屬性是資料元素，且可以具有強制執行驗證或其他規則的程式碼。 後兩個為***方法***。 方法是執行單一功能的程式碼區塊。 閱讀每個成員的名稱，應該能提供足夠的資訊，以供您或其他開發人員了解該類別的功能。

## <a name="open-a-new-account"></a>開啟新帳戶

第一個要實作的功能是開啟一個銀行帳戶。 當客戶開啟帳戶時，他們必須提供初始餘額，以及該帳戶的一或多個擁有者的相關資訊。 

建立一個 `BankAccount` 類型的新物件，表示定義一個能指派那些值的***建構函式***。 ***建構函式***是具有和該類別相同名稱的成員。 它是用來初始化該類別類型的物件。 將下列建構函式新增到 `BankAccount` 類型：

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

當您使用 [`new`](../language-reference/keywords/new.md) 建立物件時，系統便會呼叫建構函式。 以下列行取代 ***program.cs*** 中的 `Console.WriteLine("Hello World!");` 行 (以您的名字取代 `<name>`)：

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

輸入 `dotnet run` 看看會發生什麼事。  

您是否注意到帳戶號碼是空白的？ 讓我們來修正此情況。 帳戶號碼應該要在物件建構時指派。 但帳戶號碼不應該由呼叫者負責建立。 `BankAccount` 類別程式碼應該要知道如何指派新的帳戶號碼。  最簡單的方法是以 10 位數的數字開始。 建立每個新帳戶時就增加它。 最後，在物件完成建構時儲存目前的帳戶號碼。

將下列成員宣告新增到 `BankAccount` 類別：

```csharp
private static int accountNumberSeed = 1234567890;
```

這是一個資料成員。 它是 `private`，這表示它只能由 `BankAccount` 類別中的程式碼存取。 這是將公開責任 (例如具有帳戶號碼) 和私用實作 (帳戶號碼產生的方式) 區隔開來的方法。將下列兩行新增到建構函式來指派帳戶號碼：

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

輸入 `dotnet run` 來查看結果。

## <a name="create-deposits-and-withdrawals"></a>建立存款和提款

您的銀行帳戶必須能接受存款及提款，才算能正常運作。 讓我們透過建立帳戶每一筆交易的日誌，來實作存款和提款。 相較於單純地在每次交易時更新餘額，建立日誌能提供數個好處。 該記錄可用來對所有交易進行稽核，以及管理每日餘額。 藉由在必要時計算所有交易記錄的餘額，在任何單一交易中已修正的錯誤都會正確地在下一次計算中反映出來。

讓我們從建立代表交易的新類型開始。 這是一個不具任何責任的簡單類型。 它需要幾個屬性。 建立名為 ***Transaction.cs*** 的新檔案。 將下列程式碼加入該檔案：

[!code-csharp[Transaction](../../../samples/csharp/classes-quickstart/Transaction.cs "Transaction declaration")]

現在，讓我們將 `Transaction` 物件的 <xref:System.Collections.Generic.List%601> 新增到 `BankAccount` 類別。 新增下列宣告：

[!code-csharp[TransactionDecl](../../../samples/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration "Transaction declaration")]

<xref:System.Collections.Generic.List%601> 類別需要您匯入不同的命名空間。 將下列內容新增到 **BankAccount.cs** 的開頭：

```csharp
using System.Collections.Generic;
```

現在，讓我們變更 `Balance` 的報告方式。  報告可以透過針對所有交易的值進行加總來取得。 將 `BankAccount` 類別中 `Balance` 的宣告修改成如下內容：

[!code-csharp[BalanceComputation](../../../samples/csharp/classes-quickstart/BankAccount.cs#BalanceComputation "Computing the balance")]

此範例顯示出***屬性***的一個重要層面。 現在您會在另一個程式要求餘額時計算該值。 您的計算會列舉所有交易，並提供總和作為目前的餘額。

接下來，請實作 `MakeDeposit` 和 `MakeWithdrawal` 方法。 這些方法會強制執行最後兩個規則：初始餘額必須為正數，且所有提款都不能產生負數的餘額。 

這也引進了***例外狀況***的概念。 這是指出方法若無法完成其工作便應擲回例外狀況的標準方法。 例外狀況的類型和與它相關的訊息會描述該錯誤。 在這裡，如果存款的金額是負數，`MakeDeposit` 方法便會擲回例外狀況。 如果提款金額是負數，或如果套用提款金額會造成負數的餘額，則 `MakeWithdrawal` 方法會擲回例外狀況：

[!code-csharp[DepositAndWithdrawal](../../../samples/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal "Make deposits and withdrawals")]

[`throw`](../language-reference/keywords/throw.md) 陳述式會**擲回**例外狀況。 目前方法的執行會結束，並會在找到對應的 `catch` 區塊時繼續。 您會在稍後新增 `catch` 區塊來測試此程式碼。

應該對建構函式進行一項變更來使它會新增初始交易，而不是直接更新餘額。 由於您已撰寫 `MakeDeposit` 方法，請從建構函式呼叫它。 完成的建構函式應該看起來如下：

[!code-csharp[Constructor](../../../samples/csharp/classes-quickstart/BankAccount.cs#Constructor "The final version of the constructor")]

<xref:System.DateTime.Now?displayProperty=nameWithType> 是會傳回目前日期和時間的屬性。 透過在您的 `Main` 方法中新增一些存款和提款來測試此屬性：

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "friend paid me back");
Console.WriteLine(account.Balance);
```

接下來，透過建立具有負數餘額的帳戶，來測試是否能攔截到錯誤情況：

```csharp
// Test that the initial balances must be positive:
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

使用 [`try` 和 `catch` 陳述式](../language-reference/keywords/try-catch.md)來標記可能會擲回例外狀況的程式碼區塊，並攔截您所預期的那些錯誤。 您可以使用同樣的技巧來測試會針對負數餘額進行擲回的程式碼：

```csharp
// Test for a negative balance
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

儲存檔案並輸入 `dotnet run` 來嘗試它。

## <a name="challenge---log-all-transactions"></a>挑戰 - 記錄所有交易

若要完成此快速入門，您必須能撰寫會針對交易記錄建立 `string` 的 `GetAccountHistory` 方法。 將此方法新增到 `BankAccount` 類型：

[!code-csharp[History](../../../samples/csharp/classes-quickstart/BankAccount.cs#History "Display transaction history")]

此方法使用 <xref:System.Text.StringBuilder> 類別來設定針對每個交易包含單一行之字串的格式。 您已經在稍早於這些快速入門中看過字串格式設定的程式碼。 一個新的字元是 `\t`。 它會插入定位字元以設定輸出的格式。

新增下列行以在 **Program.cs** 中測試它：

```csharp
Console.WriteLine(account.GetAccountHistory());
```

輸入 `dotnet run` 來查看結果。

## <a name="next-steps"></a>後續步驟

如果遇到問題，您可以在我們的 [GitHub 存放庫](https://github.com/dotnet/docs/tree/master/samples/csharp/classes-quickstart/) \(英文\) 中查看此快速入門的原始程式碼

恭喜，您已經完成所有的快速入門。 如果您想要學習更多，請嘗試我們的[教學課程](../tutorials/index.md)
