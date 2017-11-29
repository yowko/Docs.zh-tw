---
title: "以內容為基礎的相互關聯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0490dcc854a6686c69ebc480df42e6086d1fdc52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="content-based-correlation"></a>以內容為基礎的相互關聯
這個範例示範訊息活動 (<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>) 與多個內容架構相互關聯搭配使用的方式。 在這個案例中，根據採購單識別碼先初始化一個相互關聯，接著根據客戶識別碼建立另一個相互關聯。 這示範 <xref:System.ServiceModel.Activities.Receive> 活動如何追蹤現有的相互關聯，以及根據相同的傳入訊息來初始化新的相互關聯。  
  
## <a name="demonstrates"></a>示範  
 訊息活動和內容架構相互關聯  
  
## <a name="discussion"></a>討論  
 這個範例示範如何使用多個內容架構相互關聯。  在這個案例中，根據採購單識別碼先初始化一個相互關聯，接著根據客戶識別碼建立另一個相互關聯。  相互關聯是以 <xref:System.ServiceModel.Activities.Receive> 活動串聯，這個活動會追蹤現有的相互關聯 (PurchaseOrderId)，以及根據相同的傳入訊息來初始化新的相互關聯 (CustomerId)。  <xref:System.ServiceModel.Activities.Receive> 活動使用 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>、<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> 和 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 屬性來完成這項作業。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以提高的權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]圖示，然後選取**系統管理員身分執行**。  
  
2.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CascadingCorrelation.sln 方案檔案。  
  
3.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
4.  若要執行伺服器，請按 F5。  
  
5.  一旦服務準備好接聽訊息，請在 [方案總管] 中，以滑鼠右鍵按一下用戶端專案，並執行此專案。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`  
  
## <a name="see-also"></a>另請參閱
