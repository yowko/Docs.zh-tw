---
title: NativeActivity 基底類別
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: ca4a497f1e78989f9488507015526214ead6cae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nativeactivity-base-class"></a>NativeActivity 基底類別
<xref:System.Activities.NativeActivity> 是具有受保護建構函式的抽象類別。 如同 <xref:System.Activities.CodeActivity>，<xref:System.Activities.NativeActivity> 會用於透過實作 <xref:System.Activities.NativeActivity.Execute%2A> 方法的方式寫入命令式行為。 不同於 <xref:System.Activities.CodeActivity> 的是，<xref:System.Activities.NativeActivity> 可透過傳遞至 <xref:System.Activities.NativeActivityContext> 方法的 <xref:System.Activities.NativeActivity.Execute%2A> 物件，存取工作流程執行階段的所有公開功能。  
  
## <a name="using-nativeactivitycontext"></a>使用 NativeActivityContext  
 工作流程執行階段的功能可透過 <xref:System.Activities.NativeActivity.Execute%2A> 方法內部存取，方法是使用 `context` 參數的成員 (型別為 <xref:System.Activities.NativeActivityContext>)。 透過 <xref:System.Activities.NativeActivityContext> 可使用的功能如下：  
  
-   取得與設定引數和變數。  
  
-   使用 <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A> 排程子活動。  
  
-   使用 <xref:System.Activities.NativeActivityContext.Abort%2A> 中止活動執行。  
  
-   使用 <xref:System.Activities.NativeActivityContext.CancelChild%2A> 和 <xref:System.Activities.NativeActivityContext.CancelChildren%2A> 取消子執行。  
  
-   使用 <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>、<xref:System.Activities.NativeActivityContext.RemoveBookmark%2A> 和 <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> 之類的方法存取活動書籤。  
  
-   使用 <xref:System.Activities.CodeActivityContext.Track%2A> 自訂追蹤功能。  
  
-   使用 <xref:System.Activities.CodeActivityContext.GetProperty%2A> 和 <xref:System.Activities.NativeActivityContext.GetValue%2A> 存取活動的執行屬性和值屬性。  
  
-   使用 <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> 和 <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A> 排訂活動動作與功能。  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a>若要建立繼承自 NativeActivity 的自訂活動  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  選取**檔案**，**新**，然後**專案**。 選取**Workflow 4.0**下**Visual C#** 中**專案類型**視窗，並選取**v2010**節點。 選取**活動程式庫**中**範本**視窗。 將新專案命名為 HelloActivity。  
  
3.  以滑鼠右鍵按一下 HelloActivity 專案中的 Activity1.xaml，然後選取**刪除**。  
  
4.  以滑鼠右鍵按一下 HelloActivity 專案並選取**新增**，然後**類別**。 將新類別命名為 HelloActivity.cs。  
  
5.  在 HelloActivity.cs 檔案中加入下列 `using` 指示詞。  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  將基底類別加入至類別宣告，使新的類別繼承自 <xref:System.Activities.NativeActivity>。  
  
    ```csharp  
    class HelloActivity : NativeActivity  
    ```  
  
7.  加入 <xref:System.Activities.NativeActivity.Execute%2A> 方法，藉此將功能加入至類別中。  
  
    ```csharp  
    protected override void Execute(NativeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  覆寫 <xref:System.Activities.NativeActivity.CacheMetadata%2A> 方法，並呼叫適當的 Add 方法，讓工作流程執行階段知道自訂活動的變數、引數、子系和委派。 如需詳細資訊，請參閱 <xref:System.Activities.NativeActivityMetadata> 類別。  
  
9. 使用 <xref:System.Activities.NativeActivityContext> 物件排程書籤。 如需如何建立、排程和繼續書籤的詳細資訊，請參閱 <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>。  
  
    ```  
    protected override void Execute(NativeActivityContext context)  
        {  
            // Create a Bookmark and wait for it to be resumed.  
            context.CreateBookmark(BookmarkName.Get(context),   
                new BookmarkCallback(OnResumeBookmark));  
        }  
    ```
