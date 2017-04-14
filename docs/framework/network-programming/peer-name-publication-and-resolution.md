---
title: "對等名稱發佈和解析 | Microsoft Docs"
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
ms.assetid: f0370e08-9fa6-4ee5-ab78-9a58a20a7da2
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# 對等名稱發佈和解析
## 發行對等名稱  
 若要將新的 PNRP ID，對等執行下列動作:  
  
-   傳送 PNRP 發行資訊給已登錄最低層級的 PNRP ID 快取\) 的其快取 \(鄰近對等裁剪其快取。  
  
-   選取並不是其相鄰項目在 Cloud 中的選擇性節點並傳送它們 PNRP 其 ID P2P. 的名稱解析要求  產生的端點解析程序裁剪快取在 Cloud 中的選擇性結構與發行對等的 PNRP ID。  
  
 如果它們只剖析其他 P2P ID， PNRP 2 版節點不會發出 PNRP ID。  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\PeerNet\\PNRP\\IPV6\-Global\\SearchOnly\=1 登錄值 \(REG\_DWORD 型別\) 指定只使用 PNRP 的名稱解析，而非名稱發行。  這個登錄值可以群組原則也設定。  
  
## 解析對等名稱  
 找出其他對等網路或 PNRP Cloud 流程是由兩個階段所組成:  
  
1.  端點解析  
  
2.  PNRP ID 解析  
  
 在頂點解析階段，嘗試解析的對等服務的 PNRP ID 在另一部電腦上判斷該遠端對等電腦 IPv6 位址。  遠端對等電腦所執行的相同，或與，電腦的 PNRP ID 或服務。  
  
 在驗證之後遠端端點註冊至 PNRP Cloud， PNRP ID 解析階段需求的對等電腦傳送要求至所服務的 PNRP ID 之對等電腦的端點。  端點傳送確認服務、註解和 4 KB 的 PNRP ID 的復原其他資訊要求的對等電腦可以針對未來的通訊。  例如，如果預期，端點是移動對於伺服器，另一個對等名稱記錄資料可能包含有關遊戲中的資訊，播放的層級和播放程式的目前數目。  
  
 在頂點解析階段 PNRP，以找出發行 PNRP ID，執行解析的節點與的連線管理循序與目標 PNRP ID. 更接近節點使用迴圈處理序  
  
 若要執行名稱解析在 PNRP，對等解析它符合目標 PNRP ID. 的項目本身的快取檢查輸入  如果找到，則對等 PNRP 要求傳送資訊到對等電腦並等待回應。  如果找不到 PNRP ID 的輸入，對等電腦傳送要求至 PNRP 資訊對應至輸入具有 PNRP ID 最符合目標 PNRP ID. 的對等個體。  PNRP 收到要求訊息的節點檢查物件的快取執行下列動作:  
  
-   如果找到 PNRP ID，要求的端點對等復原直接寫入要求的對等電腦。  
  
-   如果找不到 PNRP ID，然後 PNRP ID 在快取是分隔目標 PNRP ID 更接近，要求的對等電腦傳送至包含用於 PNRP ID 代表輸入對等的 IPv6 位址的要求的對等的回應最符合目標 PNRP ID.  使用在回應的 IP 位址，則要求的節點傳送另一個 PNRP 要求資訊至 IPv6 位址回應或檢查物件的快取。  
  
-   如果找不到 PNRP ID，而且沒有 PNRP ID 為分隔目標 PNRP ID 更接近其快取，要求的對等電腦傳送要求的對等表示這種情況的回應。  要求的對等電腦然後選取下一個最接近的 PNRP ID.  
  
 要求的對等繼續進行後續反覆項目的這個處理序，最終會尋找註冊 PNRP. 的節點 ID。  
  
 在 <xref:System.Net.PeerToPeer> 命名空間中，具有包含端點和 PNRP Cloud 或網狀結構它們通訊的 <xref:System.Net.PeerToPeer.PeerName> 資料錄之間的多對多關聯性。  當有複製或過時項目或多個節點具有相同的對等名稱時，使用類別， <xref:System.Net.PeerToPeer.PeerNameResolver> PNRP 節點可以取得目前的資訊。  <xref:System.Net.PeerToPeer.PeerNameResolver> 方法使用單一對等名稱簡化檢視方塊對於一個對等的許多對等名稱記錄和相同的對等電腦加入至許多 Cloud。  這類似於關聯式資料表執行查詢聯結。  在成功完成時，解析程式物件傳回指定的對等名稱 <xref:System.Net.PeerToPeer.PeerNameRecordCollection> 。  例如，對等名稱在集合中的所有對等名稱記錄時，將會產生排序由 Cloud。  這些是支援資料可能是以 PNRP 的應用程式需要對等名稱的執行個體。  
  
## 請參閱  
 <xref:System.Net.PeerToPeer>