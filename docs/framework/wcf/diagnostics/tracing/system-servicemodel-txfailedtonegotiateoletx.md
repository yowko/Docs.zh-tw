---
title: "System.ServiceModel.TxFailedToNegotiateOleTx | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# System.ServiceModel.TxFailedToNegotiateOleTx
OleTransactions 通訊協定無法完成指定的協調內容。  
  
## 描述  
 在有 OleTx 資訊的傳入交易無法使用附加的 OleTx 資訊，而且將改用 WS\-AT 時追蹤。  
  
## 疑難排解  
 代表機器之間的 MSDTC RPC 通訊有潛在的問題。如果記錄中出現這些追蹤中的多數，可能導致效能大幅下降。如果不需要 OleTx，在 WS\-AT 登錄組態中將 `OleTxUpgradeEnabled` 設定為 0。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)