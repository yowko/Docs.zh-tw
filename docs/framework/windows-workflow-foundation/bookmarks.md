---
title: Bookmarks1
ms.date: 03/30/2017
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
ms.openlocfilehash: 8b7ca9549327087e30d6c72a8b784aa37ad09f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515564"
---
# <a name="bookmarks"></a><span data-ttu-id="665ca-102">書籤</span><span class="sxs-lookup"><span data-stu-id="665ca-102">Bookmarks</span></span>
<span data-ttu-id="665ca-103">書籤是一種可讓活動被動等候輸入而不需保存工作流程執行緒的機制。</span><span class="sxs-lookup"><span data-stu-id="665ca-103">Bookmarks are the mechanism that enables an activity to passively wait for input without holding onto a workflow thread.</span></span> <span data-ttu-id="665ca-104">活動發出等候刺激的訊號時，就可以建立書籤。</span><span class="sxs-lookup"><span data-stu-id="665ca-104">When an activity signals that it is waiting for stimulus, it can create a bookmark.</span></span> <span data-ttu-id="665ca-105">此動作可讓執行階段知道，即使目前執行中的方法 (此方法建立了 <xref:System.Activities.Bookmark>) 傳回，也不應將活動的執行視為已完成。</span><span class="sxs-lookup"><span data-stu-id="665ca-105">This indicates to the runtime that the activity’s execution should not be considered complete even when the currently executing method (which created the <xref:System.Activities.Bookmark>) returns.</span></span>  
  
## <a name="bookmark-basics"></a><span data-ttu-id="665ca-106">書籤基本資訊</span><span class="sxs-lookup"><span data-stu-id="665ca-106">Bookmark Basics</span></span>  
 <span data-ttu-id="665ca-107"><xref:System.Activities.Bookmark> 代表工作流程執行個體中可繼續執行的點 (且可透過此點傳遞輸入)。</span><span class="sxs-lookup"><span data-stu-id="665ca-107">A <xref:System.Activities.Bookmark> represents a point at which execution can be resumed (and through which input can be delivered) within a workflow instance.</span></span> <span data-ttu-id="665ca-108">一般而言，<xref:System.Activities.Bookmark> 有名稱，而外部 (主機或擴充) 程式碼則會負責繼續執行具有相關資料的書籤。</span><span class="sxs-lookup"><span data-stu-id="665ca-108">Typically, a <xref:System.Activities.Bookmark> is given a name and external (host or extension) code is responsible for resuming the bookmark with relevant data.</span></span> <span data-ttu-id="665ca-109">繼續執行 <xref:System.Activities.Bookmark> 時，工作流程執行階段會排定 <xref:System.Activities.BookmarkCallback> 委派，此委派建立時與該 <xref:System.Activities.Bookmark> 相關。</span><span class="sxs-lookup"><span data-stu-id="665ca-109">When a <xref:System.Activities.Bookmark> is resumed, the workflow runtime schedules the <xref:System.Activities.BookmarkCallback> delegate that was associated with that <xref:System.Activities.Bookmark> at the time of its creation.</span></span>  
  
## <a name="bookmark-options"></a><span data-ttu-id="665ca-110">書籤選項</span><span class="sxs-lookup"><span data-stu-id="665ca-110">Bookmark Options</span></span>  
 <span data-ttu-id="665ca-111"><xref:System.Activities.BookmarkOptions> 類別會指定要建立之 <xref:System.Activities.Bookmark> 的型別。</span><span class="sxs-lookup"><span data-stu-id="665ca-111">The <xref:System.Activities.BookmarkOptions> class specifies the type of <xref:System.Activities.Bookmark> being created.</span></span> <span data-ttu-id="665ca-112">可能的非互斥值包括 <xref:System.Activities.BookmarkOptions.None>、<xref:System.Activities.BookmarkOptions.MultipleResume> 和 <xref:System.Activities.BookmarkOptions.NonBlocking>。</span><span class="sxs-lookup"><span data-stu-id="665ca-112">The possible non mutually-exclusive values are <xref:System.Activities.BookmarkOptions.None>, <xref:System.Activities.BookmarkOptions.MultipleResume>, and <xref:System.Activities.BookmarkOptions.NonBlocking>.</span></span> <span data-ttu-id="665ca-113">建立預期只應繼續執行一次的 <xref:System.Activities.BookmarkOptions.None> 時，請使用預設值 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="665ca-113">Use <xref:System.Activities.BookmarkOptions.None>, the default, when creating a <xref:System.Activities.Bookmark> that is expected to be resumed exactly once.</span></span> <span data-ttu-id="665ca-114">建立可以繼續多次的 <xref:System.Activities.BookmarkOptions.MultipleResume> 時，則使用 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="665ca-114">Use <xref:System.Activities.BookmarkOptions.MultipleResume> when creating a <xref:System.Activities.Bookmark> that can be resumed multiple times.</span></span> <span data-ttu-id="665ca-115">建立可能不會再繼續的 <xref:System.Activities.BookmarkOptions.NonBlocking> 時，請使用 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="665ca-115">Use <xref:System.Activities.BookmarkOptions.NonBlocking> when creating a <xref:System.Activities.Bookmark> that might never be resumed.</span></span> <span data-ttu-id="665ca-116">不同於使用預設 <xref:System.Activities.BookmarkOptions> 建立的書籤，<xref:System.Activities.BookmarkOptions.NonBlocking> 書籤不會防止活動完成。</span><span class="sxs-lookup"><span data-stu-id="665ca-116">Unlike bookmarks created using the default <xref:System.Activities.BookmarkOptions>, <xref:System.Activities.BookmarkOptions.NonBlocking> bookmarks do not prevent an activity from completing.</span></span>  
  
## <a name="bookmark-resumption"></a><span data-ttu-id="665ca-117">書籤繼續</span><span class="sxs-lookup"><span data-stu-id="665ca-117">Bookmark Resumption</span></span>  
 <span data-ttu-id="665ca-118">工作流程以外的程式碼可以使用其中一個 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 多載來繼續書籤。</span><span class="sxs-lookup"><span data-stu-id="665ca-118">Bookmarks can be resumed by code outside of a workflow using one of the <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> overloads.</span></span> <span data-ttu-id="665ca-119">在這個範例中，會建立 `ReadLine` 活動。</span><span class="sxs-lookup"><span data-stu-id="665ca-119">In this example, a `ReadLine` activity is created.</span></span> <span data-ttu-id="665ca-120">執行時，`ReadLine` 活動就會建立 <xref:System.Activities.Bookmark>、註冊回呼，然後等候繼續 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="665ca-120">When executed, the `ReadLine` activity creates a <xref:System.Activities.Bookmark>, registers a callback, and then waits for the <xref:System.Activities.Bookmark> to be resumed.</span></span> <span data-ttu-id="665ca-121">當它繼續時，`ReadLine` 活動會將以 <xref:System.Activities.Bookmark> 傳遞的資料指派至其 <xref:System.Activities.Activity%601.Result%2A> 引數。</span><span class="sxs-lookup"><span data-stu-id="665ca-121">When it is resumed, the `ReadLine` activity assigns the data that was passed with the <xref:System.Activities.Bookmark> to its <xref:System.Activities.Activity%601.Result%2A> argument.</span></span>  
  
```csharp  
public sealed class ReadLine : NativeActivity<string>  
{  
    [RequiredArgument]  
    public  InArgument<string> BookmarkName { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        // Create a Bookmark and wait for it to be resumed.  
        context.CreateBookmark(BookmarkName.Get(context),   
            new BookmarkCallback(OnResumeBookmark));  
    }  
  
    // NativeActivity derived activities that do asynchronous operations by calling   
    // one of the CreateBookmark overloads defined on System.Activities.NativeActivityContext   
    // must override the CanInduceIdle property and return true.  
    protected override bool CanInduceIdle  
    {  
        get { return true; }  
    }  
  
    public void OnResumeBookmark(NativeActivityContext context, Bookmark bookmark, object obj)  
    {  
        // When the Bookmark is resumed, assign its value to  
        // the Result argument.  
        Result.Set(context, (string)obj);  
    }  
}  
```  
  
 <span data-ttu-id="665ca-122">在此範例中，使用 `ReadLine` 活動建立的工作流程可蒐集使用者的名稱，並於主控台視窗中顯示。</span><span class="sxs-lookup"><span data-stu-id="665ca-122">In this example, a workflow is created that uses the `ReadLine` activity to gather the user’s name and display it to the console window.</span></span> <span data-ttu-id="665ca-123">主應用程式會執行收集輸入的實際工作，並透過繼續 <xref:System.Activities.Bookmark>，將輸入傳遞至工作流程。</span><span class="sxs-lookup"><span data-stu-id="665ca-123">The host application performs the actual work of gathering the input and passes it to the workflow by resuming the <xref:System.Activities.Bookmark>.</span></span>  
  
```csharp  
Variable<string> name = new Variable<string>  
{  
    Name = "name"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        name  
    },  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "What is your name?"  
        },  
        new ReadLine()  
        {  
            BookmarkName = "UserName",  
            Result = name  
        },  
        new WriteLine()  
        {  
            Text = new InArgument<string>((env) => "Hello, " + name.Get(env))  
        }  
    }  
};  
  
AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
// Create the WorkflowApplication using the desired  
// workflow definition.  
WorkflowApplication wfApp = new WorkflowApplication(wf);  
  
// Handle the desired lifecycle events.  
wfApp.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
{  
    // Signal the host that the workflow is complete.  
    syncEvent.Set();  
};  
  
// Start the workflow.  
wfApp.Run();  
  
// Collect the user's name and resume the bookmark.  
// Bookmark resumption only occurs when the workflow  
// is idle. If a call to ResumeBookmark is made and the workflow  
// is not idle, ResumeBookmark blocks until the workflow becomes  
// idle before resuming the bookmark.  
wfApp.ResumeBookmark("UserName", Console.ReadLine());  
  
// Wait for Completed to arrive and signal that  
// the workflow is complete.  
syncEvent.WaitOne();  
```  
  
 <span data-ttu-id="665ca-124">當執行 `ReadLine` 活動時，它會建立稱為 <xref:System.Activities.Bookmark> 的 `UserName`，然後等候書籤繼續。</span><span class="sxs-lookup"><span data-stu-id="665ca-124">When the `ReadLine` activity is executed, it creates a <xref:System.Activities.Bookmark> named `UserName` and then waits for the bookmark to be resumed.</span></span> <span data-ttu-id="665ca-125">主機會收集想要的資料，然後繼續 <xref:System.Activities.Bookmark>。</span><span class="sxs-lookup"><span data-stu-id="665ca-125">The host collects the desired data and then resumes the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="665ca-126">工作流程會繼續、顯示名稱，然後完成。</span><span class="sxs-lookup"><span data-stu-id="665ca-126">The workflow resumes, displays the name, and then completes.</span></span> <span data-ttu-id="665ca-127">請注意，繼續書籤時不需同步處理程式碼。</span><span class="sxs-lookup"><span data-stu-id="665ca-127">Note that no synchronization code is required with regard to resuming the bookmark.</span></span> <span data-ttu-id="665ca-128"><xref:System.Activities.Bookmark> 只能在工作流程閒置時繼續，若工作流程未閒置，就會封鎖對 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 的呼叫，直到工作流程閒置為止。</span><span class="sxs-lookup"><span data-stu-id="665ca-128">A <xref:System.Activities.Bookmark> can only be resumed when the workflow is idle, and if the workflow is not idle, the call to <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> blocks until the workflow becomes idle.</span></span>  
  
## <a name="bookmark-resumption-result"></a><span data-ttu-id="665ca-129">書籤繼續結果</span><span class="sxs-lookup"><span data-stu-id="665ca-129">Bookmark Resumption Result</span></span>  
 <span data-ttu-id="665ca-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 會傳回 <xref:System.Activities.BookmarkResumptionResult> 列舉值，指出書籤繼續要求的結果。</span><span class="sxs-lookup"><span data-stu-id="665ca-130"><xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> returns a <xref:System.Activities.BookmarkResumptionResult> enumeration value to indicate the results of the bookmark resumption request.</span></span> <span data-ttu-id="665ca-131">可能的傳回值包括 <xref:System.Activities.BookmarkResumptionResult.Success>、<xref:System.Activities.BookmarkResumptionResult.NotReady> 和 <xref:System.Activities.BookmarkResumptionResult.NotFound>。</span><span class="sxs-lookup"><span data-stu-id="665ca-131">The possible return values are <xref:System.Activities.BookmarkResumptionResult.Success>, <xref:System.Activities.BookmarkResumptionResult.NotReady>, and <xref:System.Activities.BookmarkResumptionResult.NotFound>.</span></span> <span data-ttu-id="665ca-132">主機與擴充可以利用這個值來判斷如何繼續進行。</span><span class="sxs-lookup"><span data-stu-id="665ca-132">Hosts and extensions can use this value to determine how to proceed.</span></span>
