---
title: 作法：使用 Async 和 Await，同時發出多個 Web 要求 (C#)
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 57c40626fcaf0c52d09fa3a2c8b74ba8b7816677
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600236"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="4a7d7-102">作法：使用 Async 和 Await，同時發出多個 Web 要求 (C#)</span><span class="sxs-lookup"><span data-stu-id="4a7d7-102">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>
<span data-ttu-id="4a7d7-103">在非同步方法中，工作會在建立後啟動。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="4a7d7-104">由於在此方法中，必須等到工作完成後才能繼續處理，因此會將 [await](../../../../csharp/language-reference/keywords/await.md) 運算子套用至工作。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-104">The [await](../../../../csharp/language-reference/keywords/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="4a7d7-105">通常，工作會在建立後等候完成，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="4a7d7-106">不過，如果您的程式有其他要完成的工作不需要等候此工作完成，您可以將建立工作與等候工作分開進行。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="4a7d7-107">從工作啟動到等候完成的這段期間，您可以啟動其他工作。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="4a7d7-108">其他工作會以隱含方式平行執行，但不會建立其他任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="4a7d7-109">下列程式會啟動三個非同步的網頁下載，然後依呼叫順序等候完成。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="4a7d7-110">請注意，當您執行此程式時，這些工作不一定會依建立和等候順序完成。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="4a7d7-111">這些工作會在建立後開始執行，而且其中一或多個工作可能會在此方法到達 await 運算式之前就已完成。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a7d7-112">若要完成此專案，您必須在電腦上安裝 Visual Studio 2012 或更高版本以及 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="4a7d7-113">如需同時啟動多個工作的其他範例，請參閱[如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-113">For another example that starts multiple tasks at the same time, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="4a7d7-114">您可以從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)下載此範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="4a7d7-115">若要設定專案</span><span class="sxs-lookup"><span data-stu-id="4a7d7-115">To set up the project</span></span>  
  
1. <span data-ttu-id="4a7d7-116">若要設定 WPF 應用程式，請完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="4a7d7-117">您可以在[逐步解說：使用 Async 和 Await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) 中，找到這些步驟的詳細指示。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="4a7d7-118">建立 WPF 應用程式，其中包含一個文字方塊和一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="4a7d7-119">將按鈕命名為 `startButton`，並將文字方塊命名為 `resultsTextBox`。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="4a7d7-120">加入 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="4a7d7-121">在 MainWindow.xaml.cs 檔案中，新增 `System.Net.Http` 的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="4a7d7-122">新增程式碼</span><span class="sxs-lookup"><span data-stu-id="4a7d7-122">To add the code</span></span>  
  
1. <span data-ttu-id="4a7d7-123">在設計視窗 MainWindow.xaml 中，按兩下此按鈕以在 MainWindow.xaml.cs 中建立 `startButton_Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="4a7d7-124">將下列程式碼複製並貼到 MainWindow.xaml.cs 中的 `startButton_Click` 主體。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="4a7d7-125">此程式碼會呼叫非同步方法 `CreateMultipleTasksAsync` 來驅動應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="4a7d7-126">將下列支援方法新增至專案：</span><span class="sxs-lookup"><span data-stu-id="4a7d7-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="4a7d7-127">`ProcessURLAsync` 使用 <xref:System.Net.Http.HttpClient> 方法，將網站內容下載為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="4a7d7-128">然後，支援方法 `ProcessURLAsync` 會顯示並傳回陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="4a7d7-129">`DisplayResults` 會顯示每個 URL 的位元組陣列中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="4a7d7-130">當每個工作完成下載時，即會顯示此畫面。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="4a7d7-131">將下列方法複製並貼到 MainWindow.xaml.cs 中的 `startButton_Click` 事件處理常式之後。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. <span data-ttu-id="4a7d7-132">最後，定義 `CreateMultipleTasksAsync` 方法以執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="4a7d7-133">方法宣告 `HttpClient` 物件，需要存取 `ProcessURLAsync` 中的方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="4a7d7-134">方法會建立並啟動三個 <xref:System.Threading.Tasks.Task%601> 類型的工作，其中 `TResult` 是整數。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="4a7d7-135">當每個工作完成時，`DisplayResults` 會顯示工作的 URL 和下載內容的長度。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="4a7d7-136">因為工作是以非同步方式執行，所以結果出現的順序可能會因宣告的順序而有所不同。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="4a7d7-137">此方法會等候每個工作完成。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="4a7d7-138">每個 `await` 運算子會暫停執行 `CreateMultipleTasksAsync`，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="4a7d7-139">此運算子也會從每個完成的工作擷取透過呼叫 `ProcessURLAsync` 傳回的值。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="4a7d7-140">完成工作並擷取整數值之後，此方法會加總網站的長度並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="4a7d7-141">將下列方法複製並貼到您的方案中。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-141">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults   
        // displays its length.  
        Task<int> download1 =   
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="4a7d7-142">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="4a7d7-143">執行此程式幾次，確認這三個工作不一定會依相同順序完成，而且其完成順序不一定是建立和等候順序。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a7d7-144">範例</span><span class="sxs-lookup"><span data-stu-id="4a7d7-144">Example</span></span>  
 <span data-ttu-id="4a7d7-145">下列程式碼包含完整的範例。</span><span class="sxs-lookup"><span data-stu-id="4a7d7-145">The following code contains the full example.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults   
            // displays its length.  
            Task<int> download1 =   
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a7d7-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a7d7-146">See also</span></span>

- [<span data-ttu-id="4a7d7-147">逐步解說：使用 Async 和 Await 存取 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="4a7d7-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="4a7d7-148">使用 Async 和 Await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="4a7d7-148">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="4a7d7-149">如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="4a7d7-149">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
