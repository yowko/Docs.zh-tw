---
title: HOW TO：啟用 Net.TCP 連接埠共用服務
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 20db0ef427a5e791bd6b8dcef90bf7911ae0d4a9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343476"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>HOW TO：啟用 Net.TCP 連接埠共用服務
Windows Communication Foundation (WCF) 會使用名為 Net.TCP Port Sharing Service 的 Windows 服務，以促進跨多個處理序的 TCP 連接埠共用。 此服務已安裝 WCF 的一部分，但服務為了安全起見預設不會啟用，因此必須手動啟用第一次使用之前。 本主題說明如何使用 Microsoft Management Console (MMC) 嵌入式管理單元，來設定 Net TCP Port Sharing Service。  
  
 啟用 Net.TCP Port Sharing Service 後，當您以手動方式啟動它時，請參閱[How to:設定 WCF 服務，以使用連接埠共用](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)如需如何將服務設定為使用這項服務的資訊。  
  
 如需使用 net.tcp:// 連接埠共用的範例，請參閱 < [Net.TCP Port Sharing 範例](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md)。  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>若要使用 MMC 來啟用 Net.TCP 連接埠共用服務  
  
1. 從 開始 功能表中，開啟 服務 管理主控台透過開啟命令提示字元視窗，然後輸入`services.msc`或以開啟 執行，並輸入`services.msc`成 開啟 方塊。  
  
2. 在 **名稱**的服務清單中的資料行上按一下滑鼠右鍵**Net.Tcp Port Sharing Service**，然後選取**屬性**從功能表。  
  
3. 若要啟用的手動啟動的服務，在**屬性**視窗中選取**一般**] 索引標籤，然後在**啟動類型**方塊選取 [手動]，然後再按一下 [ **套用**。  
  
4. 若要啟動服務，服務的 狀態 區域中，按一下**啟動** 按鈕。 服務狀態現在應該顯示為「已啟動」。  
  
5. 若要回到服務清單中，按一下**確定**，然後結束 MMC 主控台。  
  
## <a name="example"></a>範例  
  
## <a name="see-also"></a>另請參閱

- [Net.TCP Port Sharing](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [設定 Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
