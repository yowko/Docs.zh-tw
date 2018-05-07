---
title: 已啟用 ReceiveContext 的 WCF 通道
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: 3e5ac914ae4d0c97ed617ea4a8d5a893ec740179
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="receivecontext-enabled-wcf-channels"></a>已啟用 ReceiveContext 的 WCF 通道
這個範例示範具備 <xref:System.ServiceModel.Channels.ReceiveContext> 能力之 WCF 通道的用處。 這個範例會實作服務，以使用 NetMSMQ 通道尋找兩個數字的乘積。  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> 類別可讓應用程式決定要存取訊息，或是將訊息留在佇列中做進一步處理 (即使是在已檢查過訊息的內容之後)。 在這個範例中，用戶端會將隨機整數傳送至交易式佇列。 `ProductCalculator` 服務會接收訊息並檢查訊息內容 (也就是整數)，以判斷是否可以計算乘積。 如果服務作業未計算乘積，則訊息會放回佇列中，並且可以由接聽佇列的服務再次接收。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  請確定已安裝 Microsoft Message Queuing (MSMQ)。  
  
    1.  若要在 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上安裝 MSMQ：  
  
        1.  在**伺服器管理員**，按一下 **功能**。  
  
        2.  在底下的右窗格中**功能摘要**，按一下 **新增功能**。  
  
        3.  在結果視窗中，依序展開**訊息佇列**。  
  
        4.  展開**訊息佇列服務**。  
  
        5.  按一下**目錄服務整合**（針對加入網域電腦），然後按一下  **HTTP 支援**。  
  
        6.  按一下**下一步**，然後按一下 **安裝**。  
  
    2.  若要在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上安裝 MSMQ：  
  
        1.  開啟**控制台**。  
  
        2.  按一下**程式**然後在**程式和功能**，按一下 **開啟或關閉 Windows 功能**。  
  
        3.  展開**Microsoft Message Queue (MSMQ) 伺服器**，依序展開**Microsoft Message Queue (MSMQ) 伺服器核心**，然後選取要安裝的下列訊息佇列功能的核取方塊：  
  
            -   訊息佇列伺服器  
  
            -   MSMQ Active Directory 網域服務整合 (針對加入網域的電腦)  
  
            -   MSMQ HTTP 支援  
  
        4.  按一下 [確定 **Deploying Office Solutions**]。  
  
        5.  如果提示您重新啟動電腦時，請按一下**確定**以完成安裝。  
  
2.  請確定電腦上已安裝 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
3.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 ReceiveContextProductGenerator.sln 方案檔案。  
  
4.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
5.  若要執行此方案，請按下 CTRL+F5。
