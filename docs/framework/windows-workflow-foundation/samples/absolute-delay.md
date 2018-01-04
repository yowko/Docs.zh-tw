---
title: "絕對延遲"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6974c7bb281aa6685725b65edd06bb40a907559
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="absolute-delay"></a>絕對延遲
這個範例的主要案例是在工作流程應用程式中使用永久性計時器，以便延遲到指定的 <xref:System.DateTime> 為止。 這項作業與使用內建的 <xref:System.Activities.Statements.Delay> 活動不同，因為這樣做只會允許您延遲給定的 <xref:System.TimeSpan> (或分鐘/秒數)。  
  
 您可能會想要區別的一些實際案例包括：  
  
1.  您想要延遲傳送郵件 30 秒，確保沒有發生任何錯誤。  
  
2.  您在加班時間內工作，而且想要將所有郵件都延遲到正常上班時間 (例如上午 8 點) 才傳送。  
  
## <a name="demonstrates"></a>示範  
  
1.  用於實作絕對延遲的 <xref:System.Activities.Statements.DurableTimerExtension>  
  
2.  使用永久性計時器的 <xref:System.Activities.WorkflowApplication> 設定持續性  
  
3.  透過 <xref:System.Activities.NativeActivity%601> 使用擴充點  
  
4.  在 SendEmail 活動中使用 <xref:System.Activities.CodeActivity%601>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  僅限 XAML 的工作流程  
  
 這個範例示範如何建立自訂活動，此活動會接受 <xref:System.DateTime> 並且使用永久性計時器來註冊延遲持續時間。 使用永久性計時器時，您必須使用 <xref:System.Activities.NativeActivity> 來建立書籤，因為您必須利用計時器擴充註冊此書籤。 在此範例中，當永久性計時器過期時，系統就會呼叫 `OnTimerExpired` 方法。 請務必在 <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> 事件中加入計時器擴充，確保您會將這項資訊提供給執行階段。 其他實作詳細資料就是，您必須實作邏輯，以便從 <xref:System.DateTime> 轉換成 <xref:System.TimeSpan>，因為永久性計時器只接受 <xref:System.DateTime>。 請注意，這樣做會造成些微的精確度誤差。  
  
> [!NOTE]
>  從 <xref:System.DateTime> 轉換成 <xref:System.TimeSpan> 時，會喪失些微的精確度。  
  
 這個範例也會示範如何開啟 <xref:System.Activities.WorkflowApplication> 的持續性。 在此特定範例中，我們將使用永久性計時器，以便在等候計時器過期的閒置時間內，將工作流程資料卸載至持續性資料庫中。 這項實作也可用於其他持續性動作。 此範例會示範如何使用 SQL Server 來設定持續性連接字串，以及如何建立執行個體存放區，以便保存工作流程執行個體的資料。 所提供的邏輯是有關如何在引發事件之後繼續工作流程，讓工作流程執行個體可執行。  
  
 當您逐步執行這個範例時，您會看到內建延遲開始和完成的時間，接著導致系統傳送電子郵件訊息。 之後，AbsoluteDelay 活動將中止直到指定的 <xref:System.DateTime> (或 0 秒，如果 <xref:System.DateTime> 已過期的話) 為止，接著便在過期時送出電子郵件。 這將顯示內建 <xref:System.Activities.Statements.Delay> 功能與使用 AbsoluteDelay 活動的兩種不同使用案例。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已在電腦上安裝 SQL Server Express (或更新版本)。  
  
2.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元中，執行 setup.cmd (位於 WF/Basic/Services/AbsoluteDelay/CS 中)，以便建立 AbsoluteDelaySampleDB 資料庫、建立持續性結構描述以及建立持續性邏輯。  
  
3.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟方案。  
  
4.  在 Delay 活動中指定 Duration。  
  
5.  在 AbsoluteDelay 活動中指定 ExpirationTime。  
  
6.  更新 SendMail 活動中的 SendMailTo、SendMailFrom、SendMailSubject、SendMailBody 和 SmtpHost 欄位。  
  
    > [!NOTE]
    >  如果您沒有輸入有效的 SMTP 主機，應用程式將會擲回 SMTP 例外狀況。  
  
7.  選取 建置方案**建置**，**建置方案**。  
  
8.  執行方案，請按**F5**。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
