---
title: '如何使用 async 和 await，同時發出多個 web 要求（c #）'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 0cfc1d6d1d59dc74fcf5990abb0a9d980a83d7b0
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241795"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="6f4b3-102">如何使用 async 和 await，同時發出多個 web 要求（c #）</span><span class="sxs-lookup"><span data-stu-id="6f4b3-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="6f4b3-103">在非同步方法中，工作會在建立時啟動。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-103">In an async method, tasks are started when they're created.</span></span> <span data-ttu-id="6f4b3-104">[Await](../../../language-reference/operators/await.md)運算子會套用至方法中的工作點，在此情況下無法繼續處理，直到工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can't continue until the task finishes.</span></span> <span data-ttu-id="6f4b3-105">通常會在建立工作時立即等待，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-105">Often a task is awaited as soon as it's created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="6f4b3-106">不過，如果您的程式有其他工作要完成，而不是相依于工作完成，您可以區分建立工作，使其無法等候工作。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn't depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="6f4b3-107">從工作啟動到等候完成的這段期間，您可以啟動其他工作。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="6f4b3-108">其他工作會以隱含方式平行執行，但不會建立其他任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="6f4b3-109">下列程式會啟動三個非同步 web 下載，然後依照呼叫的順序來等候它們。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they're called.</span></span> <span data-ttu-id="6f4b3-110">請注意，當您執行程式時，工作不一定會依其建立和等候的順序完成。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-110">Notice, when you run the program, that the tasks don't always finish in the order in which they're created and awaited.</span></span> <span data-ttu-id="6f4b3-111">它們會在建立時開始執行，而且一或多個工作可能會在方法到達 await 運算式之前完成。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-111">They start to run when they're created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f4b3-112">若要完成此專案，您必須在電腦上安裝 Visual Studio 2012 或更高版本以及 .NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="6f4b3-113">如需同時啟動多個工作的另一個範例，請參閱[如何使用 system.threading.tasks.task.whenall 擴充非同步逐步解說（c #）](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="6f4b3-114">您可以從[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)下載此範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="6f4b3-115">若要設定專案</span><span class="sxs-lookup"><span data-stu-id="6f4b3-115">To set up the project</span></span>  
  
1. <span data-ttu-id="6f4b3-116">若要設定 WPF 應用程式，請完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="6f4b3-117">您可以在[逐步解說：使用 Async 和 Await 存取 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) 中，找到這些步驟的詳細指示。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="6f4b3-118">建立 WPF 應用程式，其中包含一個文字方塊和一個按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="6f4b3-119">將按鈕命名為 `startButton`，並將文字方塊命名為 `resultsTextBox`。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="6f4b3-120">加入 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="6f4b3-121">在 MainWindow.xaml.cs 檔案中，新增 `System.Net.Http` 的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="6f4b3-122">新增程式碼</span><span class="sxs-lookup"><span data-stu-id="6f4b3-122">To add the code</span></span>  
  
1. <span data-ttu-id="6f4b3-123">在設計視窗 MainWindow.xaml 中，按兩下此按鈕以在 MainWindow.xaml.cs 中建立 `startButton_Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="6f4b3-124">將下列程式碼複製並貼到 MainWindow.xaml.cs 中的 `startButton_Click` 主體。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="6f4b3-125">此程式碼會呼叫非同步方法 `CreateMultipleTasksAsync` 來驅動應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="6f4b3-126">將下列支援方法新增至專案：</span><span class="sxs-lookup"><span data-stu-id="6f4b3-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="6f4b3-127">`ProcessURLAsync` 使用 <xref:System.Net.Http.HttpClient> 方法，將網站內容下載為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="6f4b3-128">然後，支援方法 `ProcessURLAsync` 會顯示並傳回陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="6f4b3-129">`DisplayResults` 會顯示每個 URL 的位元組陣列中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="6f4b3-130">當每個工作完成下載時，即會顯示此畫面。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="6f4b3-131">將下列方法複製並貼到 MainWindow.xaml.cs 中的 `startButton_Click` 事件處理常式之後。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
  
4. <span data-ttu-id="6f4b3-132">最後，定義 `CreateMultipleTasksAsync` 方法以執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="6f4b3-133">方法宣告 `HttpClient` 物件，需要存取 `ProcessURLAsync` 中的方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="6f4b3-134">方法會建立並啟動三個 <xref:System.Threading.Tasks.Task%601> 類型的工作，其中 `TResult` 是整數。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="6f4b3-135">當每個工作完成時，`DisplayResults` 會顯示工作的 URL 和下載內容的長度。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="6f4b3-136">因為工作是以非同步方式執行，所以結果出現的順序可能會因宣告的順序而有所不同。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="6f4b3-137">此方法會等候每個工作完成。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="6f4b3-138">每個 `await` 運算子會暫停執行 `CreateMultipleTasksAsync`，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="6f4b3-139">此運算子也會從每個完成的工作擷取透過呼叫 `ProcessURLAsync` 傳回的值。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="6f4b3-140">完成工作並擷取整數值之後，此方法會加總網站的長度並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="6f4b3-141">將下列方法複製並貼到您的方案中。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5. <span data-ttu-id="6f4b3-142">選擇 F5 鍵以執行程式，然後選擇 [開始]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="6f4b3-143">執行程式數次，以確認三個工作不一定會以相同的順序完成，而且它們的完成順序不一定是建立和等候的順序。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-143">Run the program several times to verify that the three tasks don't always finish in the same order and that the order in which they finish isn't necessarily the order in which they're created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f4b3-144">範例</span><span class="sxs-lookup"><span data-stu-id="6f4b3-144">Example</span></span>  
 <span data-ttu-id="6f4b3-145">下列程式碼包含完整的範例。</span><span class="sxs-lookup"><span data-stu-id="6f4b3-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f4b3-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f4b3-146">See also</span></span>

- [<span data-ttu-id="6f4b3-147">逐步解說：使用 async 和 await 存取 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="6f4b3-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="6f4b3-148">使用 Async 和 Await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="6f4b3-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="6f4b3-149">如何使用 System.threading.tasks.task.whenall 擴充非同步逐步解說（c #）</span><span class="sxs-lookup"><span data-stu-id="6f4b3-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
