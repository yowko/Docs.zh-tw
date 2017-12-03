---
title: Bookmarks1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b51a346-09ae-455c-a70a-e2264ddeb9e2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ebd6586500c82144f7bceca01dea278a76759b1f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="bookmarks"></a>書籤
書籤是一種可讓活動被動等候輸入而不需保存工作流程執行緒的機制。 活動發出等候刺激的訊號時，就可以建立書籤。 此動作可讓執行階段知道，即使目前執行中的方法 (此方法建立了 <xref:System.Activities.Bookmark>) 傳回，也不應將活動的執行視為已完成。  
  
## <a name="bookmark-basics"></a>書籤基本資訊  
 <xref:System.Activities.Bookmark> 代表工作流程執行個體中可繼續執行的點 (且可透過此點傳遞輸入)。 一般而言，<xref:System.Activities.Bookmark> 有名稱，而外部 (主機或擴充) 程式碼則會負責繼續執行具有相關資料的書籤。 繼續執行 <xref:System.Activities.Bookmark> 時，工作流程執行階段會排定 <xref:System.Activities.BookmarkCallback> 委派，此委派建立時與該 <xref:System.Activities.Bookmark> 相關。  
  
## <a name="bookmark-options"></a>書籤選項  
 <xref:System.Activities.BookmarkOptions> 類別會指定要建立之 <xref:System.Activities.Bookmark> 的型別。 可能的非互斥值包括 <xref:System.Activities.BookmarkOptions.None>、<xref:System.Activities.BookmarkOptions.MultipleResume> 和 <xref:System.Activities.BookmarkOptions.NonBlocking>。 建立預期只應繼續執行一次的 <xref:System.Activities.BookmarkOptions.None> 時，請使用預設值 <xref:System.Activities.Bookmark>。 建立可以繼續多次的 <xref:System.Activities.BookmarkOptions.MultipleResume> 時，則使用 <xref:System.Activities.Bookmark>。 建立可能不會再繼續的 <xref:System.Activities.BookmarkOptions.NonBlocking> 時，請使用 <xref:System.Activities.Bookmark>。 不同於使用預設 <xref:System.Activities.BookmarkOptions> 建立的書籤，<xref:System.Activities.BookmarkOptions.NonBlocking> 書籤不會防止活動完成。  
  
## <a name="bookmark-resumption"></a>書籤繼續  
 工作流程以外的程式碼可以使用其中一個 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 多載來繼續書籤。 在這個範例中，會建立 `ReadLine` 活動。 執行時，`ReadLine` 活動就會建立 <xref:System.Activities.Bookmark>、註冊回呼，然後等候繼續 <xref:System.Activities.Bookmark>。 當它繼續時，`ReadLine` 活動會將以 <xref:System.Activities.Bookmark> 傳遞的資料指派至其 <xref:System.Activities.Activity%601.Result%2A> 引數。  
  
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
  
 在此範例中，使用 `ReadLine` 活動建立的工作流程可蒐集使用者的名稱，並於主控台視窗中顯示。 主應用程式會執行收集輸入的實際工作，並透過繼續 <xref:System.Activities.Bookmark>，將輸入傳遞至工作流程。  
  
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
  
 當執行 `ReadLine` 活動時，它會建立稱為 <xref:System.Activities.Bookmark> 的 `UserName`，然後等候書籤繼續。 主機會收集想要的資料，然後繼續 <xref:System.Activities.Bookmark>。 工作流程會繼續、顯示名稱，然後完成。 請注意，繼續書籤時不需同步處理程式碼。 <xref:System.Activities.Bookmark> 只能在工作流程閒置時繼續，若工作流程未閒置，就會封鎖對 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 的呼叫，直到工作流程閒置為止。  
  
## <a name="bookmark-resumption-result"></a>書籤繼續結果  
 <xref:System.Activities.WorkflowApplication.ResumeBookmark%2A> 會傳回 <xref:System.Activities.BookmarkResumptionResult> 列舉值，指出書籤繼續要求的結果。 可能的傳回值包括 <xref:System.Activities.BookmarkResumptionResult.Success>、<xref:System.Activities.BookmarkResumptionResult.NotReady> 和 <xref:System.Activities.BookmarkResumptionResult.NotFound>。 主機與擴充可以利用這個值來判斷如何繼續進行。
