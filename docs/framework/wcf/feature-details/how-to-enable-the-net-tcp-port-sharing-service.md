---
title: "HOW TO：啟用 Net.TCP 連接埠共用服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "連接埠共用 [WCF]"
  - "啟用服務 [WCF]"
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# HOW TO：啟用 Net.TCP 連接埠共用服務
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用名為 Net.TCP 連接埠共用服務的 Windows 服務來協助多個處理序共用 TCP 連接埠。 這項服務會安裝為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的一部份，但是為了安全起見預設不會啟用此服務，因此您必須在第一次使用時手動加以啟用。 本主題說明如何使用 Microsoft Management Console (MMC) 嵌入式管理單元，來設定 Net TCP Port Sharing Service。  
  
 在啟用 Net.TCP 連接埠共用服務並手動啟動之後，請參閱[How to︰ 設定 WCF 服務使用連接埠共用](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)如需有關如何設定您要使用這項服務的服務資訊。  
  
 如需使用 net.tcp:// 連接埠共用的範例，請參閱[Net.TCP Port Sharing 範例](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md)。  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>若要使用 MMC 來啟用 Net.TCP 連接埠共用服務  
  
1.  從 [開始] 功能表中，開啟 [服務] 管理主控台開啟命令提示字元視窗並輸入`services.msc`或開啟執行中，輸入`services.msc`成 [開啟] 方塊。  
  
2.  在**名稱**資料行清單的服務，以滑鼠右鍵按一下**Net.Tcp 連接埠共用服務**，然後選取**屬性**從功能表。  
  
3.  若要啟用服務，手動啟動在**屬性** 中選取**一般** 索引標籤，然後在**啟動類型**方塊選取 手動，然後再按一下**套用**。  
  
4.  若要啟動服務，服務狀態 區域中，按一下 **啟動** 按鈕。 服務狀態現在應該顯示為「已啟動」。  
  
5.  若要回到服務清單中，按一下 **確定**，然後結束 MMC 主控台。  
  
## <a name="example"></a>範例  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## <a name="see-also"></a>另請參閱  
 [Net.TCP 連接埠共用](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)   
 [設定 Net.TCP 連接埠共用服務](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)