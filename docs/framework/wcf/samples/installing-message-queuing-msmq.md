---
title: "安裝訊息佇列 (MSMQ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 安裝訊息佇列 (MSMQ)
下列程序示範如何安裝 Message Queuing 4.0 和 Message Queuing 3.0。  
  
> [!NOTE]
>  [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 未提供 Message Queuing 4.0。  
  
#### 若要在 Windows Server 2008 或 Windows Server 2008 R2 上安裝 Message Queuing 4.0  
  
1.  在 \[伺服器管理員\] 中，按一下 \[**功能**\]。  
  
2.  在 \[**功能摘要**\] 下的右窗格中，按一下 \[**新增功能**\]。  
  
3.  在顯示的視窗中，展開 \[**訊息佇列**\]。  
  
4.  展開 \[**訊息佇列服務**\]。  
  
5.  按一下 \[**目錄服務整合**\] \(針對加入網域的電腦\)，再按一下 \[**HTTP 支援**\]。  
  
6.  按一下 \[**下一步**\]，再按一下 \[**安裝**\]。  
  
#### 若要在 Windows 7 或 Windows Vista 上安裝 Message Queuing 4.0  
  
1.  開啟 \[**控制台**\]。  
  
2.  按一下 \[**程式集**\]，然後在 \[**程式和功能**\] 下按一下 \[**開啟或關閉 Windows 功能**\]。  
  
3.  展開 \[Microsoft Message Queue \(MSMQ\) 伺服器\]，展開 \[Microsoft Message Queue \(MSMQ\) 伺服器核心\]，然後選取下列訊息佇列功能的核取方塊進行安裝：  
  
    -   MSMQ Active Directory 網域服務整合 \(針對加入網域的電腦\)。  
  
    -   MSMQ HTTP 支援。  
  
4.  按一下 \[**確定**\]。  
  
5.  如果提示您重新啟動電腦，請按一下 \[**確定**\] 完成安裝。  
  
#### 若要在 Windows XP 和 Windows Server 2003 上安裝 Message Queuing 3.0  
  
1.  開啟 \[**控制台**\]。  
  
2.  按一下 \[**新增移除程式**\]，然後按一下 \[**新增 Windows 元件**\]。  
  
3.  選取 \[訊息佇列\]，然後按一下 \[**詳細資料**\]。  
  
    > [!NOTE]
    >  如果您執行的是 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]，請選取 \[應用程式伺服器\] 來存取訊息佇列。  
  
4.  確定在詳細資料頁面上選取 MSMQ HTTP 支援的選項。  
  
5.  按一下 \[**確定**\] 結束詳細資料頁面，然後按一下 \[**下一步**\]。完成安裝。  
  
6.  如果提示您重新啟動電腦，請按一下 \[ **確定**\] 完成安裝。  
  
## 請參閱  
 [安裝指示](../../../../docs/framework/wcf/samples/set-up-instructions.md)