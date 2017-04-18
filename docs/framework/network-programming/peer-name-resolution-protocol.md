---
title: "對等名稱解析通訊協定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# 對等名稱解析通訊協定
在點對點環境，解析彼此的網路位置的對等電腦使用特定的名稱解析系統 \(位址、通訊協定和通訊埠\) 從名稱或識別項的其他型別。  在過去，對等名稱解析由原本暫時性連接以及其他缺點複雜度簡化在網域名稱系統 \(DNS\) \(DNS\) 內。  
  
 Microsoft® Windows®對等網路平台解析對等名稱解析通訊協定 \(PNRP\)， Windows Vista™先開發適用於 Windows XP 再升級的安全性，可升級和動態名稱註冊和名稱解析通訊協定的問題。  PNRP 工作非常與傳統名稱解析系統不同，開啟應用程式開發人員的進而協助隨時啟動新的可能性。  
  
 使用 PNRP，對等名稱可套用至電腦或個別應用程式或服務在電腦上。  對等名稱解析包含一個位址、通訊埠和可擴充的裝載。  系統的優點包括容錯、瓶頸並不會傳回過時地址名稱解析;進行通訊協定找出的行動使用者的絕佳方案。  
  
 根據安全性，對等名稱可以發行為安全保護 \(Protected\) 或不安全 \(未受保護\)。  PNRP 使用公開金鑰加密受保護的對等名稱以防止假冒;電腦和服務可以使用 PNRP 命名。  
  
-   對等名稱解析通訊協定示範下列屬性:  
  
-   發出和幾乎全部是無伺服器。  伺服器在這個自持程序才是必要的。  
  
-   保護發行物名稱，而不使用協力廠商的作業中時。  沒有財務成本，不同於 DNS 名稱發行， PNRP 發行物名稱是即時和。  
  
-   PNRP 更新在執行階段，防止過時位址的解析度。  
  
-   名稱解析傳遞 PNRP 電腦以外透過也允許服務的名稱解析。  
  
## System.Net.PeerToPeer 命名空間  
  
-   PNRP 功能是由 .NET Framework 3.5 版中的 <xref:System.Net.PeerToPeer> 命名空間中定義。  它提供可用來註冊及解決一個可用的 PNRP 服務的對等名稱的一組型別。  
  
-   \(PNRP 和自訂對等解析程式可以建立及初始化使用 <xref:System.ServiceModel.PeerResolvers> 在命名空間中提供的型別\)。  
  
-   使用的基本型別註冊及解決一個可用的 PNRP 服務名稱如下:  
  
-   <xref:System.Net.PeerToPeer.Cloud>:定義描述一個可用的 PNRP Cloud，包括其範圍的資訊。  
  
-   <xref:System.Net.PeerToPeer.PeerName>:定義可以用來註冊再解析在 Cloud 中對等的一個對等名稱。  
  
-   <xref:System.Net.PeerToPeer.PeerNameRecord>:定義在包含對等的登入資訊，包括網路端點對等電腦可以聯繫 PNRP Cloud 中的資料錄。  
  
-   <xref:System.Net.PeerToPeer.PeerNameRegistration>:定義一個對等名稱註冊程序，包括方法啟動和停止對等名稱登錄。  
  
-   <xref:System.Net.PeerToPeer.PeerNameResolver>:定義用來解析的對等名稱處理序對其網路端點，包括解析度的同步和非同步方法。  
  
## 請參閱  
 <xref:System.ServiceModel.PeerResolvers>   
 <xref:System.Net.PeerToPeer>   
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)   
 [PeerToPeer 技術範例](http://go.microsoft.com/fwlink/?LinkID=179571)