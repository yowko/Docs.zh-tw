---
title: 類別和物件 - C# 教學課程簡介
description: 建立您的第一個 C# 程式並探索物件導向概念
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 5edb2d7b11caace2d794b7958dfeb75ef502ee2b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396869"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>探索使用類別與物件的物件導向程式設計

此教學課程要求您必須有可用於開發的電腦。 .NET 教學課程[Hello World 在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)，有在 Windows、Linux 或 macOS 上設定本機開發環境的指示。 您可以在[熟悉開發工具](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。

## <a name="create-your-application"></a>建立您的應用程式

使用終端機視窗，建立名為 *classes* 的目錄。 您將在該目錄建立應用程式。 在主控台視窗中變更至該目錄並輸入 `dotnet new console`。 這個命令會建立您的應用程式。 開啟*Program.cs*。 它看起來應該如下所示：

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

在此教學課程中，您將建立代表銀行帳戶的新型別。 開發人員通常會在不同的文字檔中定義每個類別。 隨著程式大小增加，這麼做會使它更易於管理。 在 *classes* 目錄中，建立名為 *BankAccount.cs* 的新檔案。

這個檔案會包含***銀行帳戶***的定義。 物件導向程式設計會以***類別***的形式建立類型來組織程式碼。 這些類別包含代表特定實體的程式碼。 `BankAccount` 類別代表銀行帳戶。 程式碼會透過方法和屬性來實作特定的作業。 在此教學課程中，銀行帳戶支援此行為：

1. 它具有能唯一識別銀行帳戶的 10 位數數字。
1. 它具有能儲存擁有者一個或多個名稱的字串。
1. 可擷取餘額。
1. 它接受存款。
1. 它接受提款。
1. 初始餘額必須為正數。
1. 提款不可使餘額成為負數。

## <a name="define-the-bank-account-type"></a>定義銀行帳戶類型

您可以從建立能定義該行為之類別的基礎項目來開始。 使用**file： new**命令建立新檔案。 將它命名為*BankAccount.cs*。 將下列程式碼新增至*BankAccount.cs*檔案：

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

在繼續之前，讓我們先查看您所建置的內容。  `namespace` 宣告能提供以邏輯方式組織程式碼的方式。 此教學課程的規模相對較小，所以您會將所有程式碼置於一個命名空間。

`public class BankAccount` 能定義您要建立的類別 (或類型)。 在和中，在類別宣告之後的所有專案都會 `{` `}` 定義類別的狀態和行為。 `BankAccount` 類別有五個***成員***。 前三個為***屬性***。 屬性是資料元素，且可以具有強制執行驗證或其他規則的程式碼。 後兩個為***方法***。 方法是執行單一函式的程式碼區塊。 閱讀每個成員的名稱，應該能提供足夠的資訊，以供您或其他開發人員了解該類別的功能。

## <a name="open-a-new-account"></a>開啟新帳戶

第一個要實作的功能是開啟一個銀行帳戶。 當客戶開啟帳戶時，他們必須提供初始餘額，以及該帳戶的一或多個擁有者的相關資訊。

建立一個 `BankAccount` 類型的新物件，表示定義一個能指派那些值的***建構函式***。 ***建構函式***是具有和該類別相同名稱的成員。 它是用來初始化該類別類型的物件。 將下列的函式加入至 `BankAccount` 類型。 將下列程式碼放在宣告的上方 `MakeDeposit` ：

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

當您使用建立物件時，會呼叫函式 [`new`](../../language-reference/operators/new-operator.md) 。 以 `Console.WriteLine("Hello World!");` 下列程式碼取代*Program.cs*中的行（以 `<name>` 您的名稱取代）：

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

讓我們執行到目前為止所建立的內容。 如果您使用 Visual Studio，請從 [**執行**] 功能表中選取 [**啟動但不進行調試**]。 如果您使用的是命令列，請 `dotnet run` 在您已建立專案的目錄中輸入。

您是否注意到帳戶號碼是空白的？ 讓我們來修正此情況。 帳戶號碼應該要在物件建構時指派。 但帳戶號碼不應該由呼叫者負責建立。 `BankAccount` 類別程式碼應該要知道如何指派新的帳戶號碼。  最簡單的方法是以 10 位數的數字開始。 建立每個新帳戶時就增加它。 最後，在物件完成建構時儲存目前的帳戶號碼。

將成員宣告加入至 `BankAccount` 類別。 將下列程式程式碼放在類別開頭的左大括弧後面 `{` `BankAccount` ：

```csharp
private static int accountNumberSeed = 1234567890;
```

這是一個資料成員。 它是 `private`，這表示它只能由 `BankAccount` 類別中的程式碼存取。 這是一種將公開責任（如擁有帳戶號碼）與私用實施（產生帳戶號碼的方式）分開的方式。 它也是 `static`，這表示它是由所有 `BankAccount` 物件共用的。 非靜態變數的值對於每個 `BankAccount` 物件的執行個體而言都是唯一的。 將下列兩行新增至函式，以指派帳戶號碼。 將它們放在下面這一行後面 `this.Balance = initialBalance` ：

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

輸入 `dotnet run` 來查看結果。

## <a name="create-deposits-and-withdrawals"></a>建立存款和提款

您的銀行帳戶必須能接受存款及提款，才算能正常運作。 讓我們透過建立帳戶每一筆交易的日誌，來實作存款和提款。 相較於單純地在每次交易時更新餘額，建立日誌能提供數個好處。 該記錄可用來對所有交易進行稽核，以及管理每日餘額。 藉由在必要時計算所有交易記錄的餘額，在任何單一交易中已修正的錯誤都會正確地在下一次計算中反映出來。

讓我們從建立代表交易的新類型開始。 這是一個不具任何責任的簡單類型。 它需要幾個屬性。 建立名為 *Transaction.cs* 的新檔案。 對其新增下列程式碼：

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

現在，讓我們將 `Transaction` 物件的 <xref:System.Collections.Generic.List%601> 新增到 `BankAccount` 類別。 在*BankAccount.cs*檔案中的函式後面新增下列宣告：

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

<xref:System.Collections.Generic.List%601> 類別需要您匯入不同的命名空間。 將下列內容新增到 *BankAccount.cs* 的開頭：

```csharp
using System.Collections.Generic;
```

現在，讓我們變更 `Balance` 的報告方式。  報告可以透過針對所有交易的值進行加總來取得。 將 `BankAccount` 類別中 `Balance` 的宣告修改成如下內容：

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

此範例顯示出***屬性***的一個重要層面。 現在您會在另一個程式要求餘額時計算該值。 您的計算會列舉所有交易，並提供總和作為目前的餘額。

接下來，請實作 `MakeDeposit` 和 `MakeWithdrawal` 方法。 這些方法會強制執行最後兩個規則：初始餘額必須為正數，且所有提款都不能產生負數的餘額。

這也引進了***例外狀況***的概念。 這是指出方法若無法完成其工作便應擲回例外狀況的標準方法。 例外狀況的類型和與它相關的訊息會描述該錯誤。 在這裡，如果存款的金額是負數，`MakeDeposit` 方法便會擲回例外狀況。 `MakeWithdrawal`如果提款金額為負數，或如果套用提款結果為負餘額，此方法就會擲回例外狀況。 在清單的宣告後面新增下列程式碼 `allTransactions` ：

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

語句會擲回 [`throw`](../../language-reference/keywords/throw.md) 例外狀況。 **throws** 目前區塊的執行會結束，而且控制權會移轉給呼叫堆疊中找到最初相符的 `catch` 區塊。 您會在稍後新增 `catch` 區塊來測試此程式碼。

應該對建構函式進行一項變更來使它會新增初始交易，而不是直接更新餘額。 由於您已撰寫 `MakeDeposit` 方法，請從建構函式呼叫它。 完成的建構函式應該看起來如下：

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType> 是會傳回目前日期和時間的屬性。 請在方法中新增幾個存款和提款 `Main` ，然後遵循建立新的程式碼，以測試此項 `BankAccount` ：

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

接下來，測試您是否藉由嘗試建立具有負餘額的帳戶來攔截錯誤狀況。 在您剛才新增的上述程式碼之後，新增下列程式碼：

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

您可以使用[ `try` 和 `catch` 語句](../../language-reference/keywords/try-catch.md)來標記可能會擲回例外狀況的程式碼區塊，並攔截您所預期的那些錯誤。 您可以使用相同的技巧來測試擲回例外狀況的程式碼是否負餘額。 在方法的結尾新增下列程式碼 `Main` ：

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

儲存檔案並輸入 `dotnet run` 來嘗試它。

## <a name="challenge---log-all-transactions"></a>挑戰 - 記錄所有交易

若要完成此教學課程，您可以撰寫會針對交易記錄建立 `string` 的 `GetAccountHistory` 方法。 將此方法新增到 `BankAccount` 型別：

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

此方法使用 <xref:System.Text.StringBuilder> 類別來設定針對每個交易包含單一行之字串的格式。 您稍早已經在這些教學課程中看過字串格式設定的程式碼。 一個新的字元是 `\t`。 它會插入定位字元以設定輸出的格式。

新增下列行以在 *Program.cs* 中測試它：

```csharp
Console.WriteLine(account.GetAccountHistory());
```

執行程式以查看結果。

## <a name="next-steps"></a>後續步驟

如果您停滯，可以[在我們的 GitHub 存放庫中](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/)看到本教學課程的來源。

恭喜，您已完成所有 C# 簡介教學課程。 如果您想要深入瞭解，請嘗試我們的[教學](../index.md)課程。
