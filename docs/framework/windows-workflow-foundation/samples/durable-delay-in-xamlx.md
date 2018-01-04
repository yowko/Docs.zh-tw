---
title: "XAMLX 中的永久性延遲"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efc38df4-2d34-453c-8e59-2c21d1307354
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff5eb09acea16ac125fac5d9e3ed875c9095e1c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="durable-delay-in-xamlx"></a>XAMLX 中的永久性延遲
這個範例示範如何使用永久性延遲，此延遲會在延遲期間將工作流程保存至永久性裝置。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlx`  
  
## <a name="discussion"></a>討論  
 此範例工作流程包含兩個本機檔案訊息，兩者之間會以延遲區隔。 當延遲觸發時，工作流程便會卸載，並且在工作流程執行個體存放區中等待 5 秒鐘，再重新載入記憶體中。  
  
 .xamlx 檔案是裝載於 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 的工作流程服務。 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 會使用 Cassini，Cassini 則會使用工作流程服務主機來裝載工作流程。  
  
 除了裝載工作流程以外，工作流程服務主機也會透過載入和卸載的方式來管理工作流程執行個體。 為了啟動 [!INCLUDE[wf](../../../../includes/wf-md.md)] 定義的執行個體 (在工作流程服務主機上)，請設定用戶端傳送訊息給工作流程中的 <xref:System.ServiceModel.Activities.Receive> 活動。 這個 <xref:System.ServiceModel.Activities.Receive> 會將它的 <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> 屬性設定為 `true`，以便在收到訊息時，建立新的工作流程執行個體。  
  
 在初始化期間，卸載執行個體的行為會加入至組態檔中，這個組態檔會指定工作流程服務主機應將執行個體卸載至持續性存放區 (資料庫) 的情況。 在這個範例中，它會在工作流程閒置後 (觸發延遲時) 立即卸載執行個體。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
2.  巡覽至 DurableDelayXamlx\CS 資料夾。  
  
3.  執行 Setup.cmd。  
  
4.  以系統管理員身分執行 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]。  
  
5.  開啟 DurableDelayXamlx.sln 方案檔。  
  
6.  在**方案總管 中**，以滑鼠右鍵按一下方案，然後選取**屬性**。  
  
7.  選取**多個啟始專案**和設定兩個專案**啟動**。  
  
8.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
9. 若要執行此方案，請按下 CTRL+F5。  
  
#### <a name="to-uninstall-this-sample"></a>若要解除安裝這個範例  
  
1.  開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。  
  
2.  巡覽至 DurableDelayXamlx\CS 資料夾。  
  
3.  執行 Cleanup.cmd。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDelayXamlX`
