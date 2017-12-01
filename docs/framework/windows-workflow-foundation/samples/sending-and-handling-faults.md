---
title: "傳送及處理錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 70693af8582de084894275c832e451d7f0fee794
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="sending-and-handling-faults"></a>傳送及處理錯誤
這個範例示範如何使用 <xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 訊息活動，傳送及接收預期和非預期的錯誤。 在這個案例中，第一個用戶端要求產生已包含在 <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> 集合中的預期錯誤。 後面幾個用戶端要求會在最終要求成功之前產生非預期的錯誤。  
  
## <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  開啟[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以提高的權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]圖示，然後選取**系統管理員身分執行**。  
  
2.  開啟 Faults.sln 方案檔案。  
  
3.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
4.  執行服務專案。  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下`FaultService`專案，然後選取**設定為啟始專案**。  
  
    2.  按下 CTRL+F5。  
  
5.  開啟另一份[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以提高的權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]圖示，然後選取**系統管理員身分執行**。  
  
6.  開啟 Faults.sln 方案檔案。  
  
7.  執行用戶端專案。  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下`FaultClient`專案，然後選取**設定為啟始專案**。  
  
    2.  按下 CTRL+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`