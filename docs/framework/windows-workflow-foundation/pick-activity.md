---
title: Pick 活動
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b9ee6c06377760d27bc54d39c1d1f3ecf67ea0d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909414"
---
# <a name="pick-activity"></a>Pick 活動
<xref:System.Activities.Statements.Pick> 活動會簡化一組後續有對應處理常式之事件觸發程序的模型。  <xref:System.Activities.Statements.Pick> 活動包含<xref:System.Activities.Statements.PickBranch> 活動的集合，其中每個 <xref:System.Activities.Statements.PickBranch> 是 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 活動和 <xref:System.Activities.Statements.PickBranch.Action%2A> 活動間的配對。  在執行時間，會平行執行所有分支的觸發程序。  當一個觸發程序完成時，就會執行對應的動作，然後取消所有其他的觸發程序。  [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<xref:System.Activities.Statements.Pick> 活動的行為與 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]<xref:System.Workflow.Activities.ListenActivity> 活動相似。  
  
 以下螢幕擷取畫面是出自[使用 Pick 活動](./samples/using-the-pick-activity.md) SDK 範例，示範兩個分支的 Pick 活動。  分支有稱為 [讀取輸入] 的觸發程序，而這是從命令列讀取輸入的自訂活動。 第二個分支有 <xref:System.Activities.Statements.Delay> 活動觸發程序。 如果**讀取輸入**活動接收資料，然後才<xref:System.Activities.Statements.Delay>活動完成<xref:System.Activities.Statements.Delay>取消延遲，並且將祝賀詞寫入主控台。  否則，如果在分配的時間內 [讀取輸入] 活動沒有收到資料，就會取消它，並且將逾時訊息寫入主控台。  這是用來將逾時加入至任何動作的常見形式。  
  
 ![Pick 活動](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>最佳作法  
 使用 Pick 時，執行的分支是先完成其觸發程序的分支。  概念上，所有觸發程序會平行執行，且在一個觸發程序完成而取消另一個觸發程序之前，會先執行其主要邏輯。  請記住，使用 Pick 活動時要遵循的一般指導原則，就是將觸發程序視為單一事件的表示，並盡量少放入邏輯。  理想上，觸發程序應包含剛好足以擷取事件的邏輯，且該事件的所有處理，都應在分支中採取行動。  這個方法會最小化觸發程序間的重疊執行量。  例如，試想具有兩個觸發程序的 <xref:System.Activities.Statements.Pick>，其中每個觸發程序都包含後續有其他邏輯的 <xref:System.ServiceModel.Activities.Receive> 活動。  如果其他邏輯引起閒置點，則很可能兩個 <xref:System.ServiceModel.Activities.Receive> 活動都成功完成。  一個觸發程序會全部完成，而另一個觸發程序會部分完成。  在部分案例中，接受訊息然後完成部分的處理是不被接受的。  因此，當使用例如 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 的內建 WF 訊息活動時 (<xref:System.ServiceModel.Activities.Receive> 常用於觸發程序)，就應盡量讓 <xref:System.ServiceModel.Activities.SendReply> 和其他邏輯採取行動。  
  
## <a name="using-the-pick-activity-in-the-designer"></a>使用設計工具中的 Pick 活動  
 若要在設計工具中使用 Pick，請尋找工具列中的 [Pick] 和 [PickBranch]。  將 [Pick] 拖放到畫布上。  根據預設，設計工具中的新 [Pick] 活動會包含兩個分支。  若要加入其他分支，請拖曳 [PickBranch] 活動並置於現有分支旁。 活動可拖曳至 [Pick] 活動上任何 [PickBranch] 的 [Trigger] 區域或 [Action] 區域中。  
  
## <a name="using-the-pick-activity-in-code"></a>在程式碼中使用 Pick 活動  
 <xref:System.Activities.Statements.Pick> 活動的使用方式是將 <xref:System.Activities.Statements.Pick.Branches%2A> 活動填入其 <xref:System.Activities.Statements.PickBranch> 集合。 每個 <xref:System.Activities.Statements.PickBranch> 活動都有型別 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 的 <xref:System.Activities.Activity> 屬性。 當指定活動完成執行時，就會執行<xref:System.Activities.Statements.PickBranch.Action%2A>。  
  
 在下列程式碼範例中，示範了如何使用 <xref:System.Activities.Statements.Pick> 活動來實作從主控台讀取行之活動的逾時。  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =   
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =   
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine   
                   {   
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +   
                           name.Get(ctx))   
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```
