---
title: "標準的 .NET 事件模式"
description: "了解 .NET 事件模式、如何建立標準事件來源，以及如何訂閱和處理程式碼中的標準事件。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: ff36438ab02ae6822d7df8425a615aef2ddbf2f2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="standard-net-event-patterns"></a>標準的 .NET 事件模式

[上一步](events-overview.md)

.NET 事件通常會遵循少數已知的模式。 這些模式的標準化表示開發人員可以利用這些標準模式的知識，它們可套用至任何 .NET 事件程式。

讓我們先了解這些標準模式，以便您有建立標準事件來源所需的全部知識，在程式碼中訂閱並處理標準事件。

## <a name="event-delegate-signatures"></a>事件委派簽章

.NET 事件委派的標準簽章是︰

```csharp
void OnEventRaised(object sender, EventArgs args);
```

傳回型別為 void。 事件以委派為基礎，而且是多點傳送的委派。 支援任何事件來源的多個訂閱者。 來自方法的單一傳回值無法擴充至多個事件訂閱者。 引發事件後，事件來源看到哪一個傳回值？ 您會在本文後面看到如何建立向事件來源報告資訊之支援事件訂閱者的事件通訊協定。

引數清單包含兩個引數︰寄件者及事件引數。 `sender` 的編譯時間類型是 `System.Object`，即使您可能知道一向正確之衍生程度較高的類型。 依照慣例使用 `object`。

第二個引數一向是衍生自 `System.EventArgs` 的類型。 (您會在[下一篇](modern-events.md)看到此慣例已不再強制執行。)如果您的事件類型不需要任何其他引數，您仍要提供兩個引數。
您應該使用特殊值 `EventArgs.Empty` 來表示您的事件不包含任何額外的資訊。

我們要組建一個類別，列出目錄中的檔案，或其遵循模式的任一子目錄。 每次找到符合模式的檔案，此元件都會引發事件。

使用事件模型可提供一些設計優勢。 您可以建立多個事件接聽程式，於找到搜尋的檔案時，執行不同的動作。 結合不同的接聽程式可以建立更強固的演算法。

以下是尋找搜尋檔案的初始事件引數宣告︰ 

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

即使這個類型看起來像是小型的僅限資料類型，您也應該遵循規範，讓它成為參考 (`class`) 類型。 這表示參考會傳遞引數物件，而所有訂閱者都會檢視資料的任何更新。 第一個版本是不可變的物件。 您應該更偏好讓事件引數類型中的屬性成為不可變。 這樣一來，某個訂閱者就無法在其他訂閱者看到值之前變更值。 (以下是這個情況的例外狀況。)  

接下來，我們需要在 FileSearcher 類別中建立事件宣告。 利用 `EventHandler<T>` 類型表示您還不需要建立另一個類型定義。 您只要使用一般的特製化即可。

我們要填寫 FileSearcher 類別，以搜尋符合模式的檔案，並在發現相符項目時引發正確的事件。

```csharp
public class FileSearcher
{
    public event EventHandler<FileFoundArgs> FileFound;

    public void Search(string directory, string searchPattern)
    {
        foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
        {
            FileFound?.Invoke(this, new FileFoundArgs(file));
        }
    }
}
```

## <a name="definining-and-raising-field-like-events"></a>定義及引發的欄位型事件

將事件新增至類別的最簡單方式，是將該事件宣告為公用欄位，如上例所示︰

```csharp
public event EventHandler<FileFoundArgs> FileFound;
```

這看起來像是宣告公用欄位，像是不正確的物件導向做法。 您想要透過屬性或方法保護資料存取。 雖然這看起來不像正確的做法，但編譯器產生的程式碼確實會建立包裝函式，事件物件只能以安全的方式存取。 欄位型事件唯一可用的作業是新增處理常式︰

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);
lister.FileFound += onFileFound;
```

以及移除處理常式：

```csharp
lister.FileFound -= onFileFound;
```

請注意，處理常式有區域變數。 如果使用了 Lambda 的主體，移除就無法正確運作。 它會有不同的委派執行個體，不以無訊息模式執行任何動作。

在類別之外的程式碼無法引發事件，也不能執行任何其他作業。

## <a name="returning-values-from-event-subscribers"></a>從事件訂閱者傳回值

您的簡單版本運作得很好。 讓我們新增另一項功能︰取消。

當您引發找到的事件時，接聽程式應該能夠停止進一步的處理，如果此檔案是搜尋到的最後一個檔案。

事件處理常式不傳回值，因此您需要以另一種方式進行通訊。 標準事件模式使用 EventArgs 物件包含事件訂閱者可用於通訊取消的欄位。

根據「取消」合約的語意，有兩種不同的模式可以使用。 這兩種情況下，您都會將布林值欄位新增至找到之檔案事件的 EventArguments。 

一種模式可讓任何一位訂閱者取消作業。
針對此模式，新的欄位會初始化為 `false`。 任何訂閱者都可以將它變更為 `true`。 在所有訂閱者皆已看過引發的事件之後，FileSearcher 元件會檢查布林值並採取動作。

如果所有的訂閱者都想要取消作業，第二個模式只會取消作業。 在此模式中，新的欄位會初始化以指出應該取消的作業，而任何訂閱者皆可將它變更為表示作業應該繼續進行。
在所有訂閱者皆已看過引發的事件之後，FileSearcher 元件會檢查布林值並採取動作。 此模式有一個額外步驟︰元件需要知道是否有任何訂閱者已看到此事件。 如果沒有任何訂閱者，則欄位會指出取消不正確。

我們要實作本例的第一個版本。 您需要將布林值欄位新增至 FileFoundEventArgs 類型︰

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }
    public bool CancelRequested { get; set; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

這個新欄位應該初始化為 false，因此取消要有理由。 這是布林值欄位的預設值，因此會自動進行。 元件僅有的其他變更是在引發事件後檢查旗標，查看是否有任何訂閱者曾要求取消︰

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

此模式的優點之一是，它不是一項重大變更。
以前沒有任何訂閱者要求取消，現在也沒有。 沒有任何訂閱者程式碼需要更新，除非它們要支援新的取消通訊協定。 它是非常鬆散的耦合。

我們要更新訂閱者，以便它在找到第一個可執行檔之後，立刻要求取消︰

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a>新增另一個事件宣告

我們要再新增一項功能，示範事件的其他語言慣例。 新增 `Search()` 方法的多載，此方法會周遊所有子目錄搜尋檔案。

這在有許多子目錄的目錄中可能會是冗長的作業。 新增在每個新目錄搜尋開始時要引發的事件。 這可讓訂閱者追蹤進度，將使用者更新為要處理的使用者。 您到目前為止建立的所有範例都是公用的。 讓我們把這個變成內部事件。 這表示您也可以將用於引數的類型變成內部。

您會從建立新的 EventArgs 衍生類別以報告新目錄和進度開始。 

```csharp
internal class SearchDirectoryArgs : EventArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs)
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
``` 

同樣地，您可以依照建議，為事件引數建立不可變的參考類型。

接下來定義事件。 這次，您要使用不同的語法。 除了使用欄位語法，您也可以使用新增和移除處理常式來明確建立屬性。 在本例中，此專案的這些處理常式中不需要額外的程式碼，但這會顯示您建立它們的方式。

```csharp
internal event EventHandler<SearchDirectoryArgs> DirectoryChanged
{
    add { directoryChanged += value; }
    remove { directoryChanged -= value; }
}
private EventHandler<SearchDirectoryArgs> directoryChanged;
```

您在此撰寫的程式碼，有很多方式會鏡像編譯器為欄位事件定義產生的程式碼，這些程式碼您稍早已見過。 您建立事件所用的語法和用於[屬性](properties.md)的語法極其相似。 請注意，處理常式有不同的名稱︰`add` 和 `remove`。 分別表示訂閱事件，或取消訂閱事件。 請注意，您也必須宣告私用支援欄位來儲存事件變數。 它會初始化為 Null。

接下來，我們要新增 Search() 方法的多載，此方法會周遊子目錄並引發這兩個事件。 達成這個目的最簡單方式，是使用預設引數來指定您想要搜尋所有目錄︰

```csharp
public void Search(string directory, string searchPattern, bool searchSubDirs = false)
{
    if (searchSubDirs)
    {
        var allDirectories = Directory.GetDirectories(directory, "*.*", SearchOption.AllDirectories);
        var completedDirs = 0;
        var totalDirs = allDirectories.Length + 1;
        foreach (var dir in allDirectories)
        {
            directoryChanged?.Invoke(this,
                new SearchDirectoryArgs(dir, totalDirs, completedDirs++));
            // Recursively search this child directory:
            SearchDirectory(dir, searchPattern);
        }
        // Include the Current Directory:
        directoryChanged?.Invoke(this,
            new SearchDirectoryArgs(directory, totalDirs, completedDirs++));
        SearchDirectory(directory, searchPattern);
    }
    else
    {
        SearchDirectory(directory, searchPattern);
    }
}

private void SearchDirectory(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

此時，您可以執行應用程式呼叫多載以搜尋所有子目錄。 新的 `ChangeDirectory` 事件沒有任何訂閱者，但使用 `?.Invoke()` 慣用語可確保其正確運作。

 我們要新增處理常式寫入一行程式碼，在主控台視窗中顯示進度。 

```csharp
lister.DirectoryChanged += (sender, eventArgs) =>
{
    Console.Write($"Entering '{eventArgs.CurrentSearchDirectory}'.");
    Console.WriteLine($" {eventArgs.CompletedDirs} of {eventArgs.TotalDirs} completed...");
};
```

您已見過整個 .NET 生態系統所遵循的模式。
了解這些模式和慣例，您就能夠快速撰寫慣用的 C# 和 .NET。

接下來，您會在最新版本的 .NET 中看到這些模式的某些變更。

[下一步](modern-events.md)
