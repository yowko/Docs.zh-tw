---
title: "非同步通訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 非同步通訊
這個範例示範如何在兩種不同的 [!INCLUDE[wf](../../../../includes/wf-md.md)] 服務之間依預設以非同步方式進行通訊。  
  
## 示範  
 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 服務之間的非同步通訊。  
  
## 討論  
 這個範例示範如何在 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 應用程式之間使用 .NET Framework 提供的訊息處理活動，以非同步方式進行通訊。  
  
 這個範例包含下列三個專案。  
  
 CreditCheckService  
 這項服務會接受特定人員的信用得分，或是要擷取的項目值，然後決定是否給予該人員信用額度。  
  
 RentalApprovalService  
 這項服務會接收需要一些信用額度的人提出的申請。這項服務會以非同步方式與 `CreditCheckService` 進行通訊，決定信用額度申請是否有效。  
  
 Client  
 Client 會以同步方式與 `RentalApprovalService` 進行通訊，了解信用額度是否核准。  
  
#### 若要安裝、建立及執行範例  
  
1.  以滑鼠右鍵按一下 \[**AsynchronousCommunication**\] 方案，然後選取 \[**屬性**\]。  
  
2.  選取 \[**通用屬性**\] 中的 \[**啟始專案**\]，然後選取 \[**多個啟始專案**\]。  
  
3.  將 \[**RentalApprovalService**\] 移至清單中的第一個位置，後面依序為 \[**CreditCheckService**\] 和 \[**Client**\]。在三個專案上設定 \[**開始**\] 動作。  
  
4.  按一下 \[**確定**\]，然後按 F5 執行範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`