---
title: "可靠的安全設定檔 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# 可靠的安全設定檔
此範例示範如何撰寫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和[可靠的安全設定檔](http://go.microsoft.com/fwlink/?LinkId=178140) \(Reliable Secure Profile，RSP\) \(英文\)。此範例示範[建立連線](http://go.microsoft.com/fwlink/?LinkId=178141) \(英文\) 通道的實作，此通道可以和 Reliable Messaging 以及 \(選擇性地\) 安全通道一起撰寫，以便根據 RSP 規格建立可靠的安全繫結。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## 討論  
 此範例示範可靠的非同步雙向訊息交換案例。此服務擁有雙工合約，而且用戶端會實作雙工回呼合約。用戶端會向服務起始一個要求，這個要求預期在不同的連線上得到回應。要求訊息是以可靠的方式傳送。用戶端不想在其結尾開啟接聽端點。因此，它會利用服務的「建立連線」要求輪詢服務，以便在這個「建立連線」要求的返回通道傳回回應。此範例示範如何透過 HTTP 進行安全可靠的雙工通訊，而不讓用戶端公開接聽端點 \(以及建立防火牆例外狀況\)。  
  
## 若要安裝、建立及執行範例  
  
1.  開啟 **ReliableSecureProfile** 方案。  
  
2.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**服務**\] 專案，然後選取內容功能表中的 \[**偵錯**\]、\[**開始新執行個體**\]。這會啟動服務主機。  
  
3.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**用戶端**\] 專案，然後選取內容功能表中的 \[**偵錯**\]、\[**開始新執行個體**\]。這會啟動用戶端。  
  
4.  在用戶端主控台視窗的提示中輸入任何字串，然後按一下 ENTER。這會將輸入字串傳送到服務，然後計算此字串的雜湊。  
  
5.  當服務回呼雙工回呼合約作業以顯示用戶端主控台視窗上的結果時，檢視用戶端視窗上的結果。在服務上會有一個刻意的延遲，以模擬處理資料的長期作業。  
  
6.  監視 HTTP 流量 \(透過 Network Monitor、Fiddler 等任何線上網路監視工具\) 顯示通訊的順序是在可靠的安全設定檔制定之用戶端和服務之間建立的，並示範用戶端如何利用「建立連線」要求輪詢服務。當服務準備好傳回處理過的回應時，它會使用最後一個「建立連線」要求的返回通道傳回結果。  
  
7.  在服務主控台視窗上按 ENTER 鍵，以關閉服務。在用戶端主控台視窗上按 ENTER 鍵，以關閉用戶端。